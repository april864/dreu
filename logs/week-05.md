# Week 5

**Dates:** 07-13 to 07-17

## Goals
- Start calibration and cycle benchmarking data processing
- Understand DEM learning in more detail (implement from Blume-Kohout and Young's paper)
- Refactor to use CUDA-Q


## Approach and Implementation
- Monday: looked over full pipeline, outlined what still needs to be implemented. Worked on calibration and cycle benchmarking data processing
- Tuesday: Wrote tests for batch syndrome processing. Met with mentor and decided to take more time to read DEM learning papers.
- Wednesday: Continued reading papers, went over pipeline with grad student. 
- Thursday: Finished reading and looked into noise models. Current implementation uses a circuit-level noise model; might change to code capacity noise model. Also analyzed rotated surface codes with distance 3, 5, and 7, and single-qubit Z errors to identify distinguishable vs indistinguishable errors.
- Friday: Verified Thursday's analysis of distinguishable vs. indistinguishable errors. Tested learnability of these errors.


## Results
- Looks like CUDA-Q can generate syndrome histories and DEM from circuit, but not learn DEMs from syndrome history.
- Current implementation uses lsq_linear solver to learn attenuations, instead of algorithms from Bluem-Kohout and Young's paper. This might not scale as well.
- Computational verification and learning test of distance 3, 5, 7 surface codes with single-qubit Z errors matched the expected results from analysis.


## Notes
Implementation todos:
- The current code should take in calibration data and obtain the initial attenuations with weighted least squares and regularized near-zero parities
- Simulate cycle benchmarking data and process it with a circuit map (CUDA-Q?)
- Fuse calibration and cycle benchmarking data to obtain initial posterior
- Generate syndrome measurement data with hardware drift to simulate running and measuring a circuit
- Update attenuations at each time step in the circuit
- Obtain decoder confidence (start with MWPM, implement BP later)
- Record decoder corrections, confidences, and true logical outcomes (from stim)
- Output validation data