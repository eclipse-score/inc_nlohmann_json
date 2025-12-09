# Non-Reproducible Tests in nlohmann/json

## Overview

The nlohmann/json test suite includes 8 CMake integration tests (comprising 10 individual test executions) that are labeled as `not_reproducible`. These tests verify different methods of consuming the library in CMake-based projects but create build artifacts with timestamps and cached state that prevent bit-for-bit reproducible builds.

The non-reproducibility of all these tests is reasonable and justified.

These can be identified and found by searching for "LABELS not_reproducible" in the project.

## The 8 Non-Reproducible CMake Integration Tests

### 1. cmake_import (2 tests)

**Location:** `tests/cmake_import/`

**Test Names:**
- `cmake_import_configure`
- `cmake_import_build`

**What it tests:**
Verifies that the library can be found and used via CMake's `find_package(nlohmann_json)` mechanism after installation. This simulates how end users would consume an installed version of the library.

**Why non-reproducible:**
- Requires `JSON_Install=ON` to generate CMake config files (`nlohmann_jsonConfig.cmake`)
- Uses `find_package()` which searches for and reads installed CMake configuration files
- Generates CMakeCache.txt with absolute paths and timestamps in the test build directory
- Creates compiled executables (`with_namespace_target`, `without_namespace_target`) with timestamps
- Multiple runs produce different timestamps on all generated artifacts

---

### 2. cmake_import_minver (2 tests)

**Location:** `tests/cmake_import_minver/`

**Test Names:**
- `cmake_import_minver_configure`
- `cmake_import_minver_build`

**What it tests:**
Similar to `cmake_import`, but specifically tests that CMake's version constraint mechanism works correctly with `find_package(nlohmann_json 3.2.0 REQUIRED)`. Ensures the library properly declares its version in the CMake config files.

**Why non-reproducible:**
- Same reasons as `cmake_import`
- Additionally verifies version metadata in generated config files
- Creates timestamped build artifacts and CMake cache files

---

### 3. cmake_add_subdirectory (2 tests)

**Location:** `tests/cmake_add_subdirectory/`

**Test Names:**
- `cmake_add_subdirectory_configure`
- `cmake_add_subdirectory_build`

**What it tests:**
Verifies that the library can be embedded directly into a CMake project using `add_subdirectory()`. This is the most common integration method for projects that vendor their dependencies.

**Why non-reproducible:**
- Runs a nested CMake configuration in an isolated test directory
- Generates CMakeCache.txt with absolute source/binary paths and timestamps
- Builds multiple executables (`with_namespace_target`, `without_namespace_target`, `without_exceptions`)
- Each build creates object files, executables with embedded timestamps
- Subsequent runs create new artifacts with different timestamps
- CMake's incremental build cache persists between runs, causing different behavior

---

### 4. cmake_target_include_directories (2 tests)

**Location:** `tests/cmake_target_include_directories/`

**Test Names:**
- `cmake_target_include_directories_configure`
- `cmake_target_include_directories_build`

**What it tests:**
Verifies that the library headers can be used via direct `target_include_directories()` calls with both `PRIVATE` and `SYSTEM` variants. Also tests a specific regression from [discussion #2281](https://github.com/nlohmann/json/discussions/2281) regarding transitive include directories.

**Why non-reproducible:**
- Creates a full CMake build with libraries (Foo, Bar) and executables
- Generates CMakeCache.txt with absolute paths to source includes
- All compiled artifacts have timestamps
- Static libraries and executables accumulate with different modification times on each run

---

## Assertions and Reproducibility

Additionally, the nlohmann/json README notes that **assertions must be disabled** for fully reproducible builds (see [discussion #4494](https://github.com/nlohmann/json/discussions/4494)). This is because:

- Assertions often use `__FILE__` which embeds absolute source paths
- Different build machines have different paths
- This embeds environment-specific information into binaries

To ensure reproducible builds, compile with:
```bash
cmake -DCMAKE_BUILD_TYPE=Release  # Typically defines NDEBUG
# or explicitly:
cmake -DCMAKE_CXX_FLAGS="-DNDEBUG"
```

## Running Reproducible Tests Only

To run only reproducible tests:
```bash
# Exclude non-reproducible tests
ctest -LE not_reproducible

# Exclude both non-reproducible and git-required tests
ctest -LE "not_reproducible|git_required"
```

The project has a dedicated CI target that automatically excludes these tests:
```bash
cmake --build build --target ci_reproducible_tests
```
