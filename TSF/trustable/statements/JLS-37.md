---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://eclipse-score.github.io/inc_nlohmann_json/main/generated/trustable_report_for_Software.html#compliance-for-ta"
          description: "Trustable Compliance Report showing scores for different TA items."
        - type: project_website
          url: "https://eclipse-score.github.io/inc_nlohmann_json/main/generated/trustable_graph.html"
          description: "presentation of the full trustable graph in which high-level statements are broken down"
evidence:
  type: https_response_time
  configuration:
    target_seconds: 2
    urls:
      - "https://eclipse-score.github.io/inc_nlohmann_json/main/generated/trustable_report_for_Software.html#compliance-for-ta"
      - "https://eclipse-score.github.io/inc_nlohmann_json/main/generated/trustable_graph.html"
---

High-level statements are decomposed into smaller, recursive statements.