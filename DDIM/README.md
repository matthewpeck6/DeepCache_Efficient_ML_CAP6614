Folder containing the code and requirements for the DDIM Model

Unlike caching, which improves diffusion speed by reusing previously computed values, DDIM (Denoising Diffusion Implicit Models) achieve acceleration by requiring fewer computations in the first place rather than storing or reusing intermediate results. As a result, I evaluated generation time using 25 inference steps for consistency with our other acceleration methods, and additionally tested a more aggressive setting with 15 steps.

Results: 

| Metric                    | SD1.5 (DDIM=False, 25) | SD1.5 (DDIM=True, 25) | SD1.5 (DDIM=True, 15) | SD2.1 (DDIM=False, 25) | SD2.1 (DDIM=True, 25) | SD2.1 (DDIM=True, 15) |
|---------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
| Avg Time Per Img (s)      | 0.412                  | 0.398                  | 0.263                  | 0.852                  | 0.862                  | 0.547                  |
| Var Time Per Img (s)      | 0.00009                | 0.00010                | 0.00008                | 0.00015                | 0.00013                | 0.00012                |
| Std Time Per Img (s)      | 0.010                  | 0.010                  | 0.009                  | 0.012                  | 0.012                  | 0.011                  |
| VRAM (GB)                 | 19.05                  | 19.05                  | 19.05                  | 35.93                  | 35.93                  | 35.93                  |
| FID                       | 52.510                 | 52.749                 | 53.970                 | 52.756                 | 52.756                 | 52.830                 |
| CLIP                      | 0.145                  | 0.146                  | 0.146                  | 0.146                  | 0.146                  | 0.147                  |
| Throughput (img/s)        | 2.427                  | 2.515                  | 3.795                  | 1.174                  | 1.159                  | 1.828                  |

As expected, using the same number of steps led to minimal speed differences, with SD1.5 + DDIM achieving a 1.04× speedup compared to the baseline. However, reducing to 15 steps increased the speedup to 1.57× while maintaining comparable FID and CLIP scores. A similar pattern was observed with SD2.1, showing a 0.99× speedup at 25 steps (effectively no change) and a 1.56× speedup when reduced to 15 steps.
