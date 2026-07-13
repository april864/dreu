# Week 4

**Dates:** 07-06 to 07-10

## Goals
- Finish same-syndrome local ambiguity test
- Learn theory to implement prior library and continuous decoding


## Approach and Implementation
The same-syndrome test wasn't working because of some edge cases with a couple of helper functions, which I ended up rewriting. More specifically, I changed how graphs were built for MWPM decoding and how syndromes were aggregated over logical masks. Regarding theory, I learned about cycle benchmarking and streaming runtime updates for this project. I also read through validation methodology for future experiments and gained a more thorough understanding of the rest of the project pipeline.


## Results
- Fixed same-syndrome test
- Rewrote and refactored helper functions: build_custom_matching, export_mwpm_weights, and get_full_mwpm_weights
- Updated tests
- Learned theory


## Notes
- Missed Monday and some of Tuesday due to illness
- Should set up GitHub repo for version control
- Need to check old scripts to confirm functionality with new functions
- Should check aggregation logic
- GPU implementation?


