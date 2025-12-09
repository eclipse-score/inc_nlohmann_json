# Failure rate analysis for nlohmann/json Ubuntu CI

## Scope and data source

- **Repository:** `nlohmann/json`
- **Workflow:** `.github/workflows/ubuntu.yml`
- **Date range:** 2025-01-11 – 2025-04-11  (3 months before the release date of the version v3.12.0)
- **Filter:** `workflow_file_name: ubuntu.yml`

GitHub’s “failure rate” counts all non-successful job runs, including cancelled
jobs (e.g. quickly closed PRs) and infrastructure/tooling problems, not only
true regressions in the JSON library.

## Jobs with the highest reported failure rates

From the Jobs table (sorted by Failure rate):

| Job (short name)                           | Failure rate | Avg. run time | Job runs |
|:-------------------------------------------|-------------:|--------------:|---------:|
| `ci_test_coverage_clang`                   | **50 %**     | 5m 33s        |        6 |
| `ci_static_analysis_clang (ci_clang_tidy)` | **14 %**     | 15m 36s       |      247 |
| `ci_test_coverage`                         | **13 %**     | 9m 19s        |      248 |
| `ci_test_clang`                            | **12 %**     | 6m 12s        |       25 |
| `ci_test_documentation`                    | 4 %          | 59s           |      232 |
| `ci_static_analysis_clang (ci_test_clang)` | 4 %          | 6m 41s        |      214 |
| `ci_test_gcc`                              | 4 %          | 6m 27s        |      245 |
| `ci_cmake_options`                         | 3 %          | 6m 01s        |      248 |
| `ci_test_standards_clang`                  | 3 %          | 2m 50s        |      222 |
| `ci_test_compiler_gcc`                     | 3 %          | 3m 28s        |      227 |



