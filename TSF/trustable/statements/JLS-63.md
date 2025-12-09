---
level: 1.1
normative: true
references:
        - type: web_content
          url: "https://www.bestpractices.dev/en/projects/289?criteria_level=1#section_project_oversight"
          description: "OpenSSF Best Practices Report for nlohmann/json, where within 'Project Oversight' it states that the Developer Certificate of Origin (DCO) is enforced via the DCO GitHub app (https://github.com/settings/installations/58991705) as of December 30, 2024."
        - type: web_content
          url: "https://developercertificate.org/"
          description: "The Developer Certificate of Origin in its original formulation."
        - type: project_website
          url: "https://github.com/nlohmann/json/discussions/4578"
          description: "Announcement by Niels Lohmann that as of January 1, 2025, the project will require DCO (https://developercertificate.org) for all merge requests."
evidence:
        type: https_response_time
        configuration:
          target_seconds: 2
          urls:
          - "https://github.com/nlohmann/json/discussions/4578"
---

Releases of the nlohmann/json library contain commit sign-offs.
