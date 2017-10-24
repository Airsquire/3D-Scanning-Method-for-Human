# 3D Reconstruction Algorithm for human

## SLAM(Simultaneous localization and mapping)

[Comparison Between RGB-D camera and Laser](http://paulbourke.net/miscellaneous/laservs3d/)

[SLAM between 2010-2016](https://link.springer.com/article/10.1186/s41074-017-0027-2)

Tango error rate +-2cm price $500

Lazer error rate +-0.3 mm price $70000

In order to obtain a geometrically consistent map, pose-graph optimization and deformation graph optimization are used in RGB-D vSLAM algorithms. Kerl et al. used pose-graph optimization to reduce the accumulative error [23]. This pose-graph optimization is almost the same as loop closure in monocular vSLAM algorithms.

Especially, Google Tango provides a stable estimation result by combining internal sensor information.

## SFM

[Difference between SFM to MVS](https://stackoverflow.com/questions/39217717/in-computer-vision-what-does-mvs-do-that-sfm-cant)

Input -- A set of 2D images

Output -- coarse 3D Point Cloud

Procedure

  1. Camera Coordinator
  2. Camera Matrix(Length, F)
  3. Feature point extraction
  4. findEssentialMat()
  5. Recover 3D Matrix for each pixel in 2D images

[Experinment reconstruct a small Cap](http://blog.csdn.net/linczone/article/details/46237197)

Test Software: VisualSFM

Reconstruct a Small
File Size: 350M
Picture amout: 65
Time consume: 30 mins


## MVS

MVS algorithm is used to refine the mesh obtained by the SfM technique, resulting in what is called a dense reconstruction. This algorithm requires the camera parameters of each image to work, which is output by the SfM algorithm. As it works on a more constrained problem (since they already have the camera parameters of every image like position, rotation, focal, etc.), MVS will compute 3D vertices on regions which were not (or could not be) correctly detected by descriptors or matched. This is what PMVS2 does.

Input: camera parameters of each image to work, which is output by the SfM algorithm
Output: dense 3d point Cloud
