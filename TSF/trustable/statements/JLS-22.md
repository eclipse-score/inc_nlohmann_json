---
level: 1.1
normative: true
references:
  - type: verbose_file
    path: "./.github/workflows/parent-workflow.yml"
    description: "Parent GitHub workflow that is scheduled to run daily and triggers the ubuntu workflow."
  - type: verbose_file
    path: "./.github/workflows/ubuntu.yml"
    description: "Ubuntu CI workflow that executes the nlohmann/json unit and integration tests in a controlled CI environment."
  - type: file
    path: "./TSF/scripts/capture_test_data_memory_sensitive.py"
    description: "Captures results from each workflow run and appends them to the persistent test results database."
score:
    Jonas-Kirchhoff: 1.0
---

A scheduled GitHub workflow in eclipse-score/inc_nlohmann_json triggers the nlohmann/json unit and integration test at least once per day and records their outcomes as time-stamped entries in the persistent test results database.