---
layout: distill
title: BRDF Reconstruction with RGBD camera
description: High-Quality RGB-D Reconstruction via Multi-View Uncalibrated Photometric Stereo and Gradient-SDF
img: assets/img/publication_preview/high_rgbd.png
importance: 1
category: work
giscus_comments: false
featured: true

authors:
  - name: Lu Sang
    url: "https://sangluisme.github.io"
    affiliations:
      name: TUM, MCML
  - name: Bjoern Haefner
    url: "https://cvg.cit.tum.de/members/haefner"
    affiliations:
      name: TUM, MCML
  - name: Xingxing Zuo
    url: "https://xingxingzuo.github.io/"
    affiliations:
      name: TUM
  - name: Daniel Cremers
    url: "https://cvg.cit.tum.de/members/cremers"
    affiliations:
      name: TUM, MCML

# bibliography: 2018-12-22-distill.bib

toc:
  - name: Abstract
    # if a section has subsections, you can add them as follows:
    # subsections:
    #   - name: Example Child Subsection 1
    #   - name: Example Child Subsection 2
  - name: Overview
  - name: Voxel center vs. Surface point
  - name: Natural Lighting Model
  - name: Point light Source Model
  - name: Results
  - name: Citation

---
<div class="link-block">
  <a href=" https://arxiv.org/abs/2210.12202" target="_blank" class="icon-link">
    <img src="https://img.icons8.com/ios-filled/50/000000/document.png" alt="Paper" width="20">
    Paper
  </a>
  
  <a href="https://github.com/Sangluisme/PSgradientSDF" target="_blank" class="icon-link">
    <img src="https://img.icons8.com/ios-filled/50/000000/github.png" alt="Code" width="20">
    Code
  </a>

  <a href="/assets/img/high_rgbd/1332-wacv.mp4" target="_blank" class="icon-link">
    <img src="https://img.icons8.com/ios-filled/50/000000/video.png" alt="Video" width="20">
    Video
  </a>
</div>

<style>
  .link-block {
    display: flex;
    gap: 15px;
    margin-top: 20px;
  }

  .icon-link {
    display: flex;
    align-items: center;
    text-decoration: none;
    font-size: 16px;
  }

  .icon-link img {
    margin-right: 5px;
  }
</style>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/high_rgbd/teaser.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>High-Quality RGBD Reconstruction</strong>. We propose a novel multi-view RGB-D based reconstruction method that tackles camera pose, lighting, albedo, and surface normal estimation via the utilization of a gradient signed distance field (gradient-SDF). It formulates the image rendering process using specific physically-based model(s) and optimizes the surface's quantities on the actual surface using its volumetric representation.
</div>

## Abstract

Fine-detailed reconstructions are in high demand in many applications. However, most of the existing RGB-D reconstruction methods rely on pre-calculated accurate camera poses to recover the detailed surface geometry, where the representation of a surface needs to be adapted when optimizing different quantities. In this paper, we present a novel multi-view RGB-D based reconstruction method that tackles camera pose, lighting, albedo, and surface normal estimation via the utilization of a gradient signed distance field (gradient-SDF). The proposed method formulates the image rendering process using specific physically-based model(s) and optimizes the surface's quantities on the actual surface using its volumetric representation, as opposed to other works which estimate surface quantities only near the actual surface. To validate our method, we investigate two physically-based image formation models for natural light and point light source applications. The experimental results on synthetic and real-world datasets demonstrate that the proposed method can recover high-quality geometry of the surface more faithfully than the state-of-the-art and further improves the accuracy of estimated camera poses.

## Overview

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/high_rgbd/pipeline.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

a) We propose a novel formulation of physically realistic image model(s) compatible with a volumetric representation which enables effective optimization on actual surface points.

b) It completes reconstruction pipeline with the capability of camera pose, geometry refinement, albedo and lighting estimation.

c) It is a method that deals with natural and point light source scenarios in an uncalibrated setting which are convenient to adopt in real applications.

