---
level: 1.1
normative: true
references:
  - type: project_website
    url: "https://github.com/nlohmann/json"
    description: "Start-page of the original nlohmann/json project"
  - type: project_website
    url: "https://github.com/eclipse-score/inc_nlohmann_json"
    description: "Start-page of the mirror of nlohmann/json within Eclipse S-CORE"
  - type: project_website
    url: "https://github.com/eclipse-score/inc_nlohmann_json/blob/main/single_include/nlohmann/json.hpp"
    description: "The single header file that contains all the source code downstream users need."
  - type: project_website
    url: "https://github.com/eclipse-score/inc_nlohmann_json/tree/main/include/nlohmann"
    description: "The modular header files, containing all the source code which is amalgamated into the single header file."
evidence:
  type: https_response_time
  configuration:
    target_seconds: 2
    urls:
      - "https://github.com/nlohmann/json"
      - "https://github.com/eclipse-score/inc_nlohmann_json"
      - "https://github.com/eclipse-score/inc_nlohmann_json/blob/main/single_include/nlohmann/json.hpp"
      - "https://github.com/eclipse-score/inc_nlohmann_json/tree/main/include/nlohmann"
---

All source code of the nlohmann/json library is mirrored within eclipse-score/inc_nlohmann_json.