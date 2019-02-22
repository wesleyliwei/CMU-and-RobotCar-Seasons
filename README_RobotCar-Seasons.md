# The RobotCar Seasons Dataset
This is the public release of the RobotCar seasons dataset that is used in this paper to 
benchmark visual localization and place recognition algorithms under changing conditions:
```
T. Sattler, W. Maddern, C. Toft, A. Torii, L. Hammarstrand, E. Stenborg, D. Safari, M. Okutomi, M. Pollefeys, J. Sivic, F. Kahl, T. Pajdla. 
Benchmarking 6DOF Outdoor Visual Localization in Changing Conditions. 
Conference on Computer Vision and Pattern Recognition (CVPR) 2018 
```
The dataset is based on the RobotCar dataset described in this paper:
```
W. Maddern, G. Pascoe, C. Linegar, and P. Newman.
1 Year, 1000km: The Oxford RobotCar Dataset.
International Journal of Robotics Research (IJRR), 36(1):3–15, 2017
```
The RobotCar Seasons dataset uses a subset of the images provided in the RobotCar
dataset. It uses images taken under a single reference condition (`overcast-reference`), 
captured at 49 different non-overlapping locations, to represent the scene. For this reference
condition, the dataset provides a reference 3D model reconstructed using COLMAP [1,2]. The
3D model consequently defines a set of 6DOF reference poses for the database images.
In addition, query images taken under different conditions (`dawn`, `dusk`, `night`,
`night-rain`, `overcast-summer`, `overcast-winter`, `rain`, `snow`, `sun`) at the 49 
locations are provided. For these query images, the reference 6DOF poses will not be
released.



## License
The RobotCar Seasons dataset builds on top of the RobotCar datset created by the Oxford
Robotics Institute at Oxford University. The original dataset can be found 
[here](http://robotcar-dataset.robots.ox.ac.uk/). 
The images provided with the RobotCar Seasons dataset originate from the RobotCar
dataset. They are licensed under a 
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/) license and are intended for non-commercial academic use (see also
[here](http://robotcar-dataset.robots.ox.ac.uk/)). Similarly, the intrinsic (in the folder
 `intrinsics/`) and extrinsic (in the folder `extrinsics/`) calibrations of the cameras are 
 licensed under the same license.
As the other files provides by the dataset build upon the original material from the RobotCar 
dataset, they are also licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/) license and are intended for non-commercial academic use.

