rgbd_to_pointcloud  generate scenen pointcloud or camera frame pointcloud using rgb depth png from 360 camera run


sam3/sam3.py put sam mask in folder for each rgb for a given folder containing rgb depth and pose


glass_killer.py test critic, given a critic and mask folder, randomly generate plane for critic


pose convention for reconsetruction: poses.csv is camera/pose in world, with quaternion order qx qy qz qw (xyzw).
Depth reconstruction points are in optical camera frame.
Before applying pose, you must rotate depth frame to pose frame using:
depth_to_pose = ros_optical_to_link
Then transform to world with:
xyz_world = R_pose * xyz_pose + t_pose
So your correct world command is the same as before, plus this key flag:

--depth_to_pose ros_optical_to_link
And only add this if needed:

--pose_is_w2c (only if your CSV is world-to-camera, which yours does not appear to be).