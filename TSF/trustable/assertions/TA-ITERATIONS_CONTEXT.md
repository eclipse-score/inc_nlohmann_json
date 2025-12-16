---
level: 1.1
normative: false
---

(Note: The guidance, evidence, confidence scoring and checklist sections below are copied from [CodeThink's documentation of TSF](https://codethinklabs.gitlab.io/trustable/trustable/trustable/TA.html). However, the answers to each point in the evidence list and checklist are specific to this project.)

**Guidance**

This assertion is best satisfied by checking generated documentation to confirm that:

- every iteration is a working product with evidence-backed, falsifiable Statements, together with documentation of confidence in those Statements and all required Trustable Statements.
- every iteration includes instructions for building and using the product
- all components, dependencies, tools, and data are identified in a manifest
- the manifest provides links to source code
- where source code is unavailable, the supplier is identified

An iteration consists of each batch of changes accepted into the canonical version of the product.
How the canonical version is managed must be documented (for TT-CHANGES) alongside the product's Expectations.

Every iteration must be usable as a standalone product, with verification and validation completed so that a hotfix could be released at any point.
Documentation generated alongside the product must include build and usage guidance together with the project's documented Expectations and supporting Statements, enabling any maintainer or user to reverify the state of the product and associated Statements.

For each iteration, any changes must be accompanied by attestations and reasoning, explaining the tests performed and the review steps taken, together with their outcomes (e.g., results of source code inspections).
Any attestations and impact assessments must be traceable to the specific changes, authors, reviewers, and the review process documentation used.

Collating and making available all appropriate data and documentation for every iteration must be automatable, so that the product's build can be reproduced and its analysis repeated end-to-end independently (best achieved using generated documentation and configuration as code).
All relevant data, including approval statuses and dates, must be stored long-term and analysed as part of TA-DATA.
For complex systems, the resulting information must be presented in a user-friendly, searchable, and accessible form.

Given such transparent documentation and attestations for every iteration, it becomes possible to analyse product and development trends over time.
For releases, additional documentation should summarise all changes across the iterations since the previous release.

**Evidence**

- list of components with source
  - source code
    - **Answer**: Provided by JLS-10.
  - build instructions
    - **Answer**: Provided by JLS-10 and JLS-19.
  - test code
    - **Answer**: Provided by JLS-10.
  - test results summary
    - **Answer**: Provided by JLS-10.
  - attestations
    - **Answer**: Provided by JLS-52.

- list of components where source code is not available
  - risk analysis
    - **Answer**: There are no components without source code within this project.
  - attestations
    - **Answer**: There are no components without source code within this project.

**Confidence scoring**

Confidence scoring for TA-ITERATIONS based on

- number and importance of source components
- number and importance of non-source components
- assessment of attestations

**Checklist**

- How much of the software is provided as binary only, expressed as a
  fraction of the BoM list?
  - **Answer**: 0% is provided as binary only. The entire library consists of source code in the form of a single C++ header file.
- How much is binary, expressed as a fraction of the total storage footprint?
  - **Answer**: 0% is provided as binary. The entire library consists of source code in the form of a single C++ header file.
- For binaries, what claims are being made and how confident are we in the
  people/organisations making the claims?
  - **Answer**: 0% is provided as binary. The entire library consists of source code in the form of a single C++ header file.
- For third-party source code, what claims are we making, and how confident
  are we about these claims?
  - **Answer**: The nlohmann/json library has no external dependencies/accesses to third party source code, as stated in JLS-34.
- For software developed by us, what claims are we making, and how confident
  are we about these claims?
  - **Answer**: There is no software developed by us, as we just use the original nlohmann/json library within eclipse_score/inc_nlohmann_json. For the code developed in nlohmann/json, all claims and confidence are provided in the statements. See e.g., all the no-json-faults (NJF) items.

