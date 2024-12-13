# UAWTrack

This repo is the official implementation of "UAWTrack: Universal 3D Single Object Tracking in Adverse Weather".


:star:**Overview**


3D single object tracking (3D SOT) in LiDAR point clouds is essential for autonomous driving. Most existing 3D SOT methods focus on clear weather, where point clouds are more defined. However, adverse weather conditions lead to sparser and noisier point clouds, significantly degrading tracking performance and posing safety risks. In this study, we introduce UAWTrack, a universal 3D SOT model designed to perform effectively across diverse real-world weather conditions. UAWTrack comprises three key modules: 1) Voxel Feature Extraction, which mitigates the perturbations in point clouds caused by adverse weather; 2) Motion-centric Spatial-temporal Aggregation and Motion-guided Feature Fusion, capturing motion clues and sampling dense BEV motion features to address the issue of sparsity; and 3) Weather-Specific Tracker, which efficiently handles tracking in various weather conditions. To fill the gap of lacking benchmarks for 3D SOT in adverse weather, we simulate physically valid adverse weather conditions on the KITTI and NuScenes datasets, creating two benchmarks: KITTI-A and NuScenes-A. Extensive experiments demonstrate that UAWTrack achieves state-of-the-art performance under all weather conditions.


![UAWTrack](figures/pipeline.png)


:scroll:**Datasets**

