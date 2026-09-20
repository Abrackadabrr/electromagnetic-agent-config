# Skill-routing evaluation prompts

These are maintenance tests for skill descriptions. They are not instructions
that consuming agents must read.

| Prompt | Expected skills |
| --- | --- |
| “Why does my sign before R differ from Gibson?” | electromagnetics-notation |
| “Convert this formula from exp(+i wt) to our convention.” | electromagnetics-notation |
| “Derive the PEC EFIE in the project K/R notation.” | surface-integral-equations; electromagnetics-notation if translation is needed |
| “Implement RWG matrix elements for a singular triangle pair.” | operator-discretization; surface-integral-equations |
| “What is the difference between E-VIE, J-VIE and D-VIE?” | volume-integral-equations |
| “Build a PEC-surface + dielectric-volume block formulation.” | volume-integral-equations |
| “Why is the voxel Green block Toeplitz on a regular grid?” | uniform-grid-vie |
| “Why does a periodic array give repeated/block-Toeplitz interaction blocks?” | structured-em-operators |
| “Should distant EM interaction blocks be low rank?” | structured-em-operators |
| “Implement a generic 3-level Toeplitz FFT matvec.” | no EM skill required; use NLA skills |
| “Optimize DGEMM cache blocking.” | no EM skill required |
| “Explain the spectral theorem for compact operators.” | no automatic EM skill required |
