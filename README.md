# WMAD-Benchmarks

---

This repository contains a curated list of resources related to World Models for Autonomous Driving (WMAD), based on the our [survey](https://arxiv.org/pdf/2501.11260v3).

## Paper Details

**Title:** A Survey of World Models for Autonomous Driving

**Authors:** Tuo Feng, Wenguan Wang, Yang Yi

[**Paper Link**](https://arxiv.org/abs/2501.11260v3)

[**Paper List**](https://github.com/FengZicai/AwesomeWMAD)

[**Benchmarks**](https://github.com/FengZicai/WMAD-Benchmarks)

---


## Evaluation Platforms and Benchmarks
### **CarlaSC.**  
[CarlaSC](https://ieeexplore.ieee.org/abstract/document/9815141) is a synthetic semantic scene-completion dataset generated using the CARLA simulator. It provides 4D occupancy sequences at a resolution of 128×128×8, covering a 25.6m×25.6m×3m volume around the ego-vehicle. CarlaSC features diverse dynamic driving scenarios, making it well suited for evaluating reconstruction and generation methods in controlled yet realistic environments.

### **NuScenes.**
[nuScenes](https://openaccess.thecvf.com/content_CVPR_2020/papers/Caesar_nuScenes_A_Multimodal_Dataset_for_Autonomous_Driving_CVPR_2020_paper.pdf) contains 1000 driving scenes, partitioned into 700 training, 150 validation, and 150 testing subsets. It integrates synchronized RGB images from six surround-view cameras (covering a 360 degree horizontal field) and high-resolution point clouds captured by a 32-beam LiDAR. Leveraging its rich annotations and centimeter-level positioning accuracy, this dataset serves as a comprehensive benchmark for autonomous-driving tasks such as motion planning.

### **Occ3D-nuScenes.**
[Occ3D-nuScenes](https://proceedings.neurips.cc/paper_files/paper/2023/file/cabfaeecaae7d6540ee797a66f0130b0-Paper-Datasets_and_Benchmarks.pdf) is generated from the real-world [nuScenes](https://openaccess.thecvf.com/content_CVPR_2020/papers/Caesar_nuScenes_A_Multimodal_Dataset_for_Autonomous_Driving_CVPR_2020_paper.pdf) dataset using the same fusion and voxelization operations. This dataset contains 700 training sequences and 150 validation sequences, each with approximately 40 frames sampled at 2Hz. The perception range is [-40m,-40m,-1m,40m,40m,5.4m] and the voxel size is [0.4m,0.4m,0.4m], leading to a grid size of [200,200,16]. Each grid cell is assigned one of 18 possible semantic categories, including 6 background and 10 foreground classes, and extra “others’’ and “free’’ categories.

### **Occ3D-Waymo.**
[Occ3D-Waymo](https://proceedings.neurips.cc/paper_files/paper/2023/file/cabfaeecaae7d6540ee797a66f0130b0-Paper-Datasets_and_Benchmarks.pdf) is derived from the real-world [Waymo](https://openaccess.thecvf.com/content_CVPR_2020/papers/Sun_Scalability_in_Perception_for_Autonomous_Driving_Waymo_Open_Dataset_CVPR_2020_paper.pdf), comprising 798 training sequences and 202 validation sequences, each with approximately 200 frames sampled at 10Hz. Occupancy labels cover 17 semantic categories and are generated via multi-frame LiDAR fusion and voxelization.

### **OpenScene.**
[OpenScene](https://arxiv.org/pdf/2405.02595), derived from the [nuPlan](https://openaccess.thecvf.com/content/CVPR2022/papers/Cao_MonoScene_Monocular_3D_Semantic_Scene_Completion_CVPR_2022_paper.pdf) dataset, comprises over 120 hours of data collected in Boston, Pittsburgh, Las Vegas and Singapore, and adds detailed occupancy labels. It provides RGB images from eight surround-view cameras alongside a merged ego-centred point cloud aggregated from five LiDAR sensors, yielding more than 600000 frames in total. Its smaller counterpart, **OpenScene-mini**, includes 5392 training frames and 8729 validation frames. [ViDAR](https://openaccess.thecvf.com/content/CVPR2024/papers/Yang_Visual_Point_Cloud_Forecasting_enables_Scalable_Autonomous_Driving_CVPR_2024_paper.pdf) conducted point-cloud forecasting within the ego-coordinate volume spanning [–51.2m, –51.2m, –5.0m] to [51.2m, 51.2m, 3.0m] at a discretisation of 200×200×16.

---

## Performance Comparison Tables

- [Table 1: 4D Scene Generation Comparison](#table-1-4d-scene-generation-comparison)
- [Table 2: Point-Cloud Forecasting on OpenScene-mini](#table-2-point-cloud-forecasting-on-openscene-mini)
- [Table 3: 4D Occupancy Forecasting on Occ3D-nuScenes](#table-3-4d-occupancy-forecasting-on-occ3d-nuscenes)
- [Table 4: Motion-Planning Performance on nuScenes](#table-4-motion-planning-performance-on-nuscenes)


### Table 1: 4D Scene Generation Comparison

| Dataset | Method | #Frames | IS&nbsp;↑ (2D) | FID&nbsp;↓ (2D) | KID&nbsp;↓ (2D) | P&nbsp;↑ (2D) | R&nbsp;↑ (2D) | IS&nbsp;↑ (3D) | FID&nbsp;↓ (3D) | KID&nbsp;↓ (3D) | P&nbsp;↑ (3D) | R&nbsp;↑ (3D) |
|---------|--------|---------|---------------|----------------|----------------|---------------|---------------|---------------|----------------|----------------|---------------|---------------|
| CarlaSC | [OccSora](https://arxiv.org/pdf/2405.20337) | 16 | 1.030 | 28.55 | 0.008 | 0.224 | 0.010 | 2.257 | 1559  | 52.72 | 0.380 | 0.151 |
| CarlaSC | [DynamicCity](https://openreview.net/pdf?id=M7KyLjuN0A) | — | **1.040** | **12.94** | **0.002** | **0.307** | **0.018** | **2.331** | **354.2** | **19.10** | **0.460** | **0.170** |
| Occ3D-Waymo | [OccSora](https://arxiv.org/pdf/2405.20337) | 16 | 1.005 | 42.53 | 0.049 | 0.654 | 0.004 | 3.129 | 3140  | 12.20 | 0.384 | 0.001 |
| Occ3D-Waymo | [DynamicCity](https://openreview.net/pdf?id=M7KyLjuN0A) | — | **1.010** | **36.73** | **0.001** | **0.705** | **0.015** | **3.206** | **1806** | **77.71** | **0.494** | **0.026** |


### Table 2: Point-Cloud Forecasting on OpenScene-mini

| Method | 0.5 s | 1.0 s | 1.5 s | 2.0 s | 2.5 s | 3.0 s | Avg. |
|--------|-------|-------|-------|-------|-------|-------|------|
| [ViDAR](https://openaccess.thecvf.com/content/CVPR2024/papers/Yang_Visual_Point_Cloud_Forecasting_enables_Scalable_Autonomous_Driving_CVPR_2024_paper.pdf) | 1.34 | 1.43 | 1.51 | 1.60 | 1.71 | 1.86 | 1.58 |
| [DFIT-OccWorld-O](https://arxiv.org/pdf/2412.13772) | 0.38 | 0.72 | 0.74 | 0.75 | 0.79 | 0.86 | 0.70 |
| [DFIT-OccWorld-V](https://arxiv.org/pdf/2412.13772) | 0.40 | 0.75 | 0.78 | 0.83 | 0.89 | 0.90 | 0.76 |


### Table 3: 4D Occupancy Forecasting on Occ3D-nuScenes

| Method | Input | Aux. Sup. | mIoU (1 s) ↑ | mIoU (2 s) ↑ | mIoU (3 s) ↑ | mIoU (Avg.) ↑ | IoU (1 s) ↑ | IoU (2 s) ↑ | IoU (3 s) ↑ | IoU (Avg.) ↑ |
|--------|-------|-----------|-----------|-----------|-----------|-------------|-----------|-----------|-----------|------------|
| Copy&Paste | 3D-Occ | None | 14.91 | 10.54 | 8.52 | 11.33 | 24.47 | 19.77 | 17.31 | 20.52 |
| [OccWorld](https://arxiv.org/pdf/2311.16038) | 3D-Occ | None | 25.78 | 15.14 | 10.51 | 17.14 | 34.63 | 25.07 | 20.18 | 26.63 |
| [RenderWorld](https://arxiv.org/pdf/2409.11356?) | 3D-Occ | None | 28.69 | 18.89 | 14.83 | 20.80 | 37.74 | 28.41 | 24.08 | 30.08 |
| [OccLLaMA-O](https://arxiv.org/pdf/2409.03272)  | 3D-Occ | None | 25.05 | 19.49 | 15.26 | 19.93 | 34.56 | 28.53 | 24.41 | 29.17 |
| [DOME-O](https://arxiv.org/pdf/2410.10429) | 3D-Occ | None | 35.11 | 25.89 | 20.29 | 27.10 | 43.99 | 35.36 | 29.74 | 36.36 |
| [DFIT-OccWorld-O](https://arxiv.org/pdf/2412.13772) | 3D-Occ | None | 31.68 | 21.29 | 15.18 | 22.71 | 40.28 | 31.24 | 25.29 | 32.27 |
| [TPVFormer](https://openaccess.thecvf.com/content/CVPR2023/papers/Huang_Tri-Perspective_View_for_Vision-Based_3D_Semantic_Occupancy_Prediction_CVPR_2023_paper.pdf)+Lidar+[OccWorld-T](https://arxiv.org/pdf/2311.16038) | Camera | Semantic LiDAR | 4.68 | 3.36 | 2.63 | 3.56 | 9.32 | 8.23 | 7.47 | 8.34 |
| [TPVFormer](https://openaccess.thecvf.com/content/CVPR2023/papers/Huang_Tri-Perspective_View_for_Vision-Based_3D_Semantic_Occupancy_Prediction_CVPR_2023_paper.pdf)+[SelfOcc](https://openaccess.thecvf.com/content/CVPR2024/papers/Huang_SelfOcc_Self-Supervised_Vision-Based_3D_Occupancy_Prediction_CVPR_2024_paper.pdf)+[OccWorld-S](https://arxiv.org/pdf/2311.16038) | Camera | None | 0.28 | 0.26 | 0.24 | 0.26 | 5.05 | 5.01 | 4.95 | 5.00 |
| [OccWorld-F](https://arxiv.org/pdf/2409.03272) | Camera | None | 8.03 | 6.91 | 3.54 | 6.16 | 23.62 | 18.13 | 15.22 | 18.99 |
| [OccLLaMA-F](https://arxiv.org/pdf/2409.03272) | Camera | None | 10.34 | 8.66 | 6.98 | 8.66 | 25.81 | 23.19 | 19.97 | 22.99 |
| [RenderWorld](https://arxiv.org/pdf/2409.11356?) | Camera | None | 2.83 | 2.55 | 2.37 | 2.58 | 14.61 | 13.61 | 12.98 | 13.73 |
| [DOME-F](https://arxiv.org/pdf/2410.10429) | Camera | None | 24.12 | 17.41 | 13.24 | 18.25 | 35.18 | 27.90 | 23.44 | 28.84 |
| [DFIT-OccWorld](https://arxiv.org/pdf/2412.13772) | Camera | 3D-Occ | 13.38 | 10.16 | 7.96 | 10.50 | 19.18 | 16.85 | 15.02 | 17.02 |


### Table 4: Motion-Planning Performance on nuScenes

| Method | Input | Aux. Sup. | L2 (1 s) ↓ | L2 (2 s) ↓ | L2 (3 s) ↓ | L2 (Avg.) ↓ | Coll. (1 s) % ↓ | Coll. (2 s) % ↓ | Coll. (3 s) % ↓ | Coll. (Avg.) % ↓ |
|--------|-------|-----------|----------|----------|----------|-----------|---------------|---------------|---------------|----------------|
| [IL](https://www.ri.cmu.edu/pub_files/pub4/ratliff_nathan_2006_1/ratliff_nathan_2006_1.pdf) | LiDAR | None | 0.44 | 1.15 | 2.47 | 1.35 | 0.08 | 0.27 | 1.95 | 0.77 |
| [NMP](https://openaccess.thecvf.com/content_CVPR_2019/papers/Zeng_End-To-End_Interpretable_Neural_Motion_Planner_CVPR_2019_paper.pdf) | LiDAR | Box & Motion | 0.53 | 1.25 | 2.67 | 1.48 | 0.04 | 0.12 | 0.87 | 0.34 |
| [FF](https://openaccess.thecvf.com/content/CVPR2021/papers/Hu_Safe_Local_Motion_Planning_With_Self-Supervised_Freespace_Forecasting_CVPR_2021_paper.pdf)  | LiDAR | Freespace | 0.55 | 1.20 | 2.54 | 1.43 | 0.06 | 0.17 | 1.07 | 0.43 |
| [EO](https://arxiv.org/pdf/2210.01917)  | LiDAR | Freespace | 0.67 | 1.36 | 2.78 | 1.60 | 0.04 | 0.09 | 0.88 | 0.33 |
| [ST-P3](https://arxiv.org/pdf/2207.07601) | Camera | Map & Box & Depth | 1.33 | 2.11 | 2.90 | 2.11 | 0.23 | 0.62 | 1.27 | 0.71 |
| [UniAD](https://openaccess.thecvf.com/content/CVPR2023/papers/Hu_Planning-Oriented_Autonomous_Driving_CVPR_2023_paper.pdf) | Camera | Map & Box & Motion & Tracklets & Occ | 0.48 | 0.96 | 1.65 | 1.03 | 0.05 | 0.17 | 0.71 | 0.31 |
| [UniAD](https://openaccess.thecvf.com/content/CVPR2023/papers/Hu_Planning-Oriented_Autonomous_Driving_CVPR_2023_paper.pdf)+[DriveWorld](https://openaccess.thecvf.com/content/CVPR2024/papers/Min_DriveWorld_4D_Pre-trained_Scene_Understanding_via_World_Models_for_Autonomous_CVPR_2024_paper.pdf) | Camera | Map & Box & Motion & Tracklets & Occ | 0.34 | 0.67 | 1.07 | 0.69 | 0.04 | 0.12 | 0.41 | 0.19 |
| [VAD-Tiny](https://openaccess.thecvf.com/content/ICCV2023/papers/Jiang_VAD_Vectorized_Scene_Representation_for_Efficient_Autonomous_Driving_ICCV_2023_paper.pdf) | Camera | Map & Box & Motion | 0.60 | 1.23 | 2.06 | 1.30 | 0.31 | 0.53 | 1.33 | 0.72 |
| [VAD-Base](https://openaccess.thecvf.com/content/ICCV2023/papers/Jiang_VAD_Vectorized_Scene_Representation_for_Efficient_Autonomous_Driving_ICCV_2023_paper.pdf) | Camera | Map & Box & Motion | 0.54 | 1.15 | 1.98 | 1.22 | 0.04 | 0.39 | 1.17 | 0.53 |
| [DriveDreamer](https://arxiv.org/pdf/2309.09777) | Camera | Map & Box & Motion | — | — | — | 0.29 | — | — | — | 0.15 |
| [GenAD](https://arxiv.org/pdf/2402.11502)  | Camera | Map & Box & Motion | 0.36 | 0.83 | 1.55 | 0.91 | 0.06 | 0.23 | 1.00 | 0.43 |
| [OccNet](https://openaccess.thecvf.com/content/ICCV2023/papers/Tong_Scene_as_Occupancy_ICCV_2023_paper.pdf)  | Camera | 3D-Occ & Map & Box | 1.29 | 2.13 | 2.99 | 2.14 | 0.21 | 0.59 | 1.37 | 0.72 |
| [OccWorld-T](https://arxiv.org/pdf/2311.16038) | Camera | Semantic LiDAR | 0.54 | 1.36 | 2.66 | 1.52 | 0.12 | 0.40 | 1.59 | 0.70 |
| [OccWorld-S](https://arxiv.org/pdf/2311.16038) | Camera | None | 0.67 | 1.69 | 3.13 | 1.83 | 0.19 | 1.28 | 4.59 | 2.02 |
| [LAW](https://arxiv.org/pdf/2406.08481)  | Camera | None | 0.26 | 0.57 | 1.01 | 0.61 | 0.14 | 0.21 | 0.54 | 0.30 |
| [Drive-OccWorld](https://ojs.aaai.org/index.php/AAAI/article/view/33010) | Camera | None | 0.32 | 0.75 | 1.49 | 0.85 | 0.05 | 0.17 | 0.64 | 0.29 |
| [ViDAR](https://openaccess.thecvf.com/content/CVPR2024/papers/Yang_Visual_Point_Cloud_Forecasting_enables_Scalable_Autonomous_Driving_CVPR_2024_paper.pdf) | Camera | None | — | — | — | 0.91 | — | — | — | 0.23 |
| [OccWorld-F](https://arxiv.org/pdf/2409.03272)  | Camera | Occ | 0.45 | 1.33 | 2.25 | 1.34 | 0.08 | 0.42 | 1.71 | 0.73 |
| [OccLLaMA-F](https://arxiv.org/pdf/2409.03272) | Camera | Occ | 0.38 | 1.07 | 2.15 | 1.20 | 0.06 | 0.39 | 1.65 | 0.70 |
| [RenderWorld](https://arxiv.org/pdf/2409.11356?) | Camera | Occ | 0.48 | 1.30 | 2.67 | 1.48 | 0.14 | 0.55 | 2.23 | 0.97 |
| [DFIT-OccWorld-V](https://arxiv.org/pdf/2412.13772) | Camera | Occ | 0.42 | 1.14 | 2.19 | 1.25 | 0.09 | 0.19 | 1.37 | 0.55 |
| [OccNet](https://openaccess.thecvf.com/content/ICCV2023/papers/Tong_Scene_as_Occupancy_ICCV_2023_paper.pdf)  | 3D-Occ | Map & Box | 1.29 | 2.31 | 2.98 | 2.25 | 0.20 | 0.56 | 1.30 | 0.69 |
| [OccWorld](https://arxiv.org/pdf/2311.16038) | 3D-Occ | None | 0.43 | 1.08 | 1.99 | 1.17 | 0.07 | 0.38 | 1.35 | 0.60 |
| [RenderWorld](https://arxiv.org/pdf/2409.11356?) | 3D-Occ | None | 0.35 | 0.91 | 1.84 | 1.03 | 0.05 | 0.40 | 1.39 | 0.61 |
| [OccLLaMA-O](https://arxiv.org/pdf/2409.03272) | 3D-Occ | None | 0.37 | 1.02 | 2.03 | 1.14 | 0.04 | 0.24 | 1.20 | 0.49 |
| [DFIT-OccWorld-O](https://arxiv.org/pdf/2412.13772) | 3D-Occ | None | 0.38 | 0.96 | 1.73 | 1.02 | 0.07 | 0.39 | 0.90 | 0.45 |

---


## BibTeX

```bibtex
@article{feng2025survey,
  title={A Survey of World Models for Autonomous Driving},
  author={Feng, Tuo and Wang, Wenguan and Yang, Yi},
  journal={arXiv preprint arXiv:2501.11260},
  year={2025}
}
```