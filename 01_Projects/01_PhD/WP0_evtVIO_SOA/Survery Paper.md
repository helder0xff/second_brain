# Event-based Simultaneous Localization and Mapping: A Comprehensive Survey
# Feedback
- 2/5
- Too shallow
# DOI
https://doi.org/10.1007/s11263-026-02845-9
# Notes
## Paper Structure
![[Pasted image 20260919192934.png]]

## Event Camera Working Principle
- Event Generation Model (EGM): events are triggered when de percentage of the **last stored memory** and the **newest sampled** differ in a percentage that is greater than a given threshold (**contrast sensitivity**).
![[Pasted image 20261018103910.png]]
- C is usually set betwee 10 and 15%.
## Event Representation
- **Individividual events:** this are filtered based methods (that seem to be the most computationally demanding
- **Event packets:** packets of individual events.
- **Event frames**: several variants, such as one channel per polarity, just summing up events, summing positive and substracting negative events, ...
- **Time surface**: a 3D representation of a timestmp per pixel. Usually the most recent timestamp of the trigger.
- **Motion compensation event frame**: warped event data using a motion model to align events. Sesitive to the motion model.
- **Voxel grid**: our tensors. A bunch of short term images.
- **Reconstruded images**: event data to brightness images. Useful to restore brightness information in HDR conditions.
## Feature-Based Method
Two main components on vSLAM methods:
1. Feature extraction and tracking
2. Camera tracking and mapping
In the feature extraction method, **invariant** features (to movement, light, noise, ...) are identified. Then, those invariant featres are tracked from sample to sample. Two main dind of features:
- Point features
- Line features
### Feature Tracking (this merge with Camera Tracking too)
1. Identify robust features in sample one
2. Indentify the same features in sample two
3. Build a translation/motion model
4. Use/invert that model to see how the cam has moved.
## Camera Tracking (and mapping)
- Optimization methods: using event frames.
- Filtered Based Methods: process event data asynchronously
### Filtered based Methods (the ones I am interested in)
The system keeps an stimation of the camera poses and updates it continuously with event based. This data is being input asynchronously as it comes.
The filter filter state is the current camera pose (and more, like location, speed, IMU data if any, ...). The fitler updates its state as data comes.
The motion model use to be a random diffusion model as we do not know where the object might be moving.
The new state is predicted using the motion model and corrected using the error measurement (from the input asynchronous data).
## Datasets
- **MVSEC**: Zhu, A. Z., Thakur, D., Özaslan, T., Pfrommer, B., Kumar, V., & Daniilidis, K. (2018). The multivehicle stereo event camera dataset: An event camera dataset for 3d perception. IEEE Robotics and Automation Letters, 3(3), 2032–2039. [https://doi.org/10.1109/ LRA.2018.2800793](https://doi.org/10.1109/LRA.2018.2800793)
- **vicon**: Guan, W., Chen, P., Xie, Y., & Lu, P. (2023). Pl-evio: Robust monocular event-based visual inertial odometry with point and line features. IEEE Transactions on Automation Science and Engineering, 1–17. [https://doi.org/10.1109/TASE.2023.3324365](https://doi.org/10.1109/TASE.2023.3324365)
- **UZH-FPV**: Delmerico, J., Cieslewski, T., Rebecq, H., Faessler, M., & Scaramuzza, D. (2019). Are we ready for autonomous drone racing? the uzhfpv drone racing dataset. In 2019 International Conference on Robotics and Automation (ICRA), (pp. 6713–6719). [https://doi. org/10.1109/ICRA.2019.8793887](https://doi.org/10.1109/ICRA.2019.8793887)
- **TUM-VIE**: Klenk, S., Chui, J., Demmel, N., & Cremers, D. (2021). Tum-vie: The tum stereo visual-inertial event dataset. In 2021 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), (pp. 8601–8608). [https://doi.org/10.1109/IROS51168.2021.9636728](https://doi.org/10.1109/IROS51168.2021.9636728)
## Miscelanea
- **Filter-based methods:** direcly process raw data - computationally expensive
- **Aggregate methods:** event-frames.
