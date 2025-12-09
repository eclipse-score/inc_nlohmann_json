---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://github.com/nlohmann/json/releases/tag/v3.12.0"
          description: "release notes for v3.12.0, listing bugs, CVEs and warnings which were either fixed or mitigated since last release"
        - type: web_content
          url: "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
          description: "OpenSSF Scorecard Report for nlohmann/json, where scores for 'Vulnerabilities', 'Pinned-Dependencies' and 'Dangerous-Workflow' support this statement."
evidence:
        type: https_response_time
        configuration:
                target_seconds: 2
                urls:
                    - "https://github.com/nlohmann/json/releases/tag/v3.12.0"
score:
    Erikhu1: 0.7
---

Known bugs, misbehaviours and CVEs are analyzed and either fixed or mitigated in the nlohmann/json repository.