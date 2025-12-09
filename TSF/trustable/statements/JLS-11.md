---
level: 1.1
normative: true
references:
        - type: website
          url: "https://github.com/eclipse-score/inc_nlohmann_json/blob/save_historical_data/TSF/misbehaviours.md"
          description: "List of outstanding bugs as well as fixes for developed code that are outstanding, not yet applied."
evidence:
    type: check_issues
    configuration:
        release_date: "2025-04-11T08:43:39Z"
        list_of_known_misbehaviours: "./TSF/docs/nlohmann_misbehaviours_comments.md"
score:
    Erikhu1: 1.0
---

Outstanding bugs or misbehaviours are analyzed within eclipse-score/inc_nlohmann_json to determine whether they are relevant for S-CORE's use cases of the nlohmann/json library.
