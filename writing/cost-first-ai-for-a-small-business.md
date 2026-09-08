# Cost-first AI for a small business

*How a fifteen-person inspection company got a production AI platform without a surprise bill.*

Every conversation about AI in a small business ends at the same place: "what's it going to cost us?" Not to build. To run. A tool the crew uses every day is a tool that calls a model every day, and a model that charges per token has no natural ceiling.

I built and operate an AI platform for a home-inspection company with thirteen field inspectors. The constraint the owner set before anything else was that it had to be fully usable by the whole crew, scale to twenty-five, and cost as little as possible to run. Not "reasonable." As little as possible. That constraint shaped every architecture decision, and I think it produced a better system than a bigger budget would have.

## Decide the ceiling before the first user

The cost controls went in before the first inspector signed in, not after the first surprising invoice. Three layers:

1. **Per-user daily cap.** Every AI call checks a counter. An inspector who somehow fires four hundred requests in a day stops getting answers until tomorrow. Nobody has hit it; that's the point.
2. **Monthly spend ceiling** on the provider account. If everything else fails, the provider stops us.
3. **Instance limits** on every cloud function. A runaway loop can't scale itself into a bill.

None of this is clever. All of it is boring to add after the fact and trivial to add before.

## Use the cheap model unless you can prove you need the expensive one

The default chat model is the small one. It answers procedure questions in the company's report voice well enough that nobody asked for better. The stronger vision model is used for exactly one task: reading tiny embossed serial numbers on equipment data plates, where a wrong character means a wrong manufacture date on a client's report. That call costs about half a cent. We know the number because we measured it before choosing.

The rule that came out of this: every use of the expensive model needs a sentence explaining why the cheap one isn't good enough. Most features never earn that sentence.

## Don't stand up a second system

The assistant retrieves from the company's own procedures. The obvious design is a vector database. We already had Firestore, and Firestore had just shipped native vector indexes. So the knowledge base lives as vector fields next to the data it belongs to, queried with the same permissions, with no second service to pay for, secure, or keep running. At a few hundred chunks that's the right call. At a few hundred thousand it might not be. The revisit trigger is written down.

The same instinct ran everywhere. Client-side PDF generation for small documents instead of a render service. Free map tiles for display and the paid mapping API only for the single call where accuracy mattered, road drive-times. A dispatch tool hosted as a Google Apps Script web app because the company already paid for Workspace. Local text-to-speech and local voice cloning for video production so a promo video costs electricity, not credits.

## Move risk out of the model where you can

The most expensive kind of AI output is the wrong kind. For equipment age, the model reads the plate, but the manufacture date decodes in deterministic, tested code: twenty-five manufacturer serial schemes, cited samples, a test suite. The model does the part only a model can do, and a table does the rest. That's cheaper, faster, and countable. A hallucinated date is an accuracy problem you can't see. A missing manufacturer scheme is a coverage gap you can list.

## What it bought

An entire field crew on one tool, daily, for over a year, with a bill the owner doesn't think about. Cost-first isn't a constraint you tolerate. For a small business it's the design principle, and it forces the discipline that makes the system trustworthy anyway.

*Ryan Faber builds AI applications and business software for operations. Case studies at [github.com/Redthreepro](https://github.com/Redthreepro).*
