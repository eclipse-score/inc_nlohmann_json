---
level: 1.1
normative: false
---

(Note: The guidance, evidence, confidence scoring and checklist sections below are copied from [CodeThink's documentation of TSF](https://codethinklabs.gitlab.io/trustable/trustable/trustable/TA.html). However, the answers to each point in the evidence list and checklist are specific to this project.)

**Guidance**

This assertion is satisfied to the extent that test data, and data collected
from monitoring of deployed versions of nlohmann/json, has been analysed, and the results
used to inform the refinement of Expectations and risk analysis.

The extent of the analysis is with sufficient precision to confirm that:

- all Expectations (TA-BEHAVIOURS) are met
- all Misbehaviours (TA-MISBEHAVIOURS) are detected or mitigated
- all advance warning indicators (TA-INDICATORS) are monitored
- failure rates (calculated directly or inferred by statistics) are
  within acceptable tolerance

When tests reveal Misbehaviours missing from our analysis (TA-ANALYSIS), we update our Expectations (TA-BEHAVIOURS, TA-MISBEHAVIOURS).
Guided by confidence evaluations (TA-CONFIDENCE), we refine and repeat the analysis as needed.
Analysis results also inform confidence evaluations, allowing automatic generation through statistical modelling and defining Key Performance Indicators (KPIs) for consistent use across the TSF.

For increased confidence in the analysis specification and results, they should be evaluated in terms of their reliability, relevance, and understandability.

- Reliability: The analysis methods must be verified against both known good and bad data to ensure sufficient detection of false negatives and false positives.
  Accuracy degradation across methods should be tracked and aggregated, making outcomes more easily verifiable and providing visibility into how changes to the system under test or to the analysis mechanisms affect the results.
- Relevance: The results must account for hardware and hardware/software interactions.
  Calibration should address capacity, scalability, response time, latency, and throughput where applicable.
  To further increase confidence in estimated failure rates, the analysis should also cover testing sufficiency (with statistical methods where appropriate), cascading failures including sequencing and concurrency, bug analysis, and comparison against expected results and variability. 
  The analysis should be automated and exercised repeatedly for timely feedback.
- Understandability: Both methods and results should be mapped to other analyses performed on the system (linked to TT_EXPECTATIONS) to ensure alignment with scope, abstraction levels, and partitioning, thereby guiding prioritisation.
  Effectiveness also depends on user-friendliness and presentation (involving semi-formal structured forms, supported by diagrams and figures with clear legends).

To gain increased confidence, test results should be shown to be reproducible. 
Even with non-deterministic software, representative test setups must be ensured to produced reproducible results
within a defined threshold as specified by TT-EXPECTATIONS.
Reproducible test results also supports verification of toolchain updates (together with other measures in TA-FIXES),
by confirming that test results remain unchanged when no changes are intended.

**Evidence**

- Analysis of test data, including thresholds in relation to appropriate statistical properties.
  - **Answer**: The analysis of test data is captured by JLS-17, but no explicit quantitative thresholds are defined.
- Analysis of failures
  - **Answer**: Provided by JLS-26 and JLS-17.
- Analysis of spikes and trends
  - **Answer**: CI test failure rates for the upstream `nlohmann/json` repository and `eclipse-score/inc_nlohmann_json` are analysed using the time-series based GitHub Actions metrics views. This analysis is performed manually (see JLS-17). There is currently no fully automated, continuous analysis of failures.
- Validation of analysis methods used
  - **Answer**: There is no separate formal validation of the analysis methods.

**Confidence scoring**

Confidence scoring for TA-ANALYSIS is based on KPIs
that may indicate problems in development, test, or production.

**CHECKLIST**

- What fraction of Expectations are covered by the test data?
  - **Answer**: The two expectations are JLEX-01 and JLEX-02. Every statement supporting either of these expectations is ultimately supported by a test, except for WFJ-06. WFJ-06 specifies that `basic_json::accept` must accept exactly JSON values for all possible inputs. Since there are infinitely many possible inputs, this cannot be tested exhaustively. Indirect tests are provided by the rejection of ill-formed json data.
- What fraction of Misbehaviours are covered by the monitored indicator data?
  - **Answer**: Currently none, because there is no implemented monitoring of deployed instances yet. This is a future integrator responsibility (see AOU-09, AOU-18 and AOU-19).
- How confident are we that the indicator data are accurate and timely?
  - **Answer**: No indicator data is collected (see the previous question).
- How reliable is the monitoring process?
  - **Answer**: See the previous question.
- How well does the production data correlate with our test data?
  - **Answer**: There are no production data.
- Are we publishing our data analysis?
  - **Answer**: Analyses of CI tests failure rates are published in the TSF documentation on GitHub (via ci_failure_rate_analysis.md), but there is currently no published analysis of production monitoring data.
- Are we comparing and analysing production data vs test?
  - **Answer**: There is no production data.
- Are our results getting better, or worse?
  - **Answer**: There are no explicit quantitative trends that indicate whether results are improving or degrading over time.
- Are we addressing spikes/regressions?
  - **Answer**: There is currently no monitored indicator data, so spikes in indicator trends are not tracked. However, any failing tests in CI are investigated and fixed, and fuzz-testing results in the original nlohmann/json repository are analysed and addressed.
- Do we have sensible/appropriate target failure rates?
  - **Answer**: No explicit numeric failure-rate targets are defined. The implicit target is that the CI test suite passes and known misbehaviours remain within an acceptable, manually monitored range.
- Do we need to check the targets?
  - **Answer**: For unit and integration tests, there are no explicit failure rate targets. The implicit target is that the CI test suite passes on all supported environments, which is continuously checked by the CI workflows (see JLS-26). Since the fuzz testing runs and is investigated in the original nlohmann/json repository, there is no need to check the target.
- Are we achieving the targets?
  - **Answer**: For the unit and integration tests, yes. The degree of target achievement for the fuzz-testing is evaluated within the original nlohmann/json repository.
- Are all underlying assumptions and target conditions for the analysis specified?
  - **Answer**: For all tests, the underlying assumption and target condition is that they should cover all expectations, and that no test is expected to fail. Any failed tests are analyzed and reasonably justified or fixed.
- Have the underlying assumptions been verified using known good data?
  - **Answer**:  The input data from [nlohmann/json_test_data](https://github.com/nlohmann/json_test_data/tree/master) which is used for the tests contain both known good data and known bad data. As each expectation is mapped to a sub-set of tests, it is indeed verified that the underlying assumption is reasonably verified.
- Has the Misbehaviour identification process been verified using known bad data?
  - **Answer**: Yes. The misbehaviour identification process has been exercised using known bad data from [nlohmann/json_test_data](https://github.com/nlohmann/json_test_data/tree/master)
- Are results shown to be reproducible?
  - **Answer**: A dedicated ci_reproducible_tests target exists to run a reproducible subset of tests, but not all tests are fully reproducible (see JLS-62).

