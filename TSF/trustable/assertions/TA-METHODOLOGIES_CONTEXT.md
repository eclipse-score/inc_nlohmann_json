---
level: 1.1
normative: false
---

(Note: The guidance, evidence, confidence scoring and checklist sections below are copied from [CodeThink's documentation of TSF](https://codethinklabs.gitlab.io/trustable/trustable/trustable/TA.html). However, the answers to each point in the evidence list and checklist are specific to this project.)

**Guidance**

To satisfy this assertion, all manual processes used in the verification of nlohmann/json must be documented, including the methodologies applied, the results for specific aspects and iterations, and evidence that these processes were reviewed against documented criteria.

Most analysis (e.g., data analysis for TA-ANALYSIS) should be automated to enable continuous feedback.
However, the quality of any remaining manual processes (whether from first parties or external third parties) must be considered and how they are documented and reviewed.
Considerations should be made about how manual processes may impact identifying and addressing Misbehaviours (TA-MISBEHAVIOURS).

Assignment of responsibilities for any manual work must follow a documented process that verifies competence and grants appropriate access, with automation applied where possible.
Resulting assigned responsibilities must ensure organisational robustness (e.g., avoidance of conflicts of interest) together with appropriate independent verification and validation.
Manual reviews involving source inspections must follow documented guidelines, with exceptions recorded and illustrated through examples.
These guidelines should evolve over time and cover:

- coding patterns (e.g., good patterns, anti-patterns, defensive coding)
- structured design practices (e.g., control flow constraints)
- complexity management (e.g., limiting feature creep)
- documentation (e.g., clear, formal figures and diagrams)
- feature subset restrictions (e.g., programming language subsets)
- code of conduct guidelines (e.g., review etiquette, handling disagreements)

Nevertheless, specific coding rules (e.g., memory allocation, typing, concurrency) should be integrated into automatic linting and static analysis tools where appropriate.

All processes and checks must themselves be reviewed to drive continuous improvement following specified guidelines.
Any resulting changes from reviews must follow change control, regardless of who initiates them or under what circumstances.

**Evidence**

- Manual process documentation
  - **Answer**: Manual processes relevant for nlohmann/json have been identified and documented (see JLS-36, 40, 41, 42, 43 and 44).
- References to methodologies applied as part of these processes
  - **Answer**: The corresponding references are given for each statement (see JLS-36, 40, 41, 42, 43 and 44).
- Results of applying the processes
  - **Answer**: Results include reviewed and merged pull requests, maintained high test coverage, published security advisories and resolved issues, updated documentation on json.nlohmann.me (see JLS-36, 40, 41, 42, 43 and 44).
- Criteria used to confirm that the processes were applied correctly
  - **Answer**: The criteria are given in the documentation (see JLS-36, 40, 41, 42, 43 and 44).
- Review records for results
  - **Answer**: Review records are provided by GitHub pull-request reviews and comments, issue and advisory discussions, as well as release notes describing behavioural and documentation changes (see JLS-36, 40, 41, 42, 43 and 44).

**Confidence scoring**

Confidence scoring for TA-METHODOLOGIES is based on identifying areas of need for
manual processes, assessing the clarity of proposed processes, analysing the
results of their implementation, and evaluating the evidence of effectiveness
in comparison to the analysed results

**Checklist**

- Are the identified gaps documented clearly to justify using a manual process?
  - **Answer**: Manual processes are introduced where automation is not feasible and are clearly documented. While no explicit justification for each manual step is provided, the rationale is generally clear from the surrounding context.
- Are the goals for each process clearly defined?
  - **Answer**: Yes. For the manual processes that were found the goals are clearly defined in the corresponding documentation. The goals include ensuring that user-facing documentation accurately reflect behavioural and API changes, correctly handling bug and vulnerability reports, and keeping the test suite at (or close to) 100% coverage for non-trivial changes.
- Is the sequence of procedures documented in an unambiguous manner?
  - **Answer**: Largely yes. Where necessary, examples and templates make the expected sequence explicit.
- Can improvements to the processes be suggested and implemented?
  - **Answer**: Improvements are proposed via GitHub issues or pull request.
- How frequently are processes changed?
  - **Answer**: Process changes are infrequent and usually happen with a new nlohmann/json release, when a need for improvement is identified. 
- How are changes to manual processes communicated?
  - **Answer**: Mostly, changes are communicated through updated documentation in the repository and release notes.
- Are there any exceptions to the processes?
  - **Answer**: Known exceptions include automatic dependency updates from Dependabot as well as smaller trivial changes (such as fixing typos in documentation). These are exempted from having to manually create issues and explain the rationale behind the change. 
- How is evidence of process adherence recorded?
  - **Answer**: Evidence in GitHub; PR histories with reviews and passing checks, issue and advisory discussions, audit trails for documentation and test updates
- How is the effectiveness of the process evaluated?
  - **Answer**: Effectiveness is evaluated indirectly via stable releases, test coverage, and documentation quality.
- Is ongoing training required to follow these processes?
  - **Answer**: No formal training is required, but contributors are expected to be familiar with the contribution guidelines and security policy.
