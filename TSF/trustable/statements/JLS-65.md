---
level: 1.1
normative: true
references:
        - type:  project_website
          url: "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
          description: "OpenSSF Scorecard Report for the nlohmann/json library."
        - type: website
          url: "https://coveralls.io/github/nlohmann/json"
          description: "Coverage Report for the nlohmann/json library."
        - type: website
          url: "https://introspector.oss-fuzz.com/project-profile?project=json"
          description: "Most recent report for fuzzing introspection of the nlohmann/json library with historical plots."
evidence:
    type: https_response_time
    configuration:
        target_seconds: 2
        urls:
            - "https://scorecard.dev/viewer/?uri=github.com%2Fnlohmann%2Fjson"
            - "https://coveralls.io/github/nlohmann/json"
            - "https://introspector.oss-fuzz.com/project-profile?project=json"
---

Releases of the nlohmann/json library contain continuous-integration test reports such as coverage reports, fuzzing reports & OpenSSF scorecard reports.