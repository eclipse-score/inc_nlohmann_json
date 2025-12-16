---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://github.com/nlohmann/json/releases/tag/v3.12.0"
          description: "release notes for v3.12.0, listing bugs, CVEs and warnings which were either fixed or mitigated since last release"
        - type: project_website
          url: "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
          description: "OpenSSF Scorecard Report for nlohmann/json, where scores for 'Vulnerabilities', 'Pinned-Dependencies' and 'Dangerous-Workflow' support this statement."
evidence:
        type: https_response_time
        configuration:
                target_seconds: 2
                urls:
                    - "https://github.com/nlohmann/json/releases/tag/v3.12.0"
                    - "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
score:
    Erikhu1: 0.7
    aschemmel-tech: 0.8
---

Known bugs, misbehaviours and CVEs are analyzed and either fixed or mitigated in the nlohmann/json repository.

aschemmel-tech: evidences support bugs and CVE fixing, no mitigation actions are offered.