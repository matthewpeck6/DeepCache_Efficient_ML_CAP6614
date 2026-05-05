Folder containing the code and requirements for the DDIM Model

Unlike caching, which improves diffusion speed by reusing previously computed values, DDIM (Denoising Diffusion Implicit Models) achieve acceleration by requiring fewer computations in the first place rather than storing or reusing intermediate results. As a result, I evaluated generation time using 25 inference steps for consistency with our other acceleration methods, and additionally tested a more aggressive setting with 15 steps.

Results: As expected, using the same number of steps led to minimal speed differences, with SD1.5 + DDIM achieving a 1.04× speedup compared to the baseline. However, reducing to 15 steps increased the speedup to 1.57× while maintaining comparable FID and CLIP scores. A similar pattern was observed with SD2.1, showing a 0.99× speedup at 25 steps (effectively no change) and a 1.56× speedup when reduced to 15 steps.
