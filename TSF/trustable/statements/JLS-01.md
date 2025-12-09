---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://github.com/nlohmann/json/blob/develop/.github/workflows/ubuntu.yml#L9"
          description: "The trigger condition for the CI workflow that executes the test suites."
evidence:
        type: https_response_time
        configuration:
                target_seconds: 2
                urls:
                    - "https://github.com/nlohmann/json/blob/develop/.github/workflows/ubuntu.yml#L9"
score:
    Jonas-Kirchhoff: 1.0
    Erikhu1: 1.0
---

The CI pipeline in the upstream nlohmann/json repository executes the unit and integration test suites on each pull request (opened, reopened, synchronized).