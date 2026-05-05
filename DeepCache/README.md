Folder containing the code and requirements to re-create the metrics in the DeepCache Paper

Achieves 2.3x speedup on Stable
Diffusion v1.5 with only 0.05 CLIP Score decrease, and 4.1x speedup on LDM-4 (ImageNet) with 0.22
FID increase -- all without any training or fine-tuning.

Hardware: Tested on Google Colab A100 GPUs.=

Dataset: COCO val2017 (1000 images) Metrics: FID, CLIP Score, mean inference time, speedup ratio Steps: 25 DDIM steps Batch size: 8

Results:

Model	Speedup	FID ↑	CLIP Δ
SD1.5	2.63×	-0.841	0.0033
SD2.1	2.86×	12.167	0.0075

Model Name, Cache Setting	Total Time	Mean Time	Variance Time	STD Time	Peak VRAM	FID Score	CLIP Score	Throughput	UNet MACs
SD1.5, Cache=False	43 mins 52 secs	0.4216 seconds	0.000003 seconds	0.001776 s	18.608 GB	25.330	0.1419	1.90 img/s	169.51 GMACs
SD1.5, Cache=True	23 mins 44 secs	0.1774 seconds	0.000041 seconds	0.006391 s	21.978 GB	24.489	0.1452	3.51 imgs/s	169.51 GMACs
SD2.1, Cache=False	38 min 55 secs	0.3568 seconds	0.000002 seconds	0.001226 s	18.455 GB	29.861	0.1479	2.14 img/s	169.75 GMACs
SD2.1, Cache=True	20 mins 23 secs	0.1326 seconds	0.000008 seconds	0.002817 s	21.825 GB	42.028	0.1554	4.09 img/s	169.75 GMACs
