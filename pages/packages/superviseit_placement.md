@page superviseit_placement Supervise It! Placement Studies


### Pilot Study

The pilot study consists of ROS bags, with one per participant.  Each
participant had to perform the placement task several times.  All tasks per
participant are recording in a single ROS bag, from which the breaks must be
determined.

#### Pilot: Calibration


This is what I forgot how to do.  There is a python script
`calibrate_firstframe_bycolor` that appears to do some of the work based on the
first frame from the ROS bag.  First it recovers the black mat, then asks for
user input to get the puzzle piece regions.
