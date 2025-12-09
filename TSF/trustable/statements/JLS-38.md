---
level: 1.1
normative: true
references:
        - type: website
          url: "https://json.nlohmann.me/integration/cmake/"
          description: "cmake build management documentation for nlohmann/json"
        - type: website
          url: "https://json.nlohmann.me/integration/package_managers/"
          description: "package manager documentation for nlohmann/json"
evidence:
        type: https_response_time
        configuration:
                target_seconds: 2
                urls:
                    - "https://json.nlohmann.me/integration/cmake/"
                    - "https://json.nlohmann.me/integration/package_managers/"
---

Every release of the nlohmann/json library shall provide configuration management for build instructions and infrastructure.