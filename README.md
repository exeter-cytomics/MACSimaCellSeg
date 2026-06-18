## Maintained By

**[Sebastiano Montante, PhD](https://github.com/semontante)**  
📧 Email: [s.montante@exeter.ac.uk](mailto:s.montante@exeter.ac.uk)

---

# MACSimaCellSeg

**Automatic cell segmentation workflows for MACSima multiplex microscopy images**


---

# Project Overview

MACSimaCellSeg is a research and development repository focused on automatic nuclear and whole-cell segmentation of MACSima multiplex microscopy images.

The project initially focuses on benchmarking existing segmentation tools such as **Cellpose-SAM**, **InstanSeg**, and **Mesmer/DeepCell**, using reproducible Docker environments and Jupyter notebooks.

The longer-term goal of this repository is to support the development of improved segmentation workflows and future fine-tuned or modified segmentation models adapted specifically to MACSima image data.

Multiplex microscopy platforms such as MACSima generate high-dimensional image data, where each region of interest can contain many marker channels acquired across multiple imaging cycles. These data provide rich biological information but also create important computational challenges for image analysis.

A key challenge is **automatic cell segmentation**, where the goal is to identify individual cells and assign image pixels to biologically meaningful objects. In this project, we distinguish between two related segmentation tasks:

- **Nuclear segmentation**, usually based on DAPI signal.
- **Whole-cell or cytoplasmic segmentation**, which is more challenging and may require membrane, cytoplasmic, or combined marker information.

Nuclear segmentation is often more straightforward because DAPI provides a strong signal for nuclei. Whole-cell segmentation is more difficult because cell boundaries can be faint, irregular, overlapping, or marker-dependent.

This repository aims to evaluate existing segmentation tools, compare their performance on MACSima images, and provide a reproducible foundation for future algorithm development.

---

# Current Goals

The current goals of this repository are:

1. Test **Cellpose-SAM** on MACSima image channels.
2. Test **InstanSeg** on multiplex microscopy data.
3. Test **Mesmer/DeepCell** as a whole-cell segmentation baseline.
4. Compare nuclear and whole-cell segmentation quality across methods.
5. Benchmark execution time on CPU and GPU environments.
6. Provide Dockerized environments for reproducible analysis.
7. Develop clear Jupyter notebooks for testing, visualization, and documentation.
8. Explore future fine-tuning or modification of Cellpose-style models for MACSima-specific segmentation.

---

# Long-Term Aim

The long-term aim is to move beyond benchmarking and toward method improvement.

In future stages, this repository may include:

- Fine-tuned segmentation models trained on MACSima images.
- Modified Cellpose-style workflows adapted to multiplex microscopy.
- Improved strategies for combining many marker channels.
- Automated preprocessing pipelines.
- Quantitative segmentation quality metrics.
- Reproducible benchmarking datasets and reports.

At the current stage, any future modified Cellpose-based method should be considered experimental research software rather than a finalized tool.

---

# Tools and Algorithms

This repository is designed to test and compare multiple segmentation approaches.

## Cellpose-SAM

Cellpose-SAM is used as an initial segmentation baseline. Current tests include DAPI-only segmentation, selected marker-channel segmentation, and combined DAPI + marker inputs.

A key practical observation is that Cellpose-SAM no longer uses the old Cellpose `channels=[...]` logic in the same way. Instead, Cellpose-SAM uses the first three channels of the input image and is trained to be invariant to channel order. Therefore, for MACSima images with many marker channels, the input image must be explicitly constructed before running the model.

## InstanSeg

InstanSeg is included because it is designed to support multiplexed image data and may be more suitable for images with many marker channels.

## Mesmer / DeepCell

Mesmer is included as a comparison method for nuclear and whole-cell segmentation, especially where paired nuclear and membrane/cytoplasmic channels are available.

