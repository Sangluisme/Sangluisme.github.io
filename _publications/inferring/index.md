---
layout: page
permalink: publications/inferring/
date: 2022_05_29 # determines sorting just take the date of the first publication as YYYY_MM_DD
image: assets/teaser.png
image_mouseover: assets/sang2020wacv_video.mp4

title: "Gradient-SDF: A Semi-Implicit Surface Representation for 3D Reconstruction"
venue: CVPR, 2022
authors:
  - name: lusang
  - name: bjoernhaefner
  - name: danielcremers
  
affiliations:
  - name: tum
    length: long

description: "A novel representation for 3D geometry that combines the advantages of implict and explicit representations. By storing at every voxel both the signed distance field as well as its gradient vector field, we enhance the capability of implicit representations with approaches originally formulated for explicit surfaces."

links:
    - name: Project Page
      link: publications/inferring/
    - name: Paper
      link: https://cvg.cit.tum.de/_media/spezial/bib/sang2020wacv.pdf
      style: "bi bi-file-earmark-richtext"
    - name: Code
      link: https://github.com/Sangluisme/MultiviewLightEnhancedDepthSR
      style: "bi bi-github"


citation: "@inproceedings{sang2020wacv,
 title = {Inferring Super-Resolution Depth from a Moving Light-Source Enhanced RGB-D Sensor: A Variational Approach},
 author = {L. Sang and B. Haefner and D. Cremers},
 booktitle = {IEEE Winter Conference on Applications of Computer Vision (WACV)},
 month = {March},
 address = {Colorado, USA},
 year = {2020},
 doi = {10.1109/WACV45572.2020.9093491},
 eprint = {1912.06501},
 eprinttype = {arXiv},
 eprintclass = {cs.CV},
}"

# citation: "@{ASDF}"
---