---
level: 1.1
normative: false
---

(Note: The guidance, evidence, confidence scoring and checklist sections below are copied from [CodeThink's documentation of TSF](https://codethinklabs.gitlab.io/trustable/trustable/trustable/TA.html). However, the answers to each point in the evidence list and checklist are specific to this project.)

**Guidance**

This assertion is satisfied if results from all tests and monitored deployments are captured accurately, ensuring:

- Sufficient precision for meaningful analysis
- Enough contextual information to reproduce the setup (e.g., runner ID, software version SHA), though not necessarily the exact results

Monitored deployments run in both production and development, validating monitoring mechanisms across environments and ensuring comparable results.
Collecting and retaining all data that support project claims (together with traceability to reasoning and specifications, and including both established and experimental indicators as well as test data from all environments) preserves evidence for selecting appropriate measures and enables historical analysis.

To avoid misinterpretation, all data storage mechanisms and locations are documented, together with long-term storage strategies, so analyses can be reliably reproduced.
How this data is made accessible is assessed as part of TA-ITERATIONS.

Storage strategies should account for foreseeable malicious activities and privacy considerations when handling sensitive data, including how the data is managed during transit and at rest, and whether it can be accessed in plaintext or only through appropriate tools (also considered for TA-INPUTS and TA-TESTS).

Appropriate storage strategies safeguard availability across the product lifecycle, with emphasis on release-related data, and account for decommissioning, infrastructure teardown, and post-project backups.

**Evidence**

- Time-stamped and traceable result records for each test execution, linked to associated system under test version and specification references.
  - **Answer**: Provided by JLS-18 and JLS-45.
- List of monitored indicators, linked to associated specification version references.
  - **Answer**: Runtime monitoring indicators for deployed instances are not yet implemented and are expected to be defined by the integrator (see AOU-09, AOU-18 and AOU-19).
- Time-stamped and traceable test-derived data for each indicator, linked to associated system under test version and indicator specifications references.
  - **Answer**: Indicator-level data is not yet collected and should be done by the integrator (see AOU-09).
- List of monitored deployments, linked to associated version and configuration references.
  - **Answer**: Not available. Monitoring of deployed instances should be specified by the integrator (see AOU-09, AOU-18 and AOU-19).
- Time-stamped and traceable production data for each indicator, linked to associated deployment metadata and specification references.
  - **Answer**: Not available. Should be done by the integrator (see AOU-09, AOU-18 and AOU-19).

**Confidence scoring**

Confidence scoring for TA-DATA quantifies the completeness of test results
(including pass/fail and performance) and the availability of data from all
monitored deployments.

**Checklist**

- Is all test data stored with long-term accessibility?
  - **Answer**: No. Test results are collected into a persistent database as part of the CI workflows, which is done as a proof of concept. Due to GitHub storage constraints, the storage of this database is currently limited.
- Is all monitoring data stored with long-term accessibility?
  - **Answer**: No. Dedicated monitoring data from deployed software is not collected yet. But it is expected to be implemented by the integrator (see AOU-09, AOU-18 and AOU-19).
- Are extensible data models implemented?
  - **Answer**: Test-result data is stored in a SQLite database with separate tables for workflow runs and individual test results (see JLS-18). This schema can be extended with additional fields or tables if needed.
- Is sensitive data handled correctly (broadcasted, stored, discarded, or anonymised) with appropriate encryption and redundancy?
  - **Answer**: This is not explicitly applicable. The captured test data does not include personal or sensitive data.
- Are proper backup mechanisms in place?
  - **Answer**: No explicit project-level backup mechanism is defined for the test results database beyond GitHub’s own infrastructure.
- Are storage and backup limits tested?
  - **Answer**: The `capture_test_data_memory_sensitive.py` script enforces size limits for the persistent database and fails the workflow if they are exceeded. There is no backup mechanism.
- Are all data changes traceable?
  - **Answer**:  Yes, for test data. Updates to `TSF/MemoryEfficientTestResultData.db` are performed by CI workflows and committed to the `save_historical_data` branch, so Git history records each change.
- Are concurrent changes correctly managed and resolved?
  - **Answer**: Largely yes for test data. The ubuntu workflow uses a concurrency group that cancels in-progress runs for the same reference, so typically only one job updates the persistent database at a time and remaining conflicts would surface as failed pushes and require manual resolution.
- Is data accessible only to intended parties?
  - **Answer**: Since the library is open source, there are no unintended parties.
- Are any subsets of our data being published?
  - **Answer**: Yes, as a proof of concept, CI test result data is committed to the `save_historical_data` branch in the SQLite database `TSF/MemoryEfficientTestResultData.db`, which is publicly accessible via this GitHub repository.
