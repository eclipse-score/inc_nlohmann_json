---
level: 1.1
normative: true
references:
    - type: project_website
      url: "https://github.com/nlohmann/json/discussions/5022"
      description: "Clarification by @nlohmann that all PRs not created by @nlohmann will be reviewed by him, while not all of his PRs are reviewed in practice."
    - type: project_website
      url: "https://github.com/nlohmann/json/pulls?q=is%3Apr+is%3Aclosed+is%3Amerged"
      description: "List of all merged Pull Requests of the nlohmann/json repository."
evidence:
    type: https_response_time
    configuration:
        target_seconds: 2
        urls:
        - "https://github.com/nlohmann/json/discussions/5022"
        - "https://github.com/nlohmann/json/pulls?q=is%3Apr+is%3Aclosed+is%3Amerged"
---

Releases of the nlohmann/json library contain Github pull request approvals.