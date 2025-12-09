---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://introspector.oss-fuzz.com/project-profile?project=json"
          description: "most recent report for fuzzing introspection of nlohmann/json with historical plots"
        - type: web_content
          url: "https://storage.googleapis.com/oss-fuzz-introspector/json/inspector-report/20250824/fuzz_report.html"
          description: "persistent storage of fuzz-testing-report for nlohmann/json version 3.12.0 on 24.08.2025"
        - type: web_content
          url: "https://raw.githubusercontent.com/nlohmann/json/refs/heads/develop/.github/workflows/cifuzz.yml"
          description: "Configuration file for Fuzz-Testing pipeline in the original nlohmann/json repository"
        - type: web_content
          url: "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
          description: "OpenSSF Scorecard Report for nlohmann/json, where score for 'Fuzzing' supports this statement."
evidence:
        type: https_response_time
        configuration:
                target_seconds: 2
                urls:
                    - "https://introspector.oss-fuzz.com/project-profile?project=json"
score:
    Jonas-Kirchhoff: 1.0
    Erikhu1: 1.0
---

Fuzz testing is used in the nlohmann/json repository to uncover edge cases and failure modes throughout development.