ros_buildfarm_config
====================

The configuration for the ROS buildfarm available under http://build.ros.org.

The `master` branch is from where we run our testing farm and is the recommended place to fork from. 

The `production` branch is what we actually run on http://build.ros.org Please do not fork from that version as it does things like turn on maintainer emails which are not appropriate for a private fork. Doing that will cause maintainers to get emails both from the main buildfarm run by OSRF, as well as duplicates from any private buildfarm which is running.

The two branches should be maintained as closely as possible. 

To deploy a custom buildfarm using this configuration you might want to use the
[ros_buildfarm](https://github.com/ros-infrastructure/ros_buildfarm)
repository.

#Contributing guidelines

## Branch hygiene
Be careful about which branch you fork from and submit a pull request to.

If you are contributing a configuration change (e.g. changing the values of keys) to be deployed on build.ros.org, make a pull request to the `production` branch.

If you are contributing a change to be deployed on the testing farm or a more structural change, make a pull request to the `master` branch.

##Guide to blacklisting packages

If you wish to blacklist a package on build.ros.org, submit a pull request to `production` doing the following:

Find the `release-build.yaml` file which is appropriate for the platform you wish to blacklist your package for under the folder for the appropriate distribution.

For example, if you want to blacklist a package on 32-bit ARM in Kinetic Kame, you want to edit the file `kinetic/release-armhf.build`.

Add the name of the package to blacklist under the entry `package_blacklist`, e.g.

```
  package_blacklist:
    - my_blacklisted_package
```

When you submit a pull request, please *open a ticket* in `ros_buildfarm_config` or the repository for your package describing why you are blacklisting your package, and link to that ticket in your pull request to blacklist the package.

If you never want your package to be unblacklisted, you don't need to do this, but if you are waiting on a system dependency to be released or updated, then you should state that in the ticket/in your pull request and, if you can, link to an external issue tracker related to the problem.
