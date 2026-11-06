# Market Evidence and Validation

## What the evidence says

| Evidence | Source | What it supports | What it does not prove |
|---|---|---|---|
| Dubai recorded 19.59 million international overnight visitors in 2025. | [DET Annual Visitor Report 2025](https://www.dubaidet.gov.ae/en/research-and-insights/annual-visitor-report-2025) | There is a large visitor population the product could serve. | That visitors struggle to plan, would use this assistant, or would pay for it. |
| Dubai recorded 18.72 million international overnight visitors in 2024, up 9% year over year; DXB handled 92.3 million passengers that year. | [DET Annual Visitor Report 2024](https://www.dubaidet.gov.ae/en/research-and-insights/annual-visitor-report-2024) | Visitor and arrival flows are substantial; trip-planning assistance has a plausible audience. | Airport passengers are not all tourists, and scale is not a customer-satisfaction measure. |
| RTA reports high annual use of public transport, shared mobility, and taxis; its official site publishes rider and service updates. | [RTA](https://www.rta.ae/) | Transport coordination is a plausible itinerary feature and a possible source of current information. | That routing is a top visitor complaint or that an AI assistant can improve transport capacity. Verify the exact figure and source before reusing a statistic externally. |

## Research conclusion

The public evidence supports market scale, not a ranked list of visitor pain points. The product hypothesis is that visitors benefit from a personalized, source-linked plan that combines verified attractions, travel transitions, time constraints, and stated needs. Treat this as unvalidated until interviews and task tests support it.

Existing official digital channels are a competitive constraint. The demo must be differentiated by a specific task and transparent sourcing, not by claiming to be the official Dubai chatbot or replacing RTA/DET services.

## Discovery before broad build

Conduct exploratory interviews with at least five visitors and two hospitality workers. This small sample is for learning, not statistical representation.

Ask about a recent Dubai visit, not hypothetical enthusiasm:

1. Tell me about the last time you planned a day in Dubai. What did you do first?
2. What information did you need to check in more than one place?
3. What changed after you made your plan?
4. Which details did you verify yourself, and how?
5. What was difficult about moving between places or checking access needs?
6. What tools or official services did you already use?
7. May I observe you planning a real or sample day with your usual tools?

Do not lead with the proposed agent. Capture the user's words, observed workarounds, frequency, consequence, and existing alternatives. Record consent and avoid unnecessary personal data.

## Pilot design

- Test 5-10 people with representative sample itineraries and a small source corpus.
- Compare their normal planning approach with the agent on the same task.
- Record task completion, elapsed time, source-checking behavior, unsupported claims, satisfaction, and what they would do next.
- Have a human reviewer verify every factual claim in the test set.
- Interview one venue or hotel only after visitor tests reveal a recurring problem that staff can influence.

## Go / revise / stop signals

- **Go:** people complete the task faster or with less effort, trust the cited information, and can identify when the agent is uncertain.
- **Revise:** users like the idea but repeatedly need missing live data, or do not trust sources and freshness.
- **Stop or narrow:** normal maps/search already solve the task well, users do not return, or reliable accessibility/opening/transport data cannot be maintained.

These are decision rules for this pilot, not external benchmarks. Set numerical thresholds after baseline tests.
