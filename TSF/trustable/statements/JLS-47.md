---
level: 1.1
normative: true
references:
    - type: project_website
      url: "https://github.com/nlohmann/json/blob/develop/single_include/nlohmann/json.hpp"
      description: "Path to the header file that the json library consists of."
evidence:
    type: https_response_time
    configuration:
        target_seconds: 2
        urls:
            - "https://github.com/nlohmann/json/blob/develop/single_include/nlohmann/json.hpp"
score:
    Erikhu1: 1.0
---

The nlohmann/json library only consists of source code in the form of a single header file, and has no binary artifacts.
