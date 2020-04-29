# DynamicFusion: Reconstruction and tracking of non-rigid scenes in real-time
Cited by 515

## Category
A new method for 3D reconstruction
* **NOT ONLY** for rigid scenes
* but target also for **DYNAMIC, UNRIGID** scenes

## Context
Related to Kinect.
* This paper was written in 2015. Reminds me of the Kinect camera..
* Much matrix calculations. Basically about warping (mapping) to the first scenes, then re-applying (inverse matrix) to map the more complete reconstruction to live video frame.

## Correctness
They seem to be correct, at least mathematically.
* This is how they approached problems before the Deep Learning era.
* Makes me think I should have an even stronger mathematical foundation.
  * Should look at many pre-deeplearning papers for theoretical catchup

# Contributions

1. Generalize optimality results (of volumetric scan fusion) for non-rigit case
2. Represent volumetric warp efficiently
* Would normally take over 100 mil transformation variables computed at frame rate
  ( 256^3, where 256 is the resolution 256*256*256)
* Depends on adaptive, sparse, hierarchial volumetric basis functions + innovative algorithm

First system capable of real-time dense reconstruction in dynamic scenes using a SINGLE depth camera
