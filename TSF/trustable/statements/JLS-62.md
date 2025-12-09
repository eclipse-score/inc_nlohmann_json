---
level: 1.1
normative: true
references:
  - type: website
    url: "https://github.com/nlohmann/json/blob/55f93686c01528224f448c19128836e7df245f72/README.md?plain=1#L1862"
    description: "README file of the nlohmann/json repository stating that 'ctest -LE not_reproducible' excludes non-reproducible tests."
  - type: website
    url: "https://github.com/nlohmann/json/issues/2324"
    description: "Issue in the nlohmann/json repository addressing tests that were non-reproducible."
  - type: verbose_file
    path: "./TSF/docs/non_reproducible_tests.md"
    description: "Overview and description of 8 non-reproducible CMake integration tests."
evidence:
  type: https_response_time
  configuration:
    target_seconds: 2
    urls:
      - "https://github.com/nlohmann/json/blob/55f93686c01528224f448c19128836e7df245f72/README.md?plain=1#L1862"
      - "https://github.com/nlohmann/json/issues/2324"
---

All tests except the ones which are excluded when using the flag "ctest -LE not_reproducible" are reproducible.