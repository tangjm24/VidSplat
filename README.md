# VidSplat: Gaussian Splatting Reconstruction with Geometry-Guided Video Diffusion Priors

### [Project Page](https://tangjm24.github.io/VidSplat) | [Paper (ArXiv)](https://arxiv.org/abs/xxxx.xxxxx) | [Video](https://youtu.be/xxxx)

> **VidSplat: Gaussian Splatting Reconstruction with Geometry-Guided Video Diffusion Priors**
>
> *Anonymous Authors*
>
> **ACM SIGGRAPH 2026 Conference Paper**

<p align="center">
  <img src="assets/teaser.png" width="100%">
</p>

We highlight the strength of **VidSplat** in large-scale scene reconstruction and novel view synthesis using only 5 input views (top), where recent sparse-view reconstruction methods fail to recover reasonable surfaces. We also demonstrate our ability to generate a complete scene from a single input image, either with all-around coverage (bottom-left) or outward-expanding completion (bottom-right).

## Abstract

Gaussian Splatting has achieved remarkable progress in multi-view surface reconstruction, yet it exhibits notable degradation when only few views are available. Although recent efforts alleviate this issue by enhancing multi-view consistency to produce plausible surfaces, they struggle to infer unseen, occluded, or weakly constrained regions beyond the input coverage. To address this limitation, we present **VidSplat**, a training-free generative reconstruction framework that leverages powerful video diffusion priors to iteratively synthesize novel views that compensate for missing input coverage, and thereby recover complete 3D scenes from sparse inputs. Specifically, we tackle two key challenges that enable the effective integration of generation and reconstruction. First, for 3D consistent generation, we elaborate a training-free, stage-wise denoising strategy that adaptively guides the denoising direction toward the underlying geometry using the rendered RGB and mask images. Second, to enhance the reconstruction, we develop an iterative mechanism that samples camera trajectories, explores unobserved regions, synthesizes novel views, and supplements training through confidence weighted refinement. VidSplat performs robustly to sparse input and even a single image. Extensive experiments on widely used benchmarks demonstrate our superior performance in sparse-view scene reconstruction.

## Method Overview

<p align="center">
  <img src="assets/method_overview.png" width="100%">
</p>

Given sparse input views, we sample novel camera trajectories and employ a camera-controlled video diffusion model (VDM) with our geometry-guided denoising strategy to generate additional views. In the initialization stage, RGB and mask images rendered from point cloud are used as VDM inputs, and the generated views are used to complete the initial point cloud. In the training stage, Gaussian-rendered RGBs and mesh-rendered masks are used as inputs, and the generated views are used to expand the training view set.

## Code

> **Code coming soon!** We are cleaning up the codebase and will release it shortly. Stay tuned!

## Results

### Surface Reconstruction on TanksAndTemples

<p align="center">
  <img src="assets/results_tnt.png" width="100%">
</p>

### Surface Reconstruction on Replica

<p align="center">
  <img src="assets/results_replica.png" width="100%">
</p>

Quantitative comparisons on Replica and TanksAndTemples datasets:

| Method | TNT CD↓ | TNT F-Score↑ | Replica CD↓ | Replica NC↑ | Replica F-Score↑ |
|---|---|---|---|---|---|
| FSGS | 0.93 | 3.00 | 0.12 | 67.36 | 39.46 |
| FatesGS | 1.04 | 1.68 | 0.74 | 52.47 | 3.47 |
| PGSR | 0.92 | 2.61 | 0.59 | 55.01 | 17.76 |
| Sparse2DGS | 1.35 | 0.49 | 0.82 | 49.64 | 2.83 |
| DIFIX3D+ | 0.82 | 0.21 | 0.70 | 51.11 | 4.77 |
| GuidedVD | 0.81 | 2.91 | 0.12 | 67.91 | 40.45 |
| MAtCha | 0.84 | 6.47 | 0.08 | 83.18 | 71.77 |
| QGS | 0.93 | 2.72 | 0.23 | 60.73 | 28.66 |
| **Ours** | **0.66** | **12.80** | **0.06** | **88.42** | **80.79** |

### Novel View Synthesis on DL3DV

<p align="center">
  <img src="assets/results_dl3dv.png" width="100%">
</p>

| Method | Indoor PSNR↑ | Indoor SSIM↑ | Indoor LPIPS↓ | Outdoor PSNR↑ | Outdoor SSIM↑ | Outdoor LPIPS↓ |
|---|---|---|---|---|---|---|
| FSGS | 16.30 | 0.622 | 0.411 | 15.56 | 0.507 | 0.435 |
| FatesGS | 14.07 | 0.505 | 0.454 | 13.81 | 0.412 | 0.444 |
| PGSR | 16.31 | 0.616 | 0.386 | 15.61 | 0.544 | 0.426 |
| Sparse2DGS | 12.96 | 0.276 | 0.535 | 13.12 | 0.260 | 0.593 |
| DIFIX3D+ | 16.36 | 0.549 | 0.391 | 14.66 | 0.422 | 0.419 |
| GuidedVD | 17.87 | 0.649 | 0.387 | 17.02 | 0.516 | 0.430 |
| MAtCha | 16.83 | 0.598 | 0.326 | 15.23 | 0.453 | 0.384 |
| QGS | 16.73 | 0.599 | 0.359 | 15.35 | 0.526 | 0.387 |
| **Ours** | **19.78** | **0.699** | **0.292** | **17.49** | **0.561** | **0.376** |

### Single-View Reconstruction

<p align="center">
  <img src="assets/singleview_recon.png" width="100%">
</p>

## BibTeX

If you find this work useful, please consider citing:

```bibtex
@article{vidsplat2026,
  title={VidSplat: Gaussian Splatting Reconstruction with Geometry-Guided Video Diffusion Priors},
  author={Anonymous},
  booktitle={ACM SIGGRAPH 2026 Conference Proceedings},
  year={2026},
  publisher={ACM}
}
```

## Acknowledgements

Our code is built upon [2DGS](https://github.com/hbb1/2d-gaussian-splatting), [MAtCha](https://github.com/amandinesandwormatcha/matcha-gaussian-splatting), [DUSt3R](https://github.com/naver/dust3r), and [Wan2.1](https://github.com/Wan-Video/Wan2.1). We thank the authors for their excellent work.

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.
