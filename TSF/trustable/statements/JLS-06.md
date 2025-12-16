---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
          description: "OpenSSF Scorecard Report for nlohmann/json, where score for 'Code-Review' reflects this statement."
evidence:
        type: https_response_time
        configuration:
                target_seconds: 2
                urls:
                    - "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
score:
    Erikhu1: 0.3
    aschemmel-tech: 0.4
---

Pull requests in the nlohmann/json repository are merged only after code review.

aschemmel-tech: taken over score from "OpenSSF Scorecard Report"
