---
order: 1
title: "MS-DPT: Multi-Sensor aided Deep Pose Tracking"
excerpt: "A hybrid approach for online object 6D pose estimation"
tagline: "[Hojun Lee](https://scholar.google.com/citations?user=SLpPgLYAAAAJ&hl=en&oi=sra)<sup>1</sup>, [Tyler Toner](https://scholar.google.com/citations?user=NKTX6H4AAAAJ&hl=en)<sup>1</sup>, [Dawn Tilbury](https://scholar.google.com/citations?user=8P0XsUgAAAAJ&hl=en)<sup>1</sup>, [Kira Barton](https://scholar.google.com/citations?user=RXmPJqsAAAAJ&hl=en)<sup>1</sup> <br/> <sup>1</sup> University of Michigan, Ann Arbor" 
header:
  teaser: /assets/images/porfolio/MS-DPT.png
  overlay_image: /assets/images/porfolio/Log2.gif
  overlay_filter: 0.4
gallery:
  - url: /assets/images/porfolio/MS-DPT.png
    image_path: /assets/images/porfolio/MS-DPT.png
    alt: "MS-DPT"
last_modified_at: 2024-06-01T11:59:26-04:00
toc: true
toc_sticky: true
---

{: .text-center}
<a href="https://www.sciencedirect.com/science/article/pii/S2405896322028488" class="btn btn--primary btn--large"><i class="fas fa-file-pdf" style="font-size:36px"></i> Paper</a> &emsp;
<a href="https://drive.google.com/file/d/1LQyA4sq_oKebqDFc3Gnt5M3VG4GPoY-2/preview" class="btn btn--primary btn--large"><i class="fab fa-youtube" style="font-size:36px"></i> MECC Conference</a> &emsp;
<a href="https://github.com/kidpaul94/MS-DPT" class="btn btn--primary btn--large"><i class="fab fa-github" style="font-size:36px"></i> Code</a>

{% include gallery caption="The MS-DPT architecture: The system detects symmetrical objects without any texture using ASUS Xtion Pro
Live on the Human Support Robot (HSR). Masks generated from a CNN with an RGB image are overlaid on a depth image to construct partial point clouds with labels. Each point cloud goes through a registration process to estimate poses of the objects with respect to the robot’s base. These poses are fused with the robot’s odometry to enhance their accuracy." %}

# Introduction
Accurate pose estimation of nearby objects is critical for robots to dynamically interact with their surroundings. The complexity of this task has led researchers to explore deep learning methods. Nowadays, many works have solely focused on developing complicated neural network architectures to estimate pose from a simple monocular camera. <ins>**However, most of these methods struggle with inherent limitations of a single sensor system, like occlusion, which are commonly encountered in mobile robotics applications.**</ins> Online, occlusion-robust pose estimation is extremely important in such cases, as mobility of a robot introduces major uncertainty that complicates manipulation. Hence, we present Multi-Sensor aided Deep Pose Tracking (MS-DPT), a framework for online object pose estimation to enable robust mobile manipulation. 

# Performance of MS-DPT
## Single Camera-based Estimation vs. Fused Estimation (OURS)
{: .text-center}
<p align="center">
<img src="/assets/images/porfolio/Log1.gif" width="45%" height="45%" /> <img src="/assets/images/porfolio/Log2.gif" width="45%" height="45%" />
</p>

In MS-DPT, a Convolutional Neural Network (CNN) identifies key objects in an RGB-D image, from which object pose estimates are generated using a variant of the Iterative Closest Point (ICP) algorithm. An extended Kalman filter is used to fuse this pose estimate with onboard motion sensors to compensate for <font color='blue' style><em>occlusion</em></font> and <font color='blue' style><em>robot motion</em></font> during manipulation. 

## Heavy Occlusion & Robotic Grasping
{: .text-center}
<p align="center">
<img src="/assets/images/porfolio/Log3.gif" width="41.2%" height="41.2%" /> <img src="/assets/images/porfolio/Log4.gif" width="55%" height="55%" />
</p>

This three stage method focuses on <font color='blue' style><em>cohering different modalities</em></font> to improve the pose tracking stability and continuity in cases where the target object becomes heavily occluded by an obstacle or a mobile robot itself. The proposed approach accurately tracks textureless objects with high symmetries while operating at 10 FPS during experiments.

# MECC Conference
<p align="center">
<iframe src="https://drive.google.com/file/d/1LQyA4sq_oKebqDFc3Gnt5M3VG4GPoY-2/preview" width="900" height="600" allow="autoplay"></iframe>
</p>

# Citation

    @article{lee2022multi,
      title={Multi-sensor aided deep pose tracking},
      author={Lee, Hojun and Toner, Tyler and Tilbury, Dawn and Barton, Kira},
      journal={IFAC-PapersOnLine},
      volume={55},
      number={37},
      pages={326--332},
      year={2022},
      publisher={Elsevier}
    }