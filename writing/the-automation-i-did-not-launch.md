# The automation I didn't launch

*A working email pipeline, a kill switch that stayed off, and why the version that eventually launched was better for it.*

In December 2025 I built an outreach automation for a home-inspection company. The idea was simple and the business case was real: when a home goes under contract, the listing agent often influences which inspector gets called. The company already received MLS "new pending" notifications by email. Parse the notification, look up the listing agent, send them a coupon for a well-and-septic evaluation at exactly the moment they're thinking about inspections.

The twenty-line version of this is a weekend. The version I built took a few days, works end to end, has one recorded send (a test), and has been switched off ever since. This is about why both of those things are true.

## Build the brakes first

Before the pipeline could email anyone, it had to pass four checks, in order, each one logged with a reason when it blocks:

1. **A kill switch** that has to literally equal `true`. Absent, empty, or anything else means nothing sends. Off is the default state.
2. **A suppression list**, with endpoints to add and remove addresses. Anyone on it is never emailed again.
3. **A daily cap** across all recipients. Twenty-five, by default.
4. **A per-agent cooldown.** Anyone emailed in the last twenty-one days is skipped.

Every stage of the pipeline returns a reason when it stops: couldn't parse, out of service area, agent not found, send disabled, suppressed, cap reached, cooldown active, send failed. In demo mode, every send redirects to an internal address, so the whole thing can run against real notifications with no agent receiving anything.

The order matters. Adding a suppression list after the first angry reply means the first angry reply already happened.

## Then don't launch

Two things stopped it, and I'd stop it again.

**The trigger wasn't the company's to give yet.** The final integration needed the service to read a mailbox. Which mailbox, whose credentials, and what else that exposed were decisions for the owner, not for me. That decision was never made, and I wasn't going to make it by default.

**The compliance posture was incomplete.** The guardrails handle volume, frequency, and opt-out. They don't handle consent, sender identification, or the disclosure language commercial email requires. Emailing a directory of agents who never opted in is the kind of thing that works until it very much doesn't, and the company's referral relationships are worth more than a coupon campaign.

So the pipeline stopped one integration short. The live configuration omits the kill-switch flag entirely, which means the policy blocks everything by construction. It is fail-closed by accident as much as by design, and one of the improvements on the list is to make the caps fail closed too when they're unset.

## What happened next

The v1 pipeline never sent a real email. A later version did. Rebuilt on self-hosted n8n with the mailbox question settled and the guardrails carried over (service-area rules, do-not-contact and cooldown controls, lead routing, persistent state with duplicate protection and failure logging), it has run in production since January 2026: 4,019 emails through early August, 95% delivered, zero spam complaints, 2% hard bounces. The point stands: the version that launched is the one that had its brakes built first.

## What this is worth

The skill in automation isn't making the thing send. It's knowing what has to be true before it's allowed to, building those conditions as code rather than as intentions, and being willing to leave the switch off until they're met. The v1 that never sent is the reason the production version could send four thousand times without a cleanup story afterward.

*Ryan Faber builds AI applications and business software for operations. Case studies at [github.com/Redthreepro](https://github.com/Redthreepro).*
