# Lab 6 – Code and Branch Coverage Analysis
## Traffic Fine Calculator

**Course:** Software Engineering  
**Lab:** 6 – Code and Branch Coverage Analysis  
**Application:** Traffic Fine Calculator

## Objective
Measure and improve test completeness using line coverage and branch coverage. The tests exercise the speeding fine calculation, driving-licence action rules, and total-penalty calculation.

## Project structure

```text
L6_L7_27_traffic_fine/
└── lab6/
    ├── traffic_fine.py
    ├── test_traffic_fine.py
    ├── CodeCoverageTest_traffic_fine.py
    ├── BranchCoverageTest_traffic_fine.py
    ├── README.md
    └── evidence/
        └── coverage-results.md
```

## Application functions

- `speeding_fine(speed, limit, zone)`: calculates a fine using the speed excess and road zone.
- `license_action(points, is_commercial, repeat_offender)`: returns the applicable licence action.
- `total_penalty(fines)`: totals fines, rejects negative values, and caps the total at ₹10,000.

## Requirements

- Python 3.x
- pytest
- coverage.py

Install dependencies from this directory:

```powershell
py -m pip install pytest coverage
```

## 1. Line coverage

```powershell
py -m coverage erase
py -m coverage run -m pytest -q CodeCoverageTest_traffic_fine.py
py -m coverage report -m traffic_fine.py
```

**Verified result:** 15 tests passed; 35 statements, 0 missed; 100% line coverage.

## 2. Branch coverage

```powershell
py -m coverage erase
py -m coverage run --branch -m pytest -q BranchCoverageTest_traffic_fine.py
py -m coverage report -m traffic_fine.py
```

**Verified result:** 20 tests passed; 35 statements, 0 missed; 26 branches, 0 partial; 100% branch coverage.

## Test coverage focus

- Speed at/below the limit and above the limit.
- School, highway, and other road zones.
- Speed excess thresholds (>20 and >40), including boundary values.
- Licence point thresholds (<4, 4–7, 8–11, and 12+).
- Commercial and non-commercial licence outcomes.
- Repeat and first-time offenders.
- Normal, negative, at-cap, and over-cap penalty totals.

## Evidence

See [evidence/coverage-results.md](evidence/coverage-results.md) for the captured terminal commands and readable output summaries.

## Commits

The line-coverage and branch-coverage test files are maintained as separate commits, as required by the lab handout.
