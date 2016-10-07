# JATT - Java Virtual Machine Auto Tuning Tool
___

## What is JATT?

JATT (Java Virtual Machine Auto Tuning Tool) is an open source software tool which
was developed to optimize the Java Virtual Machine (JVM). JATT is developed based
on the OpenTuner, another open source software framework to build domain specific
auto tuners. JATT is specifically designed to tune HotSpot JVM, one of the most 
commonly used JVM. Although JATT is primarily focused on HotSpot JVM, JATT source 
code can be easily extended to build an auto tuner specific to a different JVM 
implementation. JATT can be used in both Console mode and the Graphical User 
Interface mode(GUI) mode. But if you are using JATT for more advanced 
work (i.e. research, tuning advance java programs) we highly recommend you to 
use JATT in the console mode.

For more information please visit JATT website: 
https://sites.google.com/site/hotspotautotuner/

Currently JATT is compatible in linux environments only. 

To get started with JATT, first you need to install OpenTuner in your system.
You can install Opentuner by Visiting, http://opentuner.org/ 

We tested JATT with two benchmark suites:

* SPECjvm2008 startup benchmarks: To evaluate the startup performances in JVM 
* DaCapo benchmark suite: To evaluate the steady state performance in JVM
___

### Folder Structure Details

**BenchmarkPrograms**: Contains basic banchmarks coded by SapientS to test the JATT.
Note that these are not standard benchmarks. As standard benchmarks we have 
used SPECjvm2008 and DaCapo benchmark suites. 

**Common**: Contains some python scripts to read the opentuner database 
files and get the tuned configuration.

**Flags**: Contains the hierarchical flags structure developed for OpenJDK 
HotSpot Virtual Machine. This can be used to reduce the tuning time by 
eliminating the invalid search spaces.

**Hadoop_Default_Configurations**: Contains some files related with Hadoop 
tuning experiements. 

**Hotspot_JVM_Tuner**: Source folder of JATT in console mode. To Run JATT you 
need these folder as well as Opentuner installed in your system.

**Hotspot_JVM_Tuner_GUI**: Source folder of JATT in GUI mode. To Run JATT you 
need OpenTuner , Qt framework installed in your system

**Online_JVM_Tuner**: Contains the code related to Online tuner. Still under development. 

**TomcatTuner**: Contains all the Code Related to the tomcat server tuning using JATT. 

**opentuner-master**: Contains the Opentuner version that we are using. 

___

## Using JATT (Java Auto Tuning Tool) Console Tool ##

JATT Console mode is recommended for the research and further experimentation. All the source code related to the JATT console mode resides in the folder, **Hotspot_JVM_Tuner**. Currently JATT is compatible with Linux based operating systems only. In order to run JATT in your system you need to successfully install OpenTuner([http://opentuner.org/](http://opentuner.org/)) in your system. To install OpenTuner please follow the instructions in the OpenTuner website. After installing Opentuner you need to install python-pandas in your system. You can install it by 'sudo apt-get install python-pandas'. Note that old version of pandas might not support JATT. 

Java Virtual Machine: JATT is only tested with the Open JDK Hotspot VM only. So we recommend to use OpenJDK Hotspot VM in this installation.

In the **Hotspot_JVM_Tuner/src** contains the python file, jvmtunerInterface.py which contains the configuration manipulator and the run function (execute_program function) which can be overridden. Any domain specific or program specific tuner can be built by extending jvmtunerInterface.py file. 

For example we have developed the dacapoTuner.py and specjvmTuner.py files by extending jvmtunerInterface.py file which are used to tune the SPECjvm2008.startup benchmarks [https://www.spec.org/jvm2008/](https://www.spec.org/jvm2008/) and Dacapo benchmarks [http://www.dacapobench.org/](http://www.dacapobench.org/). Following images depicts the performance improvements that we gained using JATT for SPECjvm2008 startup programs and Dacapo benchmark suite. 

![A1_DaCapo_PI.jpg](https://bitbucket.org/repo/jbGgXj/images/1067470901-A1_DaCapo_PI.jpg)

Figure 1. Percentage performance improvements for the Dacapo benchmark suite. (Measures the steady state performances of the JVM)

![A1_SEPCjvm_startup_PI_1.jpg](https://bitbucket.org/repo/jbGgXj/images/2058958999-A1_SEPCjvm_startup_PI_1.jpg)

Figure 2. Percentage performance improvements for the SPECjvm2008.startup benchmarks (Measures the startup performances of the JVM).

In order to run the SPECjvm2008 tuner and Dacapo Tuner you need to install the benchmark code inside the src folder. In order to run the benchmark tuners you need to specify following parameters.

--source SOURCE       
source file/benchmark to tune (only give the benchmark name e.g: fop benchmark in dacapo  benchmark suite.)

--flags FLAGS
define flag combinations to feed separated by commas (E.g: bytecode,codecache,compilation,compiler,deoptimization,gc,interpreter,memory,priorities,temporary) default it is set to use all the flags of JVM. But you can specify and limit the tuning procedure to use gc,compiler,compilation etc


**TunedConfiguration** contains files that stores the good configurations that the JATT has tried. 

**Flags** Contains the HotSpot VM flags structure which will be used in the configuration manipulator in jvmtunerInterface.py.
___

## Developers ##
* Milinda Fernando (milinda.10@cse.mrt.ac.lk)
* Tharindu Rusira (tharindurusira.10@cse.mrt.ac.lk)
* Chamara Phillips (chcphilips.10@cse.mrt.ac.lk)
* Chalitha Perera (chalitha.10@cse.mrt.ac.lk)

##Project Supervisors##
* Prof.Sanath Jayasena (sanath@cse.mrt.ac.lk)
* Prof.Saman Amarasinghe (saman@csail.mit.edu)

___
If you have any problems please contact,
* Milinda Fernando (milinda.10@cse.mrt.ac.lk)
* Tharindu Rusira (tharindurusira.10@cse.mrt.ac.lk)

___