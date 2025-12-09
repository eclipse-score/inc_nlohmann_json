---
level: 1.1
normative: true
references:
    - type: project_website
      url: "https://github.com/nlohmann/json/blob/55f93686c01528224f448c19128836e7df245f72/README.md#used-third-party-tools"
      description: "List of third party tools used to build, test and document nlohmann/json v3.12.0."
    - type: verbose_file
      path: "./TSF/docs/third_party_tools_assessment.md"
      description: "Safety assessment of third party tools used in nlohmann/json v3.12.0."
evidence:
    type: https_response_time
    configuration:
        target_seconds: 2
        urls:
            - "https://github.com/nlohmann/json/blob/55f93686c01528224f448c19128836e7df245f72/README.md#used-third-party-tools"
---

All third party tools used in nlohmann/json for building, testing and documenting the project are assessed within eclipse-score/inc_nlohmann_json.