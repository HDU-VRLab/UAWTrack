# UAWTrack

This repo is the official implementation of "UAWTrack: Universal 3D Single Object Tracking in Adverse Weather".


## :star:Overview


3D single object tracking (3D SOT) in LiDAR point clouds is essential for autonomous driving. Most existing 3D SOT methods focus on clear weather, where point clouds are more defined. However, adverse weather conditions lead to sparser and noisier point clouds, significantly degrading tracking performance and posing safety risks. In this study, we introduce UAWTrack, a universal 3D SOT model designed to perform effectively across diverse real-world weather conditions. UAWTrack comprises three key modules: 1) Voxel Feature Extraction, which mitigates the perturbations in point clouds caused by adverse weather; 2) Motion-centric Spatial-temporal Aggregation and Motion-guided Feature Fusion, capturing motion clues and sampling dense BEV motion features to address the issue of sparsity; and 3) Weather-Specific Tracker, which efficiently handles tracking in various weather conditions. To fill the gap of lacking benchmarks for 3D SOT in adverse weather, we simulate physically valid adverse weather conditions on the KITTI and NuScenes datasets, creating two benchmarks: KITTI-A and NuScenes-A. Extensive experiments demonstrate that UAWTrack achieves state-of-the-art performance under all weather conditions.


![UAWTrack](figures/pipeline.png)


## :scroll:Datasets


To address the lack of datasets for 3D SOT under adverse weather conditions, we simulate physically valid weather on the KITTI and NuScenes datasets, generating two new datasets, KITTI-A and NuScenes-A. These datasets include three types of adverse weather — rain, snow, and fog — each with three intensity levels, as well as clear weather conditions. Below, we provide technical details on the simulated weather types, with visualization examples.


**Rain:** We simulate rain using the LISA technique on both KITTI and NuScenes datasets. Rainfall is categorized into three levels with rates set at {0.20, 1.5625, and 7.29}.


**Snow:** Snow simulation is also implemented using the LISA technique, with snowfall rates mirroring the rain intensities at {0.20, 1.5625, and 7.29}.


**Fog:** Fog datasets are generated by setting the attenuation coefficient to {0.005, 0.02, and 0.06} across three levels, based on the clear KITTI and NuScenes datasets.
![kitti&nus](figures/dataset.png)


## :crown:Main Results
### KITTI
<table>
<thead>
<tr>
<th align="center">Weather Type</th>
<th align="center">Tracker</th>
<th align="center">Source</th>
<th align="center">Car</th>
<th align="center">Pedestrian</th>
<th align="center">Van</th>
<th align="center">Cyclist</th>
<th align="center">Mean</th>
<th align="center">Mean by Category</th>
</tr>
</thead>
  
<tr>
<th align="center" rowspan="5" nowrap="nowrap">Clear</th>
<td align="center">P2B</td>
<td align="center">CVPR'20</td>
<td align="center">54.4/68.7</td>
<td align="center">36.9/59.6</td>
<td align="center">42.2/50.8</td>
<td align="center">27.9/37.7</td>
<td align="center">45.2/62.5</td>
<td align="center">40.4/54.2</td>
</tr>
<tr>
<td align="center">M2Track</td>
<td align="center">CVPR'22</td>
<td align="center">62.7/76.0</td>
<td align="center">49.9/80.4</td>
<td align="center">61.4/77.2</td>
<td align="center">73.1/93.4</td>
<td align="center">57.3/78.4</td>
<td align="center">61.8/81.8</td>
</tr>
<tr>
<td align="center">GLT-T</td>
<td align="center">AAAI'23</td>
<td align="center">66.3/79.3</td>
<td align="center">44.8/71.5</td>
<td align="center">44.8/52.7</td>
<td align="center">58.3/87.8</td>
<td align="center">54.9/73.8</td>
<td align="center">53.5/72.9</td>
</tr>
<tr>
<td align="center">MBPTrack</td>
<td align="center">ICCV'23</td>
<td align="center">70.6/81.3</td>
<td align="center">58.3/85.0</td>
<td align="center">67.0/78.4</td>
<td align="center">69.6/93.0</td>
<td align="center">64.9/82.9</td>
<td align="center">66.4/84.4</td>
</tr>
<tr>
<td align="center">UAWTrack</td>
<td align="center">AAAI'25</td>
<td align="center">71.8/84.0</td>
<td align="center">62.2/88.9</td>
<td align="center">64.5/77.7</td>
<td align="center">74.8/94.1</td>
<td align="center">67.1/85.8</td>
<td align="center">68.3/86.1</td>
</tr>
  
