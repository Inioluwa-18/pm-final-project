# Competitive Analysis & Journey Map (Module 2)

## Responses
- **Role, who are you solving for? (the specific user segment or profile):** A dispatcher who coordinates real-time routing and status for a fleet of drivers from a central console.
- **Goal, what is this user ultimately trying to achieve?:** Maintain an accurate, trustworthy live view of where every driver and stop stands so they can make fast reassignment decisions.
- **Friction, the main barrier (moment of misery) stopping them from succeeding:** When they reassign a route, it takes 8–15 minutes to reach the driver's app with no push notification (BUG-2044), so drivers keep working a stale route — "I reassign a route, and the driver doesn't see it for ten, fifteen minutes. By then they've driven the wrong way" (UXR-02). Compounding this, the dashboard itself lags 20–60 minutes behind reality (BUG-2072), showing stops as "in progress" long after delivery — "I can't trust the board" (UXR-09). The administrative burden here isn't a form or a report; it's the second, informal system (a WhatsApp group) they've built just to know what's actually happening.
- **External tools, the outside platforms or tools the user is forced to use:** Whataspp
- **The process, the 3 to 5 manual steps the user takes to get the job done:** Step 1 — Reassign in the platform, then immediately distrust it.
The dispatcher makes the route change in the system, but because reassignments take 8–15 minutes to propagate with no push notification (BUG-2044), they can't assume the driver has seen it. The tool's output is no longer actionable on its own.

Step 2 — Post the reassignment manually in the WhatsApp group.
To close the notification gap, the dispatcher re-communicates the same information through a channel they know is instant — the informal group referenced in UXR-02. This is a duplicate data-entry step: the same instruction now has to be typed twice, in two systems, by a human.

Step 3 — Watch the dashboard, but verify status by asking, not reading.
Because the dashboard lags 20–60 minutes and shows stale states like "in progress" on completed stops (BUG-2072, UXR-09), the dispatcher can't rely on the console for real-time decisions. Per UXR-09, they've effectively stopped trusting "the board" as an instrument.

Step 4 — Use WhatsApp (and likely direct outreach) to confirm actual status before acting.
To make a fast reassignment decision — their core goal — the dispatcher has to solicit a live human confirmation from the driver rather than reading it off the system that exists to provide that. This mirrors the pattern in UXR-03, where the platform's failure to preserve real-time information forced a manual, person-to-person fallback.
- **Core frustration, the exact moment the process feels most “broken”:** It doubles the dispatcher's workload for a single decision. Every reassignment now requires a system action and a manual message, plus a status check-in — three actions to do the job the console is supposed to do in one.
It introduces a second, unstructured system of record. WhatsApp has no audit trail, no structured stop data, and no integration with the routing engine. Decisions made there are invisible to reporting, invisible to the next shift, and invisible to the account team assessing platform health.
It scales linearly with fleet size and breaks under load. A WhatsApp thread works for a handful of live reassignments; it does not work as the fleet or the number of daily changes grows — which is precisely when a dispatcher needs the platform most.
It shifts cognitive load from software to human vigilance. The dispatcher is now the system's consistency check, manually reconciling what the console shows against what they believe is true — the opposite of the "accurate, trustworthy live view" their goal describes.
- **The evidence, a specific quote or behavior from the research that proves this:** This workaround is that burden in its purest form: the dispatcher isn't fighting complexity in the abstract; they're doing double-entry, double-verification work every single shift just to compensate for two specific defects (BUG-2044, BUG-2072). This is the same dynamic UXR-10 names directly at the account level — "the daily driver experience is dragging down adoption and now renewal is at risk." The dispatcher's WhatsApp workaround is not a workaround at all from the customer's perspective; it's evidence, visible to the ops manager who owns the renewal, that the platform they're paying for isn't the one actually running operations day-to-day.
- **Your journey map, a shareable link, or the map file you committed (e.g. journey-map.html):** https://github.com/Inioluwa-18/Dispatcher-Journey-Map-PM-Fooundations-project-/commit/78eafb42e78f926f24a9a817491a5f649b01521f
