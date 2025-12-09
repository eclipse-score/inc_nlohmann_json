---
level: 1.1
normative: true
references:
  - type: project_website
    url: "https://github.com/nlohmann/json/discussions/categories/ideas"
    description: "Feature request discussions showing that feature requests are actively investigated and answered"
  - type: project_website
    url: "https://github.com/nlohmann/json/blob/develop/.github/CODEOWNERS"
    description: "Definition of responsible owners and reviewers for the nlohmann/json repository"
evidence:
  type: https_response_time
  configuration:
    target_seconds: 2
    urls:
      - "https://github.com/nlohmann/json/discussions/categories/ideas"
      - "https://github.com/nlohmann/json/blob/develop/.github/CODEOWNERS"
---

Feature requests for the nlohmann/json repository are raised in the project's GitHub discussions and are actively reviewed and answered by the maintainer.