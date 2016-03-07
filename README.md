ros_buildfarm_config
====================

The configuration for the ROS buildfarm available under http://jenkins.ros.org.

The `master` branch is from where we run our testing farm and is the recommended place to fork from. 

The `production` branch is what we actually run on http://build.ros.org Please do not fork from that version as it does things like turn on maintainer emails which are not appropriate for a private fork. Doing that will cause maintainers to get emails both from the main buildfarm run by OSRF, as well as duplicates from any private buildfarm which is running.

The two branches should be maintained as closely as possible. 

To deploy a custom buildfarm using this configuration you might want to use the
[ros_buildfarm](https://github.com/ros-infrastructure/ros_buildfarm)
repository.
