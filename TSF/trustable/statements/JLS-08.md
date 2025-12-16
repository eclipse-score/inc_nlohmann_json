---
level: 1.1
normative: true
references:
    - type: web_content
      url: "https://eclipse-score.github.io/inc_nlohmann_json/main/generated/dashboard.html#summary"
      description: "Dashboard showing distributions of evidence scores and SME (subject-matter expert) scores."
    - type: project_website
      url: "https://eclipse-score.github.io/inc_nlohmann_json/main/generated/trustable_report_for_Software.html"
      description: "Trustable Compliance Report showing scores for statements."
    - type: web_content
      url: "https://codethinklabs.gitlab.io/trustable/trustable/methodology.html#documenting-assumptions"
      description: "Definition of Assumptions as part of the methodology"
evidence:
    type: https_response_time
    configuration:
        target_seconds: 2
        urls: 
          - "https://eclipse-score.github.io/inc_nlohmann_json/main/generated/trustable_report_for_Software.html"
---

Each leaf node in the Trustable Graph that is not an Assumption-of-Use (AoU) is scored either based on SME review(s) alone or on a combination of SME review(s) and an automatic validator.
