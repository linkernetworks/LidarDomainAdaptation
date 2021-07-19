# Lidar Domain Adaptation Resource list
![image](https://user-images.githubusercontent.com/46666499/125759984-3651b19b-c0cb-4be2-a99e-24b164b43667.png)

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
### Dataset-to-Dataset
#### [Domain Adaptation for Vehicle Detection from Bird’s Eye View LiDAR Point Cloud Data](https://arxiv.org/pdf/1905.08955.pdf)
Using GAN to make synthethic LIDAR-BEV data more realistic improve BEV-YOLO detector
#### [LiDAR Sensor modeling and Data augmentation with GANs for Autonomous driving](https://arxiv.org/pdf/1905.07290.pdf)
Cycle GAN over BEV-LIDAR of synthetic data to improve performance of YOLO-R over KITTI. [50] is pretty much same work by same authors.
### Sim-to-Real
#### [Deep Generative Modeling of LiDAR Data](https://arxiv.org/pdf/1812.01180.pdf)
Special 2D representation of LIDAR data by keeping (x,y,z) unlike range image. Perform noise and removal to original data, use VAE and GAN for reconstruction. Surprisingly good results with VAE trained only on compressed embeddings not the noisy data itself. \
Reproducilibility: Medium / [Code](https://github.com/pclucas14/lidar_generation)
#### [Learning to Drop Points for LiDAR Scan Synthesis](https://arxiv.org/pdf/2102.11952.pdf)
Uses baseline [Deep Generative Modeling of LiDAR Data](https://arxiv.org/pdf/1812.01180.pdf), similar approach with more advanced data prep with Gumbel distribution based mask on confidence map for providing differentiability for back-prop and point drop modeling. \
Quite amazing test results with recovery on manual perturbation. 🌟 \
Reproducilibility: Medium / [Code](https://github.com/kazuto1011/dusty-gan)
#### [ePointDA: An End-to-End Simulation-to-Real Domain Adaptation Framework for LiDAR Point Cloud Segmentation](https://arxiv.org/pdf/2009.03456.pdf)
Using modules of self-supervised dropout noise rendering, statistics-invariant and spatially-adaptive feature alignment,and transferable segmentation learning. \
Reproducilibility: Hard