The remaining jobs are at or below ~3 %, many at ≈0 %.
The remaining data can be found on the GitHub [insights page](https://github.com/nlohmann/json/actions/metrics/performance?dateRangeType=DATE_RANGE_TYPE_CUSTOM&sort=failureRate&tab=jobs&filters=workflow_file_name%3Aubuntu.yml&range=1736553600000-1744329600000).

## Interpretation of the higher failure rates

### `ci_test_coverage_clang`

This job was a short-lived Clang coverage experiment. In the selected time window it only ran 6 times, several of them as part of the "Fix coverage job" pull request where the coverage script was intentionally broken and iteratively fixed. The failures in these runs are due to coverage tooling / CI configuration issues, not failing unit tests or misbehaviour in the JSON library.

### `ci_static_analysis_clang (ci_clang_tidy)`

In the analyzed period, most failed `ci_static_analysis_clang (ci_clang_tidy)` runs come from a few PRs that deliberately changed static analysis or CI tooling, plus real bug fix. In particular, PR [#4654](https://github.com/nlohmann/json/pull/4654) "Fix ~basic_json causing std::terminate", PR [#4663](https://github.com/nlohmann/json/pull/4663) "Add clang-tidy plugin to convert implicit conversions to explicit ones", and the change referenced as [#4701](https://github.com/nlohmann/json/pull/4701) "Suppress clang-analyzer-webkit.NoUncountedMemberChecker" all show multiple failed Ubuntu workflow runs while their clang-tidy / analyzer configuration was being tuned. Because this job treats every clang-tidy or analyzer diagnostic as a hard error, each new or stricter check initially makes the job fail until the warnings are fixed or suppressed. The resulting ~14 % failure rate is therefore explained by intentional tightening and maintenance of the static-analysis pipeline (plus normal PR iteration), rather than by unexplained or unaddressed misbehaviour in the library itself.

### `ci_test_coverage` 

The failure rate of `ci_test_coverage` in this period is explained by intentional CI maintenance rather than unstable tests. A significant portion of failures comes from work on PR [#4595](https://github.com/nlohmann/json/pull/4595), where the coverage workflow itself was updated and repeatedly executed on the `fix-coverage` branch and several intermediate runs failed until the configuration of `gcov`, `lcov`, and the Coveralls uploader was corrected. Additional failures stem from PR [#4709](https://github.com/nlohmann/json/pull/4709), which upgraded the minimum CMake version and introduced new CMake and OpenSSL configurations in CI. During this transition, some `ubuntu.yml` workflow runs, including the coverage job, failed until the revised toolchain setup was stabilized. All changes were merged only after `ci_test_coverage` succeeded, and the underlying unit tests remained consistently green throughout, meaning the elevated failure rate reflects CI/tooling evolution rather than regressions in the JSON library.


### `ci_test_clang`

Historically, `ci_test_clang` existed as its own standalone job in the Ubuntu workflow. With PR [#4560](https://github.com/nlohmann/json/pull/4560) (“Clean up and document project files”), the Ubuntu workflow was reorganized and `ci_test_clang` was moved into the matrix of the `ci_static_analysis_clang` job (i.e. `matrix.target: [ci_test_clang, ci_clang_tidy, …]` in `.github/workflows/ubuntu.yml`). GitHub Actions always uses the workflow file from the commit on which a PR is based, so PRs that branch off **before** [#4560](https://github.com/nlohmann/json/pull/4560) and are never rebased still run the *old* workflow, while newer PRs run the *new* workflow where `ci_test_clang` only appears as a matrix target of `ci_static_analysis_clang`. This is why `ci_test_clang` shows up in different ways in the metrics, even though it ultimately refers to the same underlying CMake target.

In this period, `ci_test_clang` ran 25 times and failed 3 times (12%). All failures occurred on PR branches while Clang related code or CI configuration was being adjusted and were resolved before the respective changes were merged. In addition, because `ci_test_clang` was later removed as a standalone Ubuntu job and replaced, the statistics for this job are based on a relatively small number of historical runs. A few legitimate work-in-progress failures therefore translate into a comparatively high percentage, without indicating persistent instability of the Clang test setup.


## Conclusion

For the selected three-month window before the v3.12.0 release, the Ubuntu CI for `nlohmann/json` shows a small set of jobs with noticeably higher failure rates, but in all cases these can be traced back to intentional CI/tooling work or strict analysis settings, not to undetected misbehaviour of the library itself. All of these high failure rates occurred on PR branches, were visible to developers, and were resolved before merging, while the majority of other jobs (including `ci_test_gcc`, `ci_test_standards_*` and most compiler-matrix entries) remain at or near 0 %. Taken together, this indicates a stable CI system that reacts as intended to real issues and configuration changes, with no evidence of systematic, unexplained spikes in test failures for the Ubuntu workflow.


# Failure rate analysis for eclipse-score/inc_nlohmann_json Parent-Workflow/Ubuntu CI

## Scope and data source

- **Repository:** `eclipse-score/inc_nlohmann_json`
- **Workflow:** `Parent Workflow` (top-level CI workflow)
- **Date range:** last 90 days from 08.12.2025
- **Filter:** `workflow_file_name: parent-workflow.yml`


GitHub’s “failure rate” counts all non-successful job runs, including cancelled
jobs (e.g. quickly closed PRs) and infrastructure/tooling problems, not only
true regressions in the JSON library.

## Jobs with the highest reported failure rates

From the Jobs table (sorted by Failure rate):

| Job (short name)                                      | Failure rate | Avg. run time | Job runs |
|:------------------------------------------------------|-------------:|--------------:|---------:|
| `Run Ubuntu Workflow / publish_test_data_success`     | **5%**       | ≈ 25 s        |      38  |
| `Run Labeler Workflow / clone_missing_labels`         | **3%**       | ≈ 6 s         |      38  |

All other Parent-Workflow jobs in the last 90 days report a failure rate of
**0 %** over 38 runs each. The remaining data can be found on the GitHub [insights page](https://github.com/eclipse-score/inc_nlohmann_json/actions/metrics/performance?dateRangeType=DATE_RANGE_TYPE_LAST_90_DAYS&sort=failureRate&tab=jobs&filters=workflow_file_name%3Aparent-workflow.yml).

## Interpretation of the higher failure rates

The job `publish_test_data_success` is the final step of the Ubuntu child
workflow that publishes the persistent test-result database
(`TSF/MemoryEfficientTestResultData.db`) back to the `save_historical_data`
branch. The observed 5.26 % failure rate corresponds to 2 failed runs out of
38, and these failures are limited to this publishing step (e.g. git push /
branch / permission issues) rather than to the execution of the tests
themselves.

The job `clone_missing_labels` belongs to the separate “Labeler Workflow” and
synchronizes GitHub issue/PR labels for this repository with the organisation
defaults. Its 2.63 % failure rate corresponds to 1 failed run out of 38,
and is related to repository/label management rather than to building or
testing the JSON library.

## Conclusion

Taken together, a period of there months show that all test-related
jobs in the Parent Workflow have 0 % failures, while the few non-zero
failure rates are confined to meta-jobs that handle publishing of historical
test data and label synchronization. This indicates a stable CI setup for
`inc_nlohmann_json`, with the only reported failures occurring in
infrastructure-side integration steps rather than in the core test pipeline.

