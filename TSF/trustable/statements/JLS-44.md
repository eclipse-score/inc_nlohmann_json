---
level: 1.1
normative: true
references: 
  - type: project_website
    url: "https://github.com/nlohmann/json/blob/develop/.github/ISSUE_TEMPLATE/bug.yaml"
    description: "Bug report issue template for the nlohmann/json library"
  - type: project_website
    url: "https://github.com/nlohmann/json/blob/develop/.github/CONTRIBUTING.md#reporting-issues"
    description: "Contribution guidelines describing how to report bugs and issues for the nlohmann/json library"
evidence:
  type: https_response_time
  configuration:
    target_seconds: 2
    urls:
      - "https://github.com/nlohmann/json/blob/develop/.github/ISSUE_TEMPLATE/bug.yaml"
      - "https://github.com/nlohmann/json/blob/develop/.github/CONTRIBUTING.md#reporting-issues"
---

The manual process for reporting bugs in the nlohmann/json library is well defined and documented in the project's contribution guidelines and bug report template.