openFABMAP
==========

Open Source C++ Code for the FAB-MAP Algorithm

See the [Wiki](https://github.com/arrenglover/openfabmap/wiki) for tips!

version 2.03

### *Now Supporting OpenCV 3.0*

```
@inproceedings{
   author = {Glover, A. and Maddern, W. and Warren, M. and Reid, S. and Milford, M. and Wyeth, G.},
   title = {OpenFABMAP: An Open Source Toolbox for Appearance-based Loop Closure Detection},
   booktitle = {The International Conference on Robotics and Automation},
   address = {St Paul, Minnesota},
   publisher = {IEEE},
   year = {2011}
}
```

OpenFABMAP [Glover et. al. 2012](http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=5509547&tag=1) is an open-source, OpenCV-only dependent, version of the popular Fast Appearance-based Mapping (FAB-MAP) algorithm [Cummins & Newman 2008](http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=5509547&tag=1 Glover et al. 2010). OpenFABMAP was developed from the ground-up following FAB-MAP publications. The original FAB-MAP algorithm is now also [open-source](http://www.robots.ox.ac.uk/~mjc/Software.htm) but requires alternative project dependencies. 

FAB-MAP is a Simultaneous Localisation and Mapping algorithm which operates solely in appearance space. FAB-MAP performs location matching between places that have been visited within the world as well as providing a measure of the probability of being at a new, previously unvisited location. Camera images form the sole input to the system, from which OpenCV's feature extraction methods are used to develop bag-of-words representations for the Bayesian comparison technique. 

The code has implementations of
 * Feature Detection, Feature Extraction, and Bag-of-words models using OpenCV
 * Chow-Liu tree implementation
 * FAB-MAP v1.0 [Cummins & Newman 2008](http://ijr.sagepub.com/content/27/6/647.short Cummins & Newman 2008)
 * FAB-MAP v1.0 using a Look-up-table for improved computation speed
 * FAB-MAP with Fast-Bailout [Cummins & Newman 2010](http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=5613942)
 * FAB-MAP v2.0 [Cummins & Newman 2010](http://ijr.sagepub.com/content/30/9/1100.short)

An overview of OpenFABMAP [Glover et. al. 2012](http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=5509547&tag=1) or the original implementation/use [Glover et al. 2010](http://eprints.qut.edu.au/50317/1/glover_ICRA2012_final.pdf).

As of the latest version, openFABMAP is dependent solely on [OpenCV 2.3](http://opencv.org/) or higher.  The project has a [CMake](http://www.cmake.org/) build environment for general use on both Linux and Windows systems. OpenFABMAP is also designed to integrate with [ROS](http://www.ros.org/wiki/). See the [CyPhy-ROS](https://wiki.qut.edu.au/display/cyphy/cyphy+ROS+wiki+page) page for a package that has implemented openFABMAP as a ROS node.

Check out the GitHub Wiki for some instructions and tips on running openFABMAP.

The original googlecode project page was [here](http://code.google.com/p/openfabmap/)

#Installation


Linux (g++)

1. install cmake `sudo apt install cmake`
1. install opencv `sudo apt install libopencv-dev`
1. get the openFABMAP code `git clone https://github.com/arrenglover/openfabmap.git`
1. make the build directory `mkdir openfabmap/build && cd openfabmap/build`
1. use cmake to compile the makefile `cmake ..`. *note: the output will tell you which version of opencv you are using and if you are using the "non-free" modules*
1. make the project `make`
1. view/modify the settings file `gedit ../samples/settings.yml`
1. run the command line tool `bin/openFABMAPcli -s ../samples/settings.yml`

Windows (Visual Studio 2008)

1. install [openCV2.3](http://opencv.willowgarage.com/wiki/)
2. install [cmake](www.cmake.org/)
3. open the cmake gui, specify the source directory (the directory this README is in), a build directory for the code, and click configure
4. you may have to specify the location of opencv2.3 in UngroupedEntries->OPENCV_PATH.
5. click configure in the cmake gui again
6. click generate
7. open the visual studio solution, for default running right-click on openFABMAPexe project and select 'Set as StartUp project'. Compile openFABMAP within Visual studio.
8. add required .dll files from openCV2.3 to your build/bin directory (respective debug versions for debug mode).
9. you also may need an extra tbb .dll due to OpenCV bug which can be downloaded [here](http://threadingbuildingblocks.org/ver.php?fid=171)
10. under openFABMAPcli->properties->Debugging->command arguments specify the path to the settings file (e.g. "-s samples\settings.yml")
11. Alter the settings file for your data
12. run exampleopenFABMAP in your build/bin directory (respective debug versions for debug mode).

