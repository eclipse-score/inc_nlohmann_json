---
level: 1.1
normative: true
references:
        - type: project_website
          url: "https://github.com/nlohmann/json/blob/55f93686c01528224f448c19128836e7df245f72/.github/workflows/ubuntu.yml"
          description: "Ubuntu workflow of nlohmann/json release v3.12.0, containing specific commit SHAs for all Github Actions, in e.g., lines 24, 36, 118, etc."
evidence:
        type: https_response_time
        configuration:
                target_seconds: 2
                urls:
                    - "https://github.com/nlohmann/json/blob/55f93686c01528224f448c19128836e7df245f72/.github/workflows/ubuntu.yml"
---

Any Github Actions used in the testing process are pinned to specific commit SHAs to ensure consistent action behavior across runs.
