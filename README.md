# SelfieDrone

This repository contains the code used and developed during the master thesis entitled: "Tracking and Following a Moving Person Onboard a Pocket Drone”.

Used operative system: Ubuntu 14.04.5 LTS

Three main code components of the project are presented:

## Trackers

Code for the three trackers used in this work. The code for KCF and Struck suffered a few alterations, but the core remains the same as in http://www.robots.ox.ac.uk/~joao/circulant/ and http://www.samhare.net/research/struck, respectively. The third tracker is the Pocket Tracker which was developed during this work. The code for the pocket tracker can be directly implemented on the stereo vision board.

## Matlab

The prototype code of the Pocket Track as well as the code used to build data sets and train the parameters of the detector, respectively PocketTracker.m, PocketAnnotate.m and PocketTrainer.

## Paparazzi

The airframes, flight plans and modules used within paparazzi UAV. The modules are to be used in the following pipeline, first comes the crop of the image(video_crop) to select the area that is of interest to the tracker, then the module for the tracker (KCF or Struck, for the pocket tracker, the stereo vision board sends the detection parameters directly to the drone) and lastly the module to draw the detections in the frames. After the vision modules, the control modules selfie_drone_altitude_controller, selfie_drone_waypoint_generator, selfie_drone_yaw_controller and selfie_drone_guided_mode_control for the Bebop and update_detection for the pocket drone are used to calculate the references which are then sent to the internal control loops of paparazzi.