# Week 6

**Dates:** 07-20 to 07-24

## Goals
- Implement continous runtime syndrome update


## Approach and Implementation
- Refactored existing pipeline to estimate attenuations at calibration-time
- Wrote test to generate surface code circuits with two different error rates, compute attenuations from first set of detector measurements, and update attenuations with second set of measurements
- Implemented weighted least squares to learn attenuations (was previously using ordinary least squares)


## Results
- Implemented Gaussian information update math
- Currently using closed-form equations to update; could use constrained quadratic minimization if needed


## Notes
Things to keep in mind: 
- Set up GitHub repo 
- Use CUDA-Q



