---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
          description: "OpenSSF Scorecard Report for nlohmann/json, where score for 'CI-Tests' supports this statement"
        - type: project_website
          url: "https://github.com/nlohmann/json/pulls?q=is%3Apr+is%3Aclosed+review%3Aapproved"
          description: "All approved pull requests in the nlohmann/json repository, with the results of the CI pipeline executions."
evidence:
        type: https_response_time
        configuration:
                target_seconds: 2
                urls:
                    - "https://github.com/nlohmann/json/pulls?q=is%3Apr+is%3Aclosed+review%3Aapproved"
                    - "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
score:
    Erikhu1: 0.9
    aschemmel-tech: 1.0
---

Pull requests in the nlohmann/json repository are merged only after running CI-tests and successfully passing the pipeline.

aschemmel-tech: evidences support statement