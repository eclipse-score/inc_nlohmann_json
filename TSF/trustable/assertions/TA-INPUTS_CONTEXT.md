---
level: 1.1
normative: false
---

(Note: The guidance, evidence, confidence scoring and checklist sections below are copied from [CodeThink's documentation of TSF](https://codethinklabs.gitlab.io/trustable/trustable/trustable/TA.html). However, the answers to each point in the evidence list and checklist are specific to this project.)

**Guidance**

Anything that can influence the output of the nlohmann/json project is considered an input.
This includes:

- Software components used to implement specified features and meet defined Expectations
- Software tools, and their outputs, used for design, construction and verification
- Infrastructure that supports development and release processes

All inputs (components, tools, data) and their dependencies (recursively) used to build and verify nlohmann/json releases must be identified and assessed, since they are untrusted by default.

Each input should be evaluated on verifiable merits, regardless of any claims it makes (including adherence to standards or guidance).
Evaluation must include the project's defined Expectations to ensure that inputs meet requirements, and that risks are recorded and addressed appropriately.

For components, we need to consider how their misbehaviour might impact achieving project nlohmann/json's Expectations.
Sources (e.g. bug databases, advisories) for known risks should be identified, their update frequency recorded, and tests defined for detecting them.
These form the inputs to TA-FIXES.

For the tools used to construct and verify nlohmann/json, we need to consider how their misbehaviour could:

- Introduce unintended changes
- Fail to detect Misbehaviours during testing
- Produce misleading data used to design or verify the next iteration

Where any input impacts are identified, consider:

- How serious their impact might be, and whether Expectations or analysis outcomes are affected (severity)
- Whether they are detected by another tool, test, or manual check (detectability)

Confidence in assessing severity and detectability can be supported by analysing development history and practices of each input to evaluate upstream sources (both third-party and first-party) for maintainability and sustainability (including, for example, testability, modularity and configurability) to reduce failure impact and support safe change.

These qualities can be estimated through evidence of software engineering best practice, applied through:

- Processes defining and following design, documentation and review guidelines, carried out manually (advocating simple design, reuse, structured coding constructs, and competent release management)
- Appropriate use of programming languages and their features, supported by tools such as static analysis, with regular improvement of their configurations

For impacts with high severity or low detectability (or both), additional analysis should assess whether existing tests effectively detect Misbehaviours and their impacts.

As a result, for example, any binary inputs without reproducible build steps or clear development history and maintenance processes should be treated as risks and mitigated appropriately.

**Evidence**

- List of components used to build nlohmann/json, including:
  - Whether content is provided as source or binary
    - **Answer**: The nlohmann/json library consists of only source code in the form of a single header file, and has no binary artifacts (see JLS-47).
- Record of component assessments:
  - Originating project and version
    - **Answer**: The nlohmann/json library has no external components (see JLS-34).
  - Date of assessments and identity of assessors
    - **Answer**: The nlohmann/json library has no external components (see JLS-34).
  - Role of component in nlohmann/json
    - **Answer**: The nlohmann/json library has no external components (see JLS-34).
  - Sources of bug and risk data
    - **Answer**: The nlohmann/json library has no external components (see JLS-34).
  - Potential misbehaviours and risks identified and assessed
    - **Answer**: The nlohmann/json library has no external components (see JLS-34).
- List of tools used to build and verify nlohmann/json
  - **Answer**: Provided in JLS-48 and JLS-49.
- Record of tool assessments:
  - Originating project and tool version
    - **Answer**: Provided in JLS-48 and JLS-50.
  - Date of assessments and identity of assessors
    - **Answer**: Provided in JLS-50.
  - Role of the tool in nlohmann/json releases
    - **Answer**: Provided in JLS-48 and JLS-50.
  - Potential misbehaviours and impacts
    - **Answer**: Provided in JLS-50.
  - Detectability and severity of impacts
    - **Answer**: Provided in JLS-50.
- Tests or measures to address identified impacts
  - **Answer**: Provided in JLS-50.

**Confidence scoring**

Confidence scoring for TA-INPUTS is based on the set of components and tools
identified, how many of (and how often) these have been assessed for their risk
and impact for nlohmann/json, and the sources of risk and issue data identified.

**Checklist**

- Are there components that are not on the list?
  - **Answer**: No, the nlohmann/json library has no components besides the single hpp header file. 
- Are there assessments for all components?
  - **Answer**: The nlohmann/json library has no components besides the single hpp header file. 
- Has an assessment been done for the current version of the component?
  - **Answer**: The nlohmann/json library has no components besides the single hpp header file. 
- Have sources of bug and/or vulnerability data been identified?
  - **Answer**: The nlohmann/json library has no components besides the single hpp header file. 
- Have additional tests and/or Expectations been documented and linked to
  component assessment?
  - **Answer**: The nlohmann/json library has no components besides the single hpp header file.
- Are component tests run when integrating new versions of components?
  - **Answer**: The nlohmann/json library has no components besides the single hpp header file.
- Are there tools that are not on the list?
  - **Answer**: No tools have been identified which are not listed.
- Are there impact assessments for all tools?
  - **Answer**: Yes, see JLS-50.
- Have tools with high impact been qualified?
  - **Answer**: Yes, see JLS-50.
- Were assessments or reviews done for the current tool versions?
  - **Answer**: Yes, see JLS-50.
- Have additional tests and/or Expectations been documented and linked to
  tool assessments?
  - **Answer**: Yes, the CI-pipeline includes tests on some third party tools, see JLS-50.
- Are tool tests run when integrating new versions of tools?
  - **Answer**: Yes, the tool tests are integrated into the CI-pipeline, see JLS-50.
- Are tool and component tests included in release preparation?
  - **Answer**: The tool tests are integrated into the CI-pipeline, see JLS-50.
- Can patches be applied, and then upstreamed for long-term maintenance?
  - **Answer**: Yes, if ever a misbehaviour is found and patched, then a pull-request to the original project repository can be opened to upstream the changes.
- Do all dependencies comply with acceptable licensing terms?
  - **Answer**: Yes, the library is licensed under MIT License.
