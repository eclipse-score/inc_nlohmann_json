---
level: 1.1
normative: true
references:
        - type: web_content
          url: "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
          description: "OpenSSF Scorecard Report for nlohmann/json, where score for 'Vulnerabilities' shows that there are no outstanding CVEs."
        - type: web_content
          url: "https://github.com/nlohmann/json/discussions/4975"
          description: "Screenshot of dismissed code scanning alerts, which can also be dismissed in S-CORE."

score:
    Erikhu1: 0.5
    aschemmel-tech: 1.0
---

Outstanding CVEs are analyzed within eclipse-score/inc_nlohmann_json to determine whether they can be dismissed, and/or are relevant for S-CORE's use cases of the nlohmann/json library.

aschemmel-tech: In my understanding bot evidences support the statement completely.