# Costs for porting IxOS testing infrastructure

## Stages

1. Build binaries for ARM64
  * separate IM + HostProxy from IxOS infrastructure
  * integrate IxStack with IM
  * build plugins for IM
  * test initial builds in QEMU
2. Emulate vCard on RPi
  * run setup on RPi hardware
  * hack IM to work properly
  * send stat requests to ixStatDaemon to check if the stats are working
3. Bring up ports on vChassis
  * check where the link state gets assigned to kVirtualModuleNotReady
  * track the path to link state = kUp
  * solve the DOD problem that generated our link state issue

## Costs

1. Build binaries for ARM64
  * understand the architecture described in the build scripts
  * keep in mind that the build scripts were written in SCons which needed
  python2 support (Debian 10 came with python2 out of the box)
  * IxStack is not fully understood up to this day (I don't understand its
  components and the various config modes)
  * the toolchain had missing definitions, we needed to solve them in order to
  continue
  * unexpected costs: had to port some more plugins and libraries that were
  not estimated
  * qemu did not come cheap. it was more accessible than the rpi hardware but
  it was dead slow
2. Emulate vCard on RPi
  * we had to prepare the prepare the environment for IM to work (create pipes
  and config files)
  * before putting the RPi in the lab we had to work with a clumsy
  configuration (vChassis in VBox, RPi connected to the computer running the
  vChassis => problems with connectivity and license server)
  * unexpected costs: dmidecode did not work on RPi => hardcoded vCard UUID
  * had to patch sstream for our usage
  * if i remember correctly there was an issue with system libraries, python
  system libraries for ARM more exactly. i had to download deb packages
  manually and patch them into the system so that IM would work correctly.
  I remember: these packages were needed when building ixvmrxtx or something
  like this (I think sstream was part of ixvmrxtx)
3. Bring up ports on vChassis
  * the vCard was not visible from IxE => we had to investigate and modify the
  code in IxServer
  * the problem was hard to debug, we tried to investigate some paths that led
  to nowhere (ixStatDaemon)
  * the code was hard to debug (coding style was great, but it was huge)
  * we did not have time to patch the vCard to solve the problem

## Metacosts

* there is no easy way to understand the system => complicated architecture
diagrams, huge code base, unfamiliar versioning system
* not understanding the system costs. it costs time to ramp-up. that time can
be well spent in porting the system
* tools. using outdated tools and systems means that one must spend additional
time in order to figure out things that may otherwise be already solved by
someone (assuming there is a community around an up-to-date tool or system)
* documentation. lacking written information about how the system works means
that one either must figure out the system by oneself or must communicate with
others in order to gather info about the system, which, of course, costs time
* changing the environment. extracting a component from the environment it was
designed for, putting it in a new environment and expecting it to work is not
a good tactic (btw this is the reason why porting costs). we had a lot of
networking problems when we deployed IxServer in VBox and IM in qemu
* unexpected costs. these are the most unpleasant because they corrupt all the
previous evaluations about the porting costs. see boost bug, dmidecode and dod
problem in IxServer for example
* performance costs. we did not have problems with this one but it is worth
noting as this can be a difficult problem to solve
* solving incosistencies between environments
* trying to understand the culture around the project. this is a
meta-meta-cost :). i guess it is important to have an answer for questions
as: what was the reasoning behind this component?, is there a reason for
choosing this programming language? it's not clear yet what are the advantages
of answering these questions, but having answers for them would surley help
the person trying to port the system to familiarize and understand better the
system

# A study of Software Portability Evaluation

This paper proposes a model for estimating software porting cost based on
program characteristics and the factors hindering a program from being ported.

Software porting usually consists of the following processes:
  * investigation
    * destination system (hardware and OS)
    * program to be ported
    * development environment
    * testing environment
  * source program modification
  * file making
  * unit test
  * system test
  * documentation
  * misc

While porting cost (man-hours) is chiefly determined by PTBP size, PTBP
contents, and porting impediment factors, the porting environment is also
important.

Porting impediment factors:
  * system environment disparity
  * program factors (These factors depend on the extent to which portability
  was taken into account when the PTBP was written.)

Porting cost factors
  * human factors (experience of the programmer)
    * knowledge of
      * ptbp functions and structures
      * hardware and OS of target
      * porting process
      * language of ptbp
      * usge of tools in dev and test envs
  * environmental factors (tools and test programs)
    * development environment
    * unit test environment (NA)
    * system test environment

Porting impediment factors:
  * differences in processor architecture (not really a problem for us)
  * OS disparity (problems: /dev/kmem, proc entries)
  * differences in language processor
    * toolchain (needed to be a little bit modified)
    * library support (hard problem to solve: boost)

Portability impediment index: sum of each impediment multiplied by the degree
of portability.

Human factors & environmental factors index: sum of human and environmental
impediments.

There is a regression equation for evaluating the cost required for porting
(shame on me that I don't fully understand terms as "multiple correlation
factor", "variance ratio" or "analysis of variance").

There is a porting productivity index that will be useful for us, I think.
(still, too complicated to understand it easily)

Finally, there is an equation for estimating porting costs.

"Software conversion is generally viewed in the Federal ADP
community as a traumatic and disruptive experience, to be avoided as
long as possible, endured when necessary, and forgotten as quickly as
possible." [https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nbsspecialpublication500-105.pdf](Guide to software conversion management)
