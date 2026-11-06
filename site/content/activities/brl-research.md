---
title: "Video data pipeline for computer vision research (BRL)"
summary: "Preparing labeled video data and running models for lab research"
ShowToc: true
---

**Period:** [확인: 시작 시기] – present · **Status:** In progress
**Type:** Lab research (team) · **My role:** Data preparation and model runs

## Goal {#goal}

Prepare labeled video data for the lab's computer vision research, and help run models on that data.

## What I did {#role}

This is a team project. My part was:

- Extracting frames from videos and preprocessing them
- Labeling objects in the frames with polygons, and helping refine the labeling guidelines for unclear cases
- Running models on the labeled data and organizing the outputs
- Setting up and debugging the environments needed to run them

## Process and why {#process}

I labeled with polygons instead of bounding boxes because many objects in our videos have irregular shapes, and boxes would include too much background.

To save time, I labeled only part of the frames by hand and used a model to fill in the rest.

## Results {#results}

- Labeled frames and model outputs prepared for the lab's experiments
- Small scripts for converting and organizing the data

## What I learned / next {#next}

Getting the same models to run on three different machines (Mac, Windows, Linux server) taught me more about CUDA versions and dependency conflicts than any class did.

While labeling, I saw that small decisions about where an object begins and ends change what the model learns. Next, I want to understand how segmentation models work inside, so I can judge their outputs instead of just running them.
