---
level: 1.1
normative: true
references:
        - type: verbose_file
          path: ".github/workflows/dependency-review.yml"
          description: "The workflow scans PRs for dependency changes and vulnerabilities."
evidence:
  type: "check_artifact_exists"
  configuration:
    check_amalgamation: exclude
    codeql: exclude
    dependency_review: include
    labeler: exclude
    publish_documentation: exclude
    test_trudag_extensions: exclude
    ubuntu: exclude
score:
    Jonas-Kirchhoff: 1.0
    Erikhu1: 1.0
    aschemmel-tech: 1.0
---

External dependencies within nlohmann/json are checked for potential security vulnerabilities with each pull request to main. Merging is blocked until all warnings are resolved.