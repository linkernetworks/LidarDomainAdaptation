# Lidar Domain Adaptation Resource list
## Survey Papers
#### [A Survey on Deep Domain Adaptation for LiDAR Perception](https://arxiv.org/pdf/2106.02377.pdf)
## Domain Invariant Data
### Sensor-to-Sensor
#### [CNN-based synthesis of realistic high-resolution LiDAR data](https://arxiv.org/pdf/1907.00787.pdf) 
Compare down-upsampled with original range images via pointwise/perceptive/semantic losses. Possible to use both on semantic and detection tasks without using the semantic loss \
Reproducibility: Hard / No Code
#### [Simulation-based Lidar Super-resolution for Ground Vehicles](https://arxiv.org/pdf/2004.05242.pdf) 
Use U-Net with droupout on range image to upsample simulated environments with different sensors. Any super resolution model would likely perform similar, mentioning effect of drop out rate. \
Reproducibility: Hard (Custom-Simulation Data) / [Code](https://github.com/RobustFieldAutonomyLab/lidar_super_resolution) 
#### [Improved Semantic Segmentation of Low-Resolution 3D Point Clouds Using Supervised Domain Adaptation](https://ieeexplore.ieee.org/document/9257903) 
TBD 
#### [Analyzing the Cross-Sensor Portability of Neural Network Architectures for LiDAR-based Semantic Labeling](https://arxiv.org/pdf/1907.02149.pdf)
2D-3D labelling transfer mechanism with different sensor cross tests, no specific adaptation mechanism is proposed.
### Dataset-to-Dataset
#### [Complete & Label: A Domain Adaptation Approach to Semantic Segmentation of LiDAR Point Clouds](https://arxiv.org/pdf/2007.08488.pdf)
Create incomplete versions of original lidars and train a voxel based sparse convolution completer. \
Reproducibility: Hard / No Code
## Domain Mapping 
### Dataset-to-Dataset n Sim-to-Real
#### [Domain Adaptation for Vehicle Detection from Bird’s Eye View LiDAR Point Cloud Data](https://arxiv.org/pdf/1905.08955.pdf)
Using GAN to make synthethic LIDAR-BEV data more realistic improve BEV-YOLO detector
#### [LiDAR Sensor modeling and Data augmentation with GANs for Autonomous driving](https://arxiv.org/pdf/1905.07290.pdf)
Cycle GAN over BEV-LIDAR of synthetic data to improve performance of YOLO-R over KITTI. [50] is pretty much same work by same authors.
### Sim-to-Real
#### [Deep Generative Modeling of LiDAR Data](https://arxiv.org/pdf/1812.01180.pdf)
Special 2D representation of LIDAR data by keeping (x,y,z) unlike range image. Perform noise and removal to original data, use VAE and GAN for reconstruction. Surprisingly good results with VAE trained only on compressed embeddings not the noisy data itself. \
Reproducilibility: Easy / [Code](https://github.com/pclucas14/lidar_generation)
#### [Learning to Drop Points for LiDAR Scan Synthesis](https://arxiv.org/pdf/2102.11952.pdf)
Uses baseline [Deep Generative Modeling of LiDAR Data](https://arxiv.org/pdf/1812.01180.pdf), similar approach with more advanced data prep with Gumbel distribution based mask on confidence map for providing differentiability for back-prop and point drop modeling. \
Quite amazing test results with recovery on manual perturbation. 🌟 \
Reproducilibility: Easy / [Code](https://github.com/kazuto1011/dusty-gan)
#### [ePointDA: An End-to-End Simulation-to-Real Domain Adaptation Framework for LiDAR Point Cloud Segmentation](https://arxiv.org/pdf/2009.03456.pdf)
Using modules of self-supervised dropout noise rendering, statistics-invariant and spatially-adaptive feature alignment,and transferable segmentation learning. \
Reproducilibility: Hard
### Dataset-to-Dataset
#### [Domain Adaptation in LiDAR Semantic Segmentation](https://arxiv.org/pdf/2010.12239.pdf)
Using combination of statistics/feature normalization with [MinEnt](https://arxiv.org/abs/1811.12833), achieves good results with inter-dataset adaptations. Simple tricks however no code.\
Reproducilibility: Medium
### Sensor-to-Sensor
#### [Domain Transfer for Semantic Segmentation of LiDAR Data using Deep Neural Networks](http://ras.papercept.net/images/temp/IROS/files/0060.pdf)
From creators of Semantic KITTI, transfer Velodyne HDL-64 scans to match scans from a Velodyne HDL-32, a sensor with a lower resolution and different FOV.
Exploit the fusion of multiple scans of the source dataset and meshing for a denser map to sample virtual scans, however this aims high to low quality adaptation. \
Reproducilibity: Medium / [Code](https://github.com/PRBonn/lidar_transfer)
## Domain Invariant Feature Learning
### Sim-to-Real
#### [SqueezeSegV2](https://arxiv.org/pdf/1809.08495.pdf)
Predecessor work of **ePointDA**, and following work of SqueezeSeg, uses GTA-LIDAR and combines  learned intensity rendering, geodesic correlation alignment, and progressive domain calibration for adaptation. \
Reproducibility: Easy / [Code](https://github.com/xuanyuzhou98/SqueezeSegV2)
### Multi adaptations
#### [xMUDA: Cross-Modal Unsupervised Domain Adaptation for 3D Semantic Segmentation](https://arxiv.org/pdf/1911.12676.pdf)
One of the few model using multi modality (lidar-image) learning with 3d semantic labels. Mimicking between the modalities, achieved through KL divergence. \
An architecture with separate main and mimicking head to disentangle the segmentation from the cross-modal learning objective. Considers day-night, country-country, dataset-dataset adaptation. \
Reproducilibity: Medium / [Code](https://github.com/valeoai/xmuda)
### Dataset-to-Dataset
#### [LiDARNet: A Boundary-Aware Domain Adaptation Model for Point Cloud Semantic Segmentation](https://arxiv.org/pdf/2003.01174.pdf)
Boundary-aware domain adaptation approach for semantic segmentation of the lidar point cloud. Utilizes the GatedSCNN to enable the domain shared feature extractor to keep boundary information in the domain shared features and utilize the learned boundary to refine the segmentation. \
Reproducilibity: Medium / [Code](https://github.com/unmannedlab/LiDARNet)
### Sensor-to-Sensor
#### [Range Adaptation for 3D Object Detection in LiDAR](https://arxiv.org/pdf/1909.12249.pdf)
Cross-range (near/far) and cross-device(multi-dataset) adaptation using adversarial global adaptation and fine-grained local adaptation. Only losses are described no architecture or training details provided. 🌟 \
Reproducilibity: Hard
### Dataset-to-Dataset
#### [SF-UDA3D: Source-Free Unsupervised Domain Adaptation for LiDAR-Based 3D Object Detection](https://arxiv.org/pdf/2010.08243.pdf)
Pseudo-annotations, reversible scale-transformations and motion coherency of object size. Beats the few shot tuning only with scale supervision 🌟 \
Reproducilibity: Hard / [Code](https://github.com/saltoricristiano/SF-UDA-3DV) not released yet.
## Normalization Statistics n Others
#### [Cross-Sensor Deep Domain Adaptation for LiDAR Detection and Segmentation](https://repository.tudelft.nl/islandora/object/uuid%3A618db181-4d0d-4384-a9b2-4c0a8925da4f/datastream/OBJ/download)
Task agnostic, multi task approach combining detection and segmentation using SECOND-like architecture.
Reproducilibity: Hard
#### [Pseudo-labeling for Scalable 3D Object Detection](https://arxiv.org/pdf/2103.02093.pdf)
Using wide/augmented multi-frame teachers for pseudolabelling on unlabeled data and train students over those. Shows promising results especially when the labeled data ratio is low. 🌟 \
Reproducilibity: Medium
#### [Exploiting Playbacks in Unsupervised Domain Adaptation for 3D Object Detection](https://arxiv.org/pdf/2103.14198.pdf)
Uses self-training created pseudo-labels with smoothing(online/offline), resizing and extrapolation(dreaming). 🌟 \
Reproducibility: Hard
#### [ST3D: Self-training for Unsupervised Domain Adaptation on 3D Object Detection](https://arxiv.org/pdf/2103.05346.pdf)
Random scale object augmentation, iou-loss for quality aware and memory ensembling, curriculum data augmentation self-training(pseudo-label generation). 🌟🌟 \
Reproducilibility: Easy / [Code](https://github.com/CVMI-Lab/ST3D)
## Dataset Benchmark
#### [One Million Scenes for Autonomous Driving: ONCE Dataset](https://arxiv.org/pdf/2106.11037.pdf)
Benchmark/Dataset work in self(contrastive/clustering), semi-supervised(pseudo-label,student/teacher) methods, and unsupervised methods (SN-like) over their new dataset and cross dataset using the SECOND as baseline. 🌟🌟 \
Reproducibility : Easy / [Code](https://github.com/PointsCoder/Once_Benchmark) (only semi-supervised and unsupervised methods)
## Table 
![image](https://user-images.githubusercontent.com/46666499/125759984-3651b19b-c0cb-4be2-a99e-24b164b43667.png)