Please see this [webpage](http://robotcar-dataset.robots.ox.ac.uk/contact/) if you are
interested in using the images commercially.

### Using the RobotCar Seasons Dataset
By using the RobotCar Seasons dataset, you agree to the license terms set out above.
If you are using the RobotCar Seasons dataset in a publication, please cite **both** of the
following two papers:
```
@inproceedings{Sattler2018CVPR,
  author={Sattler, Torsten and Maddern, Will and Toft, Carl and Torii, Akihiko and Hammarstrand, Lars and Stenborg, Erik and Safari, Daniel and Okutomi, Masatoshi and Pollefeys, Marc and Sivic, Josef and Kahl, Fredrik and Pajdla, Tomas},
  title={{Benchmarking 6DOF Outdoor Visual Localization in Changing Conditions}},
  booktitle={Conference on Computer Vision and Pattern Recognition (CVPR)},
  year={2018},
}

@article{Maddern2017IJRR,
  author={Maddern, Will and Pascoe, Geoffrey and Linegar, Chris and Newman, Paul},
  title={{1 Year, 1000km: The Oxford RobotCar Dataset}},
  journal = {The International Journal of Robotics Research (IJRR)},
  volume = {36}, 
  number = {1}, 
  pages = {3-15}, 
  year = {2017},
}
```

### Image Details
The RobotCar Seasons dataset uses images captured with the Grasshopper 2 Left, Right, and
Rear cameras mounted on the vehicle used to create the original RobotCar dataset. The 
images provided with the RobotCar Seasons dataset have been undistorted.
Below is a table mapping the images taken under different conditions to the capture dates
listed on the RobotCar [webpage](http://robotcar-dataset.robots.ox.ac.uk/). An extended 
version of this table is included in the extended version of the CVPR 2018 paper that can be
found on [arXiv](https://arxiv.org/abs/1707.09092).

Condition | Capture Date
------------|----------------
overcast-reference | 28 Nov 2014
dawn | 16 Dec 2014
dusk | 20 Feb 2015
night | 10 Dec 2014
night-rain | 17 Dec 2014
overcast-summer | 22 May 2015
overcast-winter | 13 Nov 2015
rain |  25 Nov 2014
snow | 3 Feb 2015
sun | 10 Mar 2015

### Privacy
We take privacy seriously. If you have any concerns regarding the images and other data
provided with this dataset, please [contact us](mailto:sattlert@inf.ethz.ch).



## Provided Files
The following files are provides with this release of the RobotCar Seasons dataset in various 
directories:
* `3D-models/`: Contains the 3D models created from the reference images.
* `extrinsics/`: Contains the extrinsic camera calibration between the three cameras used in
 the dataset.
* `images/`: Contains the images of the RobotCar Seasons dataset.
* `intrinsics/`: Contains the intrinsic calibrations of the three cameras used in the dataset.
 
In the following, we will describe the different files provided with the dataset in more detail.

### 3D Models
This directory contains the reference 3D models build for the dataset. We provide two types of 
3D models: A `full` model containing all 49 locations, stored in the subdirectory 
`all-merged`, and `individual` reconstructions of the 49 locations, stored in the 
`individual/` subdirectory. All models are in the same coordinate system, i.e., the 
`individual` models are in the same coordinate system as the `full` model.

The `all-merged` model was used to generate the results shown in Tables 4 and 5 of the 
CVPR 2018 paper while the `individual` models were used to generate the results shown in 
Table 6 of the CVPR 2018 paper.

We provide the 3D reconstructions in various formats:
* `COLMAP models` (only for the `individual` models): 3D models in COLMAP's [text format](https://colmap.github.io/format.html#text-format).
* `NVM models` (`.nvm` file names): 3D models in the [NVM file format](http://ccwu.me/vsfm/doc.html#nvm) 
used by VisualSfM [5,6]. 
* `Bundler models` (`.out` and `.list.txt` file names): 3D models in the [file format](http://www.cs.cornell.edu/~snavely/bundler/bundler-v0.4-manual.html#S6) 
used by Bundler [7]. The `.list.txt` file for a given model, e.g., `001_aligned.list.txt` 
for the `001_aligned.out` model, specifies the images in the reconstruction. The order is the 
same as in the reconstruction. Note that the 3D models (`.out` files) have been compressed 
with [gzip](https://www.gzip.org/).
* Binary `.info` files: These are binary files containing the poses of all database images, all 
3D points in the reference 3D model, and their corresponding descriptors. A C++ code 
snippet for loading the data is available [here](https://s3.amazonaws.com/LocationRecognition/Datasets/load_info_file_snippet.cc).

For the `individual` models, we also provide a file `queries_per_location.zip`. This zip 
file contains a text file for each of the 49 locations. Each text file stores the file names for the 
query images for this location. The format of the filenames is `condition/camera/name.jpg`, 
where `condition` specifies the query condition (for example `sun`), `camera` the camera 
used to capture the image (for example `rear`), and `name` is the timestamp at which the 
image was captured.

Please familiarize yourself with the different file formats. Please also pay special attention to 
the different camera coordinate systems and conventions of the different formats detailed below. 

#### Coordinate Systems and Conventions (Important!)
We provide the 3D models in different file formats for convenience. However, providing 
different formats also comes with a catch: *Different formats use different coordinate systems 
and conventions*.

##### Camera Coordinate Systems
The NVM and COLMAP models use the same **coordinate system**, more specifically, the 
camera coordinate system typically used in *computer vision*. In this camera coordinate 
system, the camera is looking down the `z`-axis, with the `x`-axis pointing to the right and the 
`y`-axis pointing downwards. The coordinate `(0, 0)` corresponds to the top-left corner of 
an image. 

The Bundler models and the `.info` files (which are based on the Bundler models) use the 
same camera coordinate system, but one that differs from the *computer vision camera 
coordinate system*. More specifically, they use the camera coordinate system typically used 
in *computer graphics*. In this camera coordinate system, the camera is looking down the 
`-z`-axis, with the `x`-axis pointing to the right and the `y`-axis pointing upwards. The 
coordinate `(0, 0)` corresponds to the lower-left corner of an image. 
Camera poses in the Bundler and `.info` formats can be converted to poses in the NVM and 
COLMAP formats via the following pseudo-code
```
// Here, R_* is the rotation from the world into the camera coordinate system
// and c_* is the position of the camera in the world-coordinate system.
// We denote the two coordinate systems as "nvm" (NVM and COLMAP) and 
// "out" (Bundler and .info files).
c_nvm = c_out;
// Mirrors the y- and z-coordinates
c_nvm[1] *= -1.0;
c_nvm[2] *= -1.0;
R_nvm = R_out;
// Changes the sign of some entries.
R_nvm(0, 1) *= -1.0;
R_nvm(0, 2) *= -1.0;
R_nvm(1, 0) *= -1.0;
R_nvm(2, 0) *= -1.0;
```
For the **evaluation** of poses estimated on the RobotCar Seasons dataset, you will need to 
provide **pose estimates in the coordinate system used by NVM and COLMAP**.

##### Conventions
The different types of models store poses in different formats.
* The COLMAP models store the rotation (as a quaternion) from the world coordinate system 
to the camera coordinate system as well as the camera translation. Thus, COLMAP stores a 
pose as `[R|t]`.
* The NVM models store the rotation (as a quaternion) from the world coordinate system 
to the camera coordinate system as well as the camera position in world coordinates. Thus, 
NVM stores a pose as `R, c` and the camera translation can be computed as 
`t = -(R * c)`.
* The Bundler models and `.info` files store the rotation (as a 3x3 matrix) from the world 
coordinate system to the camera coordinate system as well as the camera translation. Thus, 
they store a pose as `[R|t]`.

We strongly recommend that you familiarize yourself with the file format of the models that 
you plan to use.


#### COLMAP Databases
In addition to the 3D models, we provide two [COLMAP](https://colmap.github.io/) databases, 
`overcast-reference.db` and `query.db`, storing the upright RootSIFT [3,4] features used 
in the CVPR 2018 paper for the reference and query images, respectively. COLMAP provides 
functionality to export the features from the databases.

### Extrinsics
The extrinsic parameters of the three cameras on the car with respect to the car itself. The 
extrinsics are provided as a 4x4 matrix
```
[R c]
[0 1]
```
where `R` is a rotation matrix that maps from *camera to world coordinates* and `c` is the
position of the camera in world coordinates. The entries of the matrix are separated by `,`.

### Images
This directory contains zip files with the images, one for each condition. Each zip file extracts
to a subdirectory with the name of the condition. After downloading and unzipping, place all
subdirectories into a single directory called `images/`.
All images besides those in the `overcast-reference/` directory consistute the query 
images of the RobotCar Seasons dataset.

### Intrinsics
The intrinsic calibration of the three cameras. For each camera, two focal length values (`fx` 
and `fy` for the two axes)  and the position of the principal point (`cx` and `cy`) is provided. 
Since all images used in the dataset have been undistorted, the cameras can be modeled by
the pinhole camera model. The coordinate `(0, 0)` corresponds to the top-left corner of an
image, with the x-axis pointing to the right and the y-axis pointing downwards.



## Evaluating Results on the RobotCar Seasons Datset
We are currently setting up an [evaluation service](http://visuallocalization.net/) for the benchmarks proposed in the CVPR 
2018 paper. You will be able to upload the poses estimated by your method to this service, 
which in turn will provide results to you. While the service is being set-up, we will manually 
evaluate the results for you. To use this service, please send your results via email to 
[Torsten Sattler](mailto:sattlert@inf.ethz.ch).

Please submit your results as a text file using the following file format. For each query 
image for which your method has estimated a pose, use a single line. This line should store the
result as `camera/name.jpg qw qx qy qz tx ty tz`.  
Here, `camera` speficies the camera used to capture the image, i.e., either `left`, `rear`, or 
`right`. `name` corresponds to the timestamp of the image. `qw qx qy qz` represents the 
**rotation** from world to camera coordinates as a **unit quaternion**. `tx ty tz` is the 
camera **translation** (**not the camera position**). 
An example, obtained using the *DenseVLAD* baseline from the CVPR 2018 paper, for such a 
line is 
```
rear/1417178853389469.jpg 0.655230866337965 -0.536609290501044 -0.340346549997501 -0.408516459863989 24.094399999999997 24.855200000000004 -120.244000000000028
```
Note that the type of condition **is not specified** as there is a unique mapping from 
timestamps to conditions.

Please adhere to the following naming convention for the files that you submit:
```
RobotCar_eval_[yourmethodname].txt
```
Here, `yourmethodname` is some name or identifier chosen by yourself. This name or identifier 
should be as unique as possible to avoid confusion with other methods. Once the evaluation 
service is ready, it will be used to display the results of your method.

**IMPORTANT:** Our evaluation tools expect that the coordinate system in which the camera 
pose is expressed is the **NVM or COLMAP coordinate system** (both use the same 
system). If you are using the Bundler or `.info` coordinate system to estimate poses, you will 
need to **convert poses to the NVM / COLMAP coordinate system** before submission. 
A good **sanity check** to ensure that you are submitting poses in the correct format is to 
query with a reference image and then check whether the pose matches the reference pose 
defined in the COLMAP reconstruction (or the NVM model after converting the stored camera 
position to a translation as described above).


## References:
1. J. L. Schönberger, J.-M. Frahm. Structure-from-Motion Revisited. Conference on
Computer Vision and Pattern Recognition (CVPR) 2016.
2. J. L. Schönberger, E. Zheng, M. Pollefeys, J.-M. Frahm. Pixelwise View Selection for
Unstructured Multi-View Stereo. European Conference on Computer Vision (ECCV) 2016.
3. R. Arandjelović, A. Zisserman. Three things everyone should know to improve object 
retrieval. Conference on Computer Vision and Pattern Recognition (CVPR) 2012.
4. D. Lowe. Distinctive Image Features from Scale-Invariant Keypoints. International Journal 
of Computer Vision (IJCV) 2004.
5. C. Wu. Towards Linear-time Incremental Structure From Motion. 3DV 2013
6. C. Wu. VisualSFM: A Visual Structure from Motion System. http://ccwu.me/vsfm/, 2011
7. N. Snavely, S. M. Seitz, R. Szeliski. Photo Tourism: Exploring image collections in 3D. 
ACM Transactions on Graphics (Proceedings of SIGGRAPH 2006) 2006.
