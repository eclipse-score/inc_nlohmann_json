---
level: 1.1
normative: true
references:
  - type: project_website
    url: "https://github.com/nlohmann/json/security/policy"
    description: "Security policy describing how to report vulnerabilities for the nlohmann/json library"
  - type: project_website
    url: "https://github.com/nlohmann/json/security/advisories/new"
    description: "Well-defined process for issuing a vulnerability or bug report for the nlohmann/json library"
evidence:
  type: https_response_time
  configuration:
    target_seconds: 2
    urls:
      - "https://github.com/nlohmann/json/security/advisories/new"
      - "https://github.com/nlohmann/json/security/policy"
---

The manual process for reporting vulnerabilities in the nlohmann/json library is well defined and documented in the project's security policy and vulnerability reporting template.