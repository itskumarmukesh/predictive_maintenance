# Predictive Maintenance: Remaining Useful Life Prediction for Turbofan Engines

## Problem statement
Aircraft engines degrade gradually, but the wear is buried in noisy sensor
readings that also change with how the engine is being flown. A maintenance
team must decide when to pull an engine from service: too early wastes usable
life and money, too late risks an in-service failure.

This project builds a reproducible prognostics pipeline that, given the sensor
and operating-condition history of an engine up to its current flight cycle,
estimates its Remaining Useful Life (RUL), the number of cycles left before
failure, and flags engines likely to fail within a chosen warning window. The
goal is to let maintenance be scheduled before failure while wasting as little
remaining life as possible.

## Tasks
1. Primary: RUL regression (predict remaining cycles for each engine)
2. Secondary: failure-warning classification ("will this engine fail within the next N cycles?")
3. Extensions: degradation analysis, prediction uncertainty, drift monitoring,
   harder subsets (FD002-FD004) and a second dataset

## Data
NASA C-MAPSS turbofan simulation (FD001-FD004). See data/README.md. This is
simulated data, so results show the method works, not that it is production-ready.

## Success criteria (fixed before any modeling)
- Metrics: RMSE, MAE and the NASA asymmetric score (late predictions penalized more)
- Official test protocol: one prediction per test engine, at its last recorded
  cycle, compared with the provided true RUL
- Validation: split by engine ID, never by row; test set used only for final reporting
- Every model must beat simple baselines to count as progress
- Fixed random seeds, pinned requirements.txt, results regenerable from raw data
- Limitations and failure cases documented

## Status
Phase 0 (setup) complete. Phase 1 (data validation) in progress.