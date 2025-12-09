---
level: 1.1
normative: true
references: 
    - type: verbose_file
      path: "./TSF/scripts/README.md"
      description: "Explanation of how test-result data is stored, how long it is retained, which size limits apply, and which maintenance actions are required for the persistent storage."
    - type: file
      path: "./TSF/scripts/capture_test_data_memory_sensitive.py"
      description: "Implementation of memory-sensitive storage with heuristic limits on the number of stored test results and workflow metadata, and explicit failure behaviour when limits are exceeded."
---

The storage location, retention limits, and intended use of captured test result data for eclipse-score/inc_nlohmann_json are documented so that the scope and reproducibility of the available test data can be understood.