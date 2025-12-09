---
level: 1.1
normative: true
references:
    - type: workflow_failures
      owner: "nlohmann"
      repo: "json"
      branch: "master"
    - type: project_website
      url: "https://github.com/nlohmann/json/actions?query=branch%3Amaster"
      description: "CI workflow history for the master branch of nlohmann/json."
evidence:
    type: https_response_time
    configuration:
        target_seconds: 2
        urls:   
            - "https://github.com/nlohmann/json/actions?query=branch%3Amaster"
score:
    Jonas-Kirchhoff: 1.0
    Erikhu1: 1.0
---

Any failed CI pipeline executions in the master branch of the nlohmann/json repository are analyzed and fixed.