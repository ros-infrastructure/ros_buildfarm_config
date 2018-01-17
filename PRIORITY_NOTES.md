This file contains some notes on the Jenkins job priorities that are configured in this repository.

The ROS buildfarm is currently setup with a Jenkins plugin that manages job priorities.
The priorities are inverse numerically based; that is, a lower number means a higher priority.
As of this writing, the buildfarm is configured to have a range of 1 to 99.
There are periodic maintenance jobs that use priorities 1 to 39, thus those priorities should never be used for distribution jobs.

There are currently 6 classes of distribution jobs that the buildfarm runs.
Within each class, the ROS distributions should be in release order (newest ROS release has highest priority).
To make it so that we don't have to change the priorities on every release, we have defined some ranges for the classes, listed in the table below:

| Job Type                     | Numeric Range |
| ---------------------------- |:-------------:|
| Pull Request                 | 40 - 49       |
| Commit                       | 50 - 59       |
| Source                       | 60 - 69       |
| Basic Binary (x86/amd64)     | 70 - 79       |
| Documentation                | 80 - 89       |
| Extended Architecture Binary | 90 - 99       |


To add jobs for a new distribution, find the newest currently existing distribution within a class, subtract one from the priority, and set that to the priority for the new distribution.
For instance, assume we want to add a Pull Request job for N-Turtle to the list of distributions.
Further assume that the Pull Request job for M-Turtle has priority 55.
Therefore, the Pull Request job for N-Turtle would be 54.
The current list of priorities can be assessed by running the `list_priorities.py` program from the top-level of this repository.
