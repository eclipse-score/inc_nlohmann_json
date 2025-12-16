---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
          description: "OpenSSF Scorecard Report for nlohmann/json, where scores for 'Security-Policy' and 'Code-Review' reflect this statement."
        - type: project_website
          url: "https://github.com/nlohmann/json?tab=contributing-ov-file#readme"
          description: "Contribution Guidelines for nlohmann/json, where it is indirectly indicated that all changes are reviewed."
evidence:
        type: https_response_time
        configuration:
                target_seconds: 2
                urls:
                    - "https://github.com/nlohmann/json?tab=contributing-ov-file#readme"
                    - "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
score:
    Erikhu1: 0.8
---

Malicious code changes in nlohmann/json are mitigated by code reviews, adhering to the contribution guidelines and security policy specified by nlohmann/json.