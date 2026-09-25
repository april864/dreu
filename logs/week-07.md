# Week 7

**Dates:** 07-27 to 07-31

## Goals
- Test continous runtime syndrome update
- Integrate MWPM decoder

## Approach and Implementation
- Wrote a script that generates data from a distance-3 surface code, runs the calibration-time estimator, and obtains initial attenuation estimates. It then simulates hardware drift by changing the error probability when generating data, and then obtains several additional ‘windows’ of detector data. The attenuations are updated as each window’s data is produced using the runtime update math implemented last week. 
- Tested calibration-time prior estimation followed by runtime syndrome updates and decoding over several windows of a distance 3 surface code. Compared results with those from only using the calibration-time prior estimation. Also obtained results from a DEM without duplicate supports and one with an injected duplicate.
- Conducted tests using both a code capacity and circuit level noise model with p=0.005
- Cleaned and refactored codebase in anticipation of leaving for August


## Results
- Estimated probabilities increase as hardware drifts: pipeline is correctly updating estimates to follow true error probabilities
- Without duplicate support, using runtime syndrome data marginally improved logical error rate
- With duplicate support, logical error rate was worse when runtime syndrome data was used, maybe due to how decoder graph chooses which logical mask to use
- d=5 took much longer than d=3; impractical
- The code capacity noise test showed that learned weights vary in their accuracy, with a mean average error of 0.08127. The circuit level noise test produced events with duplicate supports, which seem to be the points at the top of the graph. The mean average error was 1.66013, and the logical mask error rate, or the rate at which the decoder uses the wrong logical mask, was 3.2%.

## Notes
- Simulation does not natively produce events with duplicate supports
- Wrote a temporary placeholder function to convert from the aggregated attenuations learned during calibration to the fine-class attenuations used in runtime updating assuming no cycle benchmarking data
- Updated attenuations restricted to nonnegative values temporarily by removing negative values, but this eventually will use constrained quadratic minimization
- There doesn’t seem to be a simple way to implement the SI1000 noise model in stim, so the circuit level noise model I used is just a simple depolarizing one in stim. CUDA-Q may have better support for the SI1000 noise model. 
