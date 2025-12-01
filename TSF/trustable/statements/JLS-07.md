---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://github.com/nlohmann/json/actions?query=event%3Apush+branch%3Adevelop"
          description: "List of all pushes to the develop branch in nlohmann/json, showing that all commits are done by nlohmann and indicating that direct commits are not possible."
evidence:
        type: https_response_time
        configuration:
                target_seconds: 2
                urls:
                    - "https://github.com/nlohmann/json/actions?query=event%3Apush+branch%3Adevelop"
score:
    Jonas-Kirchhoff: 1.0
    Erikhu1: 1.0
    aschemmel-tech: 1.0
---

The develop branch of nlohmann/json is protected, i.e. no direct commits are possible.

aschemmel-tech: no other pushes as from nlohman are observable
