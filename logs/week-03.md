# Week 3

**Dates:** 06-29 to 07-03

## Goals

- Finish conceptual summary
- Implement syndrome measurement portions of the code

## Approach and Implementation

On Monday, I fixed a NumPy type converting bug and used the Stim package to generate data for testing with an MWPM decoder, which I added and tested on Tuesday. On Wednesday, I finished the conceptual summary. I then spent the rest of the week writing tests and running experiments with a simple surface code.

## Results

- Incorporated Stim for data generation
- Added MWPM decoder
- Completed conceptual summary
- Repetition code test: our pipeline does better at correcting errors than a uniform baseline and a simulation with true values
- Surface code test: reasonably accurate prediction of injected error probabilities. More training shots also lowers logical error rate, as expected.

## Notes

- Tested with distance-3 repetition code and distance-3 surface code---try more varied or complex codes sometime?
- Careful with integer types and parity polarization
- Aggregated different faults with same detector support before constructing MWPM graph
- Used scipy.optimize.nnls instead of np.linalg.lstsq to obtain attenuation, in order to restrict to positive values