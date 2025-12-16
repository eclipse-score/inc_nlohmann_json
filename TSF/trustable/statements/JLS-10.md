---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://github.com/nlohmann/json/releases"
          description: "List of nlohmann/json releases consisting of source code, build instructions, test code and test result summaries."
evidence:
    type: https_response_time
    configuration:
        target_seconds: 2
        urls: 
          - "https://github.com/nlohmann/json/releases"
---

Every release of the nlohmann/json library includes source code, build instructions, test code and test results summaries.