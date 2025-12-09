---
level: 1.1
normative: true
references:
    - type: project_website
      url: "https://otterdog.eclipse.org/projects/automotive.score/repos/inc_nlohmann_json#rulesets"
      description: "Dashboard of the infrastructure configuration tool 'Otterdog', showing that the main branch of eclipse-score/inc_nlohmann_json is protected and requires code reviews for all merge requests."
evidence:
    type: https_response_time
    configuration:
        target_seconds: 2
        urls:
            - "https://otterdog.eclipse.org/projects/automotive.score/repos/inc_nlohmann_json#rulesets"
---

The mirror of nlohmann/json is configured via infrastructure under direct control, and rejects history rewrites.