---
level: 1.1
normative: false
---

(Note: The guidance, evidence, confidence scoring and checklist sections below are copied from [CodeThink's documentation of TSF](https://codethinklabs.gitlab.io/trustable/trustable/trustable/TA.html). However, the answers to each point in the evidence list and checklist are specific to this project.)

**Guidance**

This assertion is satisfied if each iteration of nlohmann/json is *repeatable*, with all
required inputs controlled, and *reproducible* (covering both nlohmann/json and the
construction toolchain/environment, as described in TA-TESTS).

This assertion can be most effectively satisfied in a Continuous Integration
environment with mirrored projects (see TA-SUPPLY_CHAIN) and build servers
without internet access. The aim is to show that all build tools, nlohmann/json
components, and dependencies are built from controlled inputs, that rebuilding
produces the same binary fileset, and that builds can be repeated on any
suitably configured server, with server differences shown not to affect
reproducibility.

For releases in particular, builds from source must be shown to produce
identical outputs both with and without cache access. 

Again this will not be achievable for components/tools provided in binary form,
or accessed via an external service - we must consider our confidence in
attestations made by/for the supply chain.

All non-reproducible elements, such as timestamps or embedded random values from
build metadata, are clearly identified and considered when evaluating
reproducibility.

As a result, we gain increased confidence that the toolchain behaves correctly
during version upgrades: unintended changes to the project are avoided, intended
fixes produce the expected effects, and the constructed output of nlohmann/json shows the
correct behavioural changes, verified and validated with test results according
to TT-RESULTS analysis.

**Evidence**

- list of reproducible SHAs
  - **Answer**: JLS-14 ensures that the SHA value of the nlohmann/json library used within eclipse-score/inc_nlohmann_json coincides with the SHA value provided by Niels Lohmann (for the same version).
- list of non-reproducible elements with:
  - explanation and justification
    - **Answer**: The only elements which are not reproducible are 8 CMake integration tests. The list of these, together with explanation and justification, is provided in TSF/docs/non_reproducible_tests.md.
  - details of what is not reproducible
    - **Answer**: The only elements which are not reproducible are 8 CMake integration tests. The list of these, together with explanation and justification, is provided in TSF/docs/non_reproducible_tests.md.
- evidence of configuration management for build instructions and infrastructure
  - **Answer**: Provided by JLS-10 and JLS-19.
- evidence of repeatable builds
  - **Answer**: Provided by JLS-53.

**Confidence scoring**

Calculate:

R = number of reproducible components (including sources which have no build stage)
N = number of non-reproducible
B = number of binaries
M = number of mirrored
X = number of things not mirrored

Confidence scoring for TA-RELEASES could possibly be calculated as
R / (R + N + B + M / (M + X))

**Checklist**

- How confident are we that all components are taken from within our
  controlled environment?
  - **Answer**: We are very confident that all components are taken from within our controlled environment, as there are currently no external components used within the nlohmann/json library (as documented in JLS-34).
- How confident are we that all of the tools we are using are also under our
  control?
  - **Answer**: All tools used by nlohmann/json are mirrored within our controlled environment eclipse-score/inc_nlohmann_json. Therefore, these tools are under full control of the Eclipse S-Core organisation.
- Are our builds repeatable on a different server, or in a different context?
  - **Answer**: Since there is no "build" of the header-only library, yes.
- How sure are we that our builds don't access the internet?
  - **Answer**: We are confident that our builds don't access the internet, since there is no "build" of the header-only library.
- How many of our components are non-reproducible?
  - **Answer**:  All of our components are reproducible, since we only use a single component, the nlohmann/json library.
- How confident are we that our reproducibility check is correct?
  - **Answer**: We are very confident that our reproducibility check is correct.
 
    
