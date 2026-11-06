# Dubai Visitor Companion

## Product goal

Build and pilot a source-grounded assistant that helps a first-time Dubai visitor make a practical one-day plan around their time, starting area, budget, interests, preferred pace, and stated mobility needs. It should explain why each suggestion fits, show the sources used, and offer alternatives when a place or route cannot be verified.

The first release is a demonstration product, not an official Dubai service. Its job is to make planning easier, not to replace official visitor, transport, emergency, medical, or accessibility information.

## Problem hypothesis

Visitors may need to combine attraction information, travel options, opening hours, weather considerations, and personal constraints across multiple sources. A conversational planner may reduce that planning effort. This is a hypothesis to test with visitors and hospitality staff; visitor-volume statistics establish potential reach, not proof of this specific pain or willingness to use an agent.

## Initial user and scope

- Primary user: an independent first-time visitor already in Dubai, planning one day.
- Initial interaction: English-language web demo; the architecture should allow another language later.
- Initial area: a small, clearly stated set of attractions and transit facts selected for the demo. Do not imply citywide coverage.
- Main task: produce a time-bounded itinerary with reasons, source links, estimated travel legs where verified, and one or more alternatives.
- Accessibility: ask what the visitor needs, but label each venue or route as verified, unknown, or needs confirmation. Never infer accessibility from vague descriptions.

## What the agent must do

1. Ask only the details needed to plan: date or time window, starting area, budget range, interests, pace, language, and optional mobility needs.
2. Use a maintained, source-attributed knowledge set. Show the source and its last-checked date for material facts.
3. Distinguish confirmed facts, estimates, and unknowns. If current opening, transport, weather, or access information is unavailable, say so and link to the authoritative source.
4. Return a practical plan, not an unranked list: sequence, approximate time blocks, travel transitions, reasons for fit, alternatives, and what needs confirmation.
5. Keep the visitor in control of bookings, purchases, account creation, and messages.

## Non-goals and boundaries

- No claiming affiliation with Dubai DET, RTA, Dubai Municipality, a hotel, or another authority.
- No booking, payment, external form submission, or contacting a venue in the MVP.
- No guarantees about live traffic, availability, safety, opening hours, or accessibility.
- No legal, immigration, medical, emergency, or financial advice.
- No collection of passport numbers, payment details, precise live location, or other unnecessary sensitive data.
- No unauthorized scraping or bypassing access controls. Prefer official public sources and permitted APIs.

## Success measures

These are proposed pilot measures, not published Dubai benchmarks. Record a baseline before setting final thresholds.

- Task completion: can a visitor produce a plan they say they would use?
- Time-to-plan: compare the demo with the visitor's usual search process.
- Factual quality: percentage of testable claims supported by the linked source.
- Freshness: percentage of volatile facts with a visible check date and current source.
- Accessibility integrity: zero unsupported claims presented as verified.
- Satisfaction: a short post-task rating and an open-text reason.
- Safety: no unapproved external action and a clear handoff when confidence or source coverage is insufficient.

For a later venue pilot, estimate ROI as staff time saved plus attributable incremental gross profit, minus implementation and operating costs. Do not claim ROI from a public demo without venue data.

## Evidence available at project start

Dubai DET reported 19.59 million international overnight visitors in 2025. This demonstrates the scale of the visitor economy, but it does not demonstrate that visitors have the hypothesized planning problem. See [market-evidence.md](research/market-evidence.md) for sources, caveats, and the validation plan.
