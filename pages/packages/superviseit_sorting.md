@page superviseit_sorting Supervise It! Placement Studies


### Pilot Sorting Study

The pilot study will record a ROS bag, but will also hopefully process 
in real time the video data to generate user level measures for statistical
analysis.  It will consist of a pool region pieces and three or four sort
regions.  Puzzle pieces will be placed in the pool region and must be moved to
their assigned sort regions.

Each participant has to perform the sorting task several times.  All tasks
per participant will be a single sitting, from which the breaks must be
determined.

The supervisory system will observe where the pieces were placed, keep track of
what sort region they were placed in, and the user activities/timing.  A marker
will be used to signal termination of a study run, with marker removal
indicating commencement of the next study run.  

Termination perhaps should be done at the comman line (hit 'q' style).
The suggested alternative to signal termination is to place a different marker
(other color) in same place, or same marker in a different place.

#### Pilot: Calibration

The core calibration files will be hosted in the Mary (the Puzzlebot)
repository, as it is core puzzlebot code.  Expected calibration for Mary
includes:
- Workscene calibration (black mat, glove, planar workspace).
- Zones calibration (pool and sort regions)
  - First clicked point should be the pool region.  Rest sort regions.

The implementation will use the Workscene perceiver, an activity regions
monitor add-on, and reporters for the regions.

If run at GT and UCF, then the calibration files should differentiate via `GT` and `UCF` prefixes.


#### Pilot: Execution

To run the sorting pilot involves execution code in the `supervise-it` repo,
within the `Pilot_Sorting` folder.

> ./run_sorting_pilot

It will load the calibration files and save the data in the `supervise-it` data
folder (`Sorting` sub-folder).