<tr> 
<th align="center" rowspan="5" nowrap="nowrap">Rain</th>
<td align="center">P2B</td>
<td align="center">CVPR'20</td>
<td align="center">35.0/42.1</td>
<td align="center">36.7/58.8</td>
<td align="center">20.6/23.2</td>
<td align="center">27.5/38.0</td>
<td align="center">34.3/47.6</td>
<td align="center">30.0/40.5</td>
</tr>
<tr>
<td align="center">M2Track</td>
<td align="center">CVPR'22</td>
<td align="center">42.9/52.1</td>
<td align="center">50.5/81.8</td>
<td align="center">26.3/32.5</td>
<td align="center">73.4/93.5</td>
<td align="center">45.4/64.1</td>
<td align="center">45.4/64.1</td>
</tr>
<tr>
<td align="center">GLT-T</td>
<td align="center">AAAI'23</td>
<td align="center">38.5/45.8</td>
<td align="center">44.9/71.0</td>
<td align="center">21.7/23.3</td>
<td align="center">55.9/84.2</td>
<td align="center">40.2/55.6</td>
<td align="center">40.2/55.6</td>
</tr>
<tr>
<td align="center">MBPTrack</td>
<td align="center">ICCV'23</td>
<td align="center">55.0/66.9</td>
<td align="center">58.5/86.1</td>
<td align="center">25.6/28.5</td>
<td align="center">68.9/92.8</td>
<td align="center">54.2/72.4</td>
<td align="center">52.0/68.6</td>
</tr>
<tr>
<td align="center">UAWTrack</td>
<td align="center">AAAI'25</td>
<td align="center">58.3/70.2</td>
<td align="center">58.0/85.8</td>
<td align="center">41.0/49.5</td>
<td align="center">74.5/94.1</td>
<td align="center">57.0/75.6</td>
<td align="center">60.3/74.9</td>
</tr>

<tr> 
<th align="center" rowspan="5" nowrap="nowrap">Snow</th>
<td align="center">P2B</td>
<td align="center">CVPR'20</td>
<td align="center">34.3/41.4</td>
<td align="center">36.3/58.5</td>
<td align="center">20.6/23.2</td>
<td align="center">28.7/39.4</td>
<td align="center">33.8/47.1</td>
<td align="center">30.0/40.6</td>
</tr>
<tr>
<td align="center">M2Track</td>
<td align="center">CVPR'22</td>
<td align="center">41.1/49.6</td>
<td align="center">51.2/82.6</td>
<td align="center">27.3/33.7</td>
<td align="center">72.5/93.2</td>
<td align="center">44.9/63.4</td>
<td align="center">48.0/64.8</td>
</tr>
<tr>
<td align="center">GLT-T</td>
<td align="center">AAAI'23</td>
<td align="center">34.8/41.1</td>
<td align="center">42.3/67.8</td>
<td align="center">21.1/22.6</td>
<td align="center">57.4/87.4</td>
<td align="center">37.3/52.0</td>
<td align="center">38.9/54.7</td>
</tr>
<tr>
<td align="center">MBPTrack</td>
<td align="center">ICCV'23</td>
<td align="center">53.7/65.5</td>
<td align="center">56.7/82.7</td>
<td align="center">23.1/24.8</td>
<td align="center">69.1/92.9</td>
<td align="center">52.6/69.6</td>
<td align="center">50.7/66.5</td>
</tr>
<tr>
<td align="center">UAWTrack</td>
<td align="center">AAAI'25</td>
<td align="center">57.2/68.9</td>
<td align="center">56.9/84.6</td>
<td align="center">39.6/46.9</td>
<td align="center">74.3/94.0</td>
<td align="center">55.9/74.3</td>
<td align="center">57.0/73.6</td>
</tr>
</table>

![kitti](figures/kitti.png)


### NuScenes
![nus](figures/nus.png)
