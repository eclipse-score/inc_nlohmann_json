---
level: 1.1
normative: true
references:
  - type: project_website
    url: "https://json.nlohmann.me/community/contribution_guidelines/#update-the-documentation"
    description: "Contribution guidelines describing how to update and locally build the mkdocs-based documentation"
  - type: project_website
    url: "https://github.com/nlohmann/json/releases"
    description: "Release notes summarising behavioural changes and documentation updates for each version"
  - type: web_content
    url: "https://json.nlohmann.me"
    description: "Published documentation site for the nlohmann/json library"
evidence:
  type: https_response_time
  configuration:
    target_seconds: 2
    urls:
      - "https://json.nlohmann.me/community/contribution_guidelines/#update-the-documentation"
      - "https://github.com/nlohmann/json/releases"
---

For changes that affect the behaviour or public API of the nlohmann/json library, contributors manually update the library documentation and locally rebuild it for verification.
