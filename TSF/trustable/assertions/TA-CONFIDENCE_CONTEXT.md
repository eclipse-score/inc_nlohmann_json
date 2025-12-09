---
level: 1.1
normative: false
---

(Note: The guidance, evidence, confidence scoring and checklist sections below are copied from [CodeThink's documentation of TSF](https://codethinklabs.gitlab.io/trustable/trustable/trustable/TA.html). However, the answers to each point in the evidence list and checklist are specific to this project.)

**Guidance**

To quantify confidence, either a subjective assessment or a statistical argument must be presented for each statement and then systematically and repeatably aggregated to assess whether the final deliverable is fit for purpose.

To improve the accuracy of confidence evaluations in reflecting reality, the following steps are necessary:

- Break down high-level claims into smaller, recursive requests.
- Provide automated evaluations whenever possible, and rely on subjective assessments from appropriate parties when automation is not feasible.
- Aggregate confidence scores from evidence nodes.
- Continuously adjust prior confidence measures with new evidence, building on established values.

Any confidence scores, whether tracked manually or statistically, must be based on documented review guidelines that are themselves reviewed and applied by appropriate parties.
These guidelines should focus on detecting inconsistencies in the reasoning and evidence linked to related Expectations, and on assessing the relevancy of all aspects considered.
As a result, the argument structure must reflect the project scope, which in turn should be captured in the set Expectations and linked to the project’s analysis, design considerations, and partitioning.
Within this structure, Statements must be ordered or weighted so that their relative importance and supporting reasoning are clear, with iteration scores capturing strengths and weaknesses and guiding decisions.

As subjective assessments are replaced with statistical arguments and confidence scores are refined with new evidence, evaluation accuracy improves.
Over time, these scores reveal the project's capability to deliver on its objectives.
The process itself should be analysed to determine score maturity, with meta-analysis used to assess long-term trends in sourcing, accumulation, and weighting.

**Evidence**

- Confidence scores from other TA items
  - **Answer**: Provided in JLS-08, JLS-09 and JLS-37

**Confidence scoring**

Confidence scoring for TA-CONFIDENCE is based on quality of the confidence
scores given to Statements

**Checklist**

- What is the algorithm for combining/comparing the scores?
  - **Answer**: The algorithm behind the scoring in given in JLS-09
- How confident are we that this algorithm is fit for purpose?
  - **Answer**: We are confident that the scoring algorithm is fit for purpose and is aligned with the TSF methodology described (see also JLS-09). However, at the moment, the statements require a larger number of SME reviewers to profit from the law-of-large-numbers and arrive at statistically significant scores.
- What are the trends for each score?
  - **Answer**: At the moment, there are no trends as all statements have the review-status 'unreviewed'. However, the infrastructure for saving history of scores is already in place (see JLS-20).
- How well do our scores correlate with external feedback signals?
  - **Answer**: Such correlation can not be measured yet due to missing data.