## Voxel center vs. Surface point

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/high_rgbd/voxel_center.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The key idea of the proposed method is describing the explicit surface under an implicit representation, i.e., under a volumetric cube. To perform all the operations on the actual surface, we must find the corresponding surface point to each voxel. To combine the advantage of surface point representation with volumetric representation, gradient-SDF stores the signed distance $\psi^j$ for each voxel $\boldsymbol{v}^j$ for $j\in\mathcal{V}$, together with the distance gradient $\boldsymbol{g}^j$ of this voxel. It allows us to easily compute the surface point $\boldsymbol{x}^j$ by moving along the gradient direction $\boldsymbol{g}^j$ with the voxel distance $\psi^j$ 

$$
 \boldsymbol{x}^j = \boldsymbol{v}^j - \boldsymbol{g}^j\psi^j
$$

## Natural Lighting Model

A *natural light* source situation is, for example, the light source is the sun, or when the light sources are in a distance. The lighting directions that reach the surface are nearly parallel, then the environment lighting can be well modeled using Spherical Harmonics (SH) functions. The integral part is approximated by the sum of SH basis.

$$
   \boldsymbol{I}(\boldsymbol{p}(\boldsymbol{x})) \approx \boldsymbol{P}(\boldsymbol{x})<\boldsymbol{l}, \boldsymbol{SH}(\boldsymbol{n}(\boldsymbol{x}))>\,,
$$

where $\boldsymbol{l} \in \mathbb{R}^4$ is an 4-dimensional lighting vector for the current view and $\boldsymbol{SH}(\boldsymbol{n}(\boldsymbol{x}))\in \mathbb{R}^4$ are the first-order SH basis functions for a fixed $\boldsymbol{n}(\boldsymbol{x})$. 
The model is simply formulated and still can reach relatively high accuracy with a low order model. 

## Point light Source Model

Apart from the natural light, another commonly encountered scenario is the point light source situation, mainly when focusing on small object reconstruction. The object is usually illuminated by a *point light source*, e.g., a LED light that is close to the object. The lighting can hardly be regarded as a set of parallel lines, thus point light source provides more changes to the object illumination, which is preferred to deal with the ill-posedness of the PS model. One widely used point light source-light model is:

$$
    \boldsymbol{I}(\boldsymbol{p}(\boldsymbol{x})) = \Psi^s \boldsymbol{P}(\boldsymbol{x}) (\frac{<\boldsymbol{n}^s,\boldsymbol{l}^s>}{||\boldsymbol{l}^s||})^{\mu^s} \frac{\max(<\boldsymbol{n}(\boldsymbol{x}),\boldsymbol{l}^s>, 0)}{||\boldsymbol{l}^s||^3}\,,
$$

where $\Psi^s$ is the light source intensity, $\boldsymbol{n}^s$ is the principal direction of the light source, and $\boldsymbol{l}^{s}$ is the vector pointing from the light location to the surface point. The denominator term $\lVert\boldsymbol{l}^{s}\rVert^3$ describes the attenuation of the light intensity when it reaches the surface point. $\mu^s \geq 0$ is the anisotropy parameter.

## Results

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/high_rgbd/reconstruction.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
<strong>Reconstruction results</storng> Reconstrution results compare with other methods under Natural light conditions.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/high_rgbd/point_light.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<strong>Reconstruction results</storng> Reconstrution results under point light source conditions, uncalibrated.
</div>



## bibtex citation
{% highlight javascript %}
    @inproceedings{sang2023high,
    author = {L Sang and B Haefner and X Zuo and D Cremers},
    title = {High-Quality RGB-D Reconstruction via Multi-View Uncalibrated Photometric Stereo and Gradient-SDF},
    booktitle = {IEEE Winter Conference on Applications of Computer Vision (WACV)},
    month = {January},
    address = {Hawaii, USA},
    year = {2023},
    eprint = {2210.12202},
    eprinttype = {arXiv},
    eprintclass = {cs.CV},
    copyright = {Creative Commons Attribution Non Commercial No Derivatives 4.0 International},
    titleurl = {sang2023high.png},
    award = {Spotlight Presentation},
    keywords = {3d-reconstruction,rgb-d,photometry},
    }
 {% endhighlight %}