---
layout: page
permalink: publications/diffcd/
date: 2024_07_17 # determines sorting just take the date of the first publication as YYYY_MM_DD
image: assets/teaser.png
image_mouseover: assets/header_video.mp4

title: "DiffCD: A Symmetric Differentiable Chamfer Distance for Neural Implicit Surface Fitting"
venue: ECCV, 2024
authors:
  - name: linusnielsen
    affiliation: "1,2"
  - name: lusang
    affiliations: "1,2"
  - name: abhisheksaroha
    affiliations: "1,2"
  - name: nikitaaraslanov
    affiliations: "1,2"
  - name: danielcremers
    affiliations: "1,2"

affiliations:
  - name: tum
    length: short
  - name: mcml
    length: long

description: " We propose a novel loss function corresponding to the symmetric Chamfer distance to address these shortcomings. It assures both that the points are near the surface and that the surface is near the points. Our approach reliably recovers a high level of shape detail and eliminates spurious surfaces without the need for additional regularization. To make our approach more practical, we further propose an efficient method for uniformly sampling point batches from the implicit surface."

links:
    - name: Project Page
      link: publications/diffcd/
    - name: Paper
      link: coming soon
      style: "bi bi-file-earmark-richtext"
    - name: Code
      link: coming soon
      style: "bi bi-github"

citation: "@inproceedings{haerenstam2024diffcd,
 title = {DiffCD: A Symmetric Differentiable Chamfer Distance for Neural Implicit Surface Fitting},
 author = {L Härenstam-Nielsen and L Sang and A Saroha and N Araslanov and D Cremers},
 booktitle = {European Conference on Computer Vision (ECCV)},
 year = {2024},
}"

---

![Teaser Figure](./assets/teaser.png)

***DiffCD.** We propose a novel loss function corresponding to the symmetric Chamfer distance to address these shortcomings. It assures both that the points are near the surface and that the surface is near the points. Our approach reliably recovers a high level of shape detail and eliminates spurious surfaces without the need for additional regularization. To make our approach more practical, we further propose an efficient method for uniformly sampling point batches from the implicit surface.*

# Abstract

Fitting neural implicit surfaces to point clouds is typically done by encouraging the network output to equal zero on the point cloud. Yet, since the underlying shape metric is not symmetric, previous methods are susceptible to spurious surfaces. We theoretically analyze the predominant approach for dealing with spurious surfaces, and show that it is equivalent to regularizing the surface area, leading to over-smoothing. We propose a novel loss function corresponding to the symmetric Chamfer distance to address these shortcomings. It assures both that the points are near the surface and that the surface is near the points. Our approach reliably recovers a high level of shape detail and eliminates spurious surfaces without the need for additional regularization. To make our approach more practical, we further propose an efficient method for uniformly sampling point batches from the implicit surface. 