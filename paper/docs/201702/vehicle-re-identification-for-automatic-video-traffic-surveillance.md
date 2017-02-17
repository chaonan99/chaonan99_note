## Vehicle Re-Identification for Automatic Video Traffic Surveillance
* [paper](http://www.cv-foundation.org/openaccess/content_cvpr_2016_workshops/w25/papers/Zapletal_Vehicle_Re-Identification_for_CVPR_2016_paper.pdf)
* [dataset](https://medusa.fit.vutbr.cz/traffic/research-topics/detection-of-vehicles-and-datasets/vehicle-re-identification-for-automatic-video-traffic-surveillance-ats-cvpr-2016/)
* Tasks: vehicle re-identification

### Approach
* 3D bounding box
* Linear regression with color histogram and/or HOG feature
* Car image is projected (3D box -> plane) and split into a grid, features are computed in each grid
    * Only the right and front sides are used to project

### Dataset
* Statistics
    - 5 video shots from different angles, at roughly the same spot, each has A and B folder
    - Over 800 vehicles
    - Training images are projected images
* Positive pairs generation
    * Each car has a _representative_ image and serval _combined_ images
    * Each camera has a ground truth cvs file, matching the same car (_representative_ image) in xA and xB (x=1,2,3,4,5)
    * Positive pairs are randomly choosed (in the paper, around 12,000-16,000 of them are generated in total)
* Negative pairs are randomly selected within the same camera (xA and xB) rather than cross-camera pairs
* Test set
    - Containing 1,232 pairs crowd-sourced by about 500 people
    - Use threshold to judge if a pair is the same car and plot ROC curve
