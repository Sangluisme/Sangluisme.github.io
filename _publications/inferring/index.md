---
layout: page
permalink: publications/inferring/
date: 2020_01_29 # determines sorting just take the date of the first publication as YYYY_MM_DD
image: assets/teaser.png
image_mouseover: assets/sang2020wacv_video.mp4

title: "Inferring Super-Resolution Depth from a Moving Light-Source Enhanced RGB-D Sensor: A Variational Approach"
venue: WACV, 2020
authors:
  - name: lusang
  - name: bjoernhaefner
  - name: danielcremers
  
affiliations:
  - name: tum
    length: long

description: "A novel approach towards depth map super-resolution using multi-view uncalibrated photometric stereo is presented. Practically, an LED light source is attached to a commodity RGB-D sensor and is used to capture objects
from multiple viewpoints with unknown motion. This nonstatic camera-to-object setup is described with a nonconvex variational approach such that no calibration on lighting or camera motion is required due to the formulation of an end-to-end joint optimization problem. Solving the proposed variational model results in high resolution depth, reflectance and camera pose estimates, as we show on challenging synthetic and real-world datasets."

links:
    - name: Project Page
      link: publications/inferring/
    - name: Paper
      link: https://cvg.cit.tum.de/_media/spezial/bib/sang2020wacv.pdf
      style: "bi bi-file-earmark-richtext"
    - name: Code
      link: https://github.com/Sangluisme/MultiviewLightEnhancedDepthSR
      style: "bi bi-github"
    - name: Video
      link: publications/inferring/assets/sang2020wacv_video.mp4
      style: "bi bi-youtube"

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
 award = {Spotlight Presentation},
 titleurl = {sang2020wacv.pdf},
 keywords = {3d-reconstruction,rgb-d,photometry},
}"

# citation: "@{ASDF}"
---