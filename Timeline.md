# 05.07 - 09.07

Status
  * surveyed build system
  * identified internal and external dependencies
  * built IM + libim + HostProxy for ARM64
    * deployed in qemu
    * IM and HP throw errors that must be investigated

Planning
  * configure multinic B2B topology in QEMU
  * investigate IM and HP crashes
  * separate IM from IxOS in a new git repository
  * document the compilation flags

# 12.07 - 16.07

Status
  * compiled IM with IX_SOFT_PORT => triggered ixtcp compilation
  * get plugin faliures for IM after solving crashes

Planning
  * make git repo with everything
  * fix IM boot issues
    * plugins: libsstream, libixvm, etc
    * ethtool
    * pwatchdogd
    * ixrte exception
  * build ixstack infrastructure
    * ixnam, ixtcp, ixrte
  * configure multinic B2B topology in QEMU
  * fix build issue with ixtcp headers and ixrte
  * find out how to make new CEGL

# 19.07 - 23.07

Status
  * git repository is up
  * built libstatmanager
  * ordered RPi hardware

Planning
  * fix IM boot issues
  * deploy vChassis for use with RPi
  * make hardware setup
    * make infrastructre to write RPi IP to a remote machine
  * find out how to make new CEGL

# 26.07 - 30.07

Status
  * plugins imported in IM: libPGID, libsstream

Planning
  * fix IM boot issues
  * deploy vChassis for use with RPi

# 02.08 - 06.08

Status
  * IM is booting, having config issues
  * created RPi setup
  * deployed RPi + vChassis + IxExplorer setup
    * port is visible from IxE but we have issues with link state
      * maybe there is a problem with published stats
  * attempted connections from vChassis to vCard
  * ran into configuration issues
  * need to trick the vChassis into beliving that we're on x64

Planning
  * fix port down/hwfault report from IM
    * trick the chassis into beliving we're legit IxVM
    * make HostProxy - chassis connection

# 10.08 - 13.08

Status
  * checking xmls between vChassis and IM
    * IM doesn't seem to be handling ixvm-config requests properly
  * disable license check on vChassis
    * pkgget taking a long time (while rebuilding vChassis?)
  * need to rebuild vChassis code

Planning
  * make RPi setup in lab
  * check stats bring-up (required for link state)
  * check if there is docs about the communication between vchassis and vcard

# 17.08 - 20.08

Status
  * debugging init-time IM issues
  * recompiled libsstream, flowdetective and libPGID
  * need to test

Planning
  * debug init-time IM issues
  * load protocol layers

# 23.08 - 27.08

Status
  * sturgling with flowdetective build on ARM64
  * trying to recompile FD using an older c++ standard
  * we know what the issues is, not trivial to solve, migrating to new boost
  might not help
  * try to isolate the problem
  * get we get a FD stub if the problem is hard to solve? can we modify FD?
  * symbols from boost are missing because of header vs code version mismatch,
  need to try to build boost 1.51

Planning
  * debug init-time IM issues
    * libsstream done, libPGID in progress (depends on FD, which fails with
    weird template error)
  * pkgget issues regarding ARM64 files (what is the matter with this pkgget?)
  * build boost 1.51 for ARM64
  * create rpi fault tolerance scripts
  * write project documentation
  * load protocol layers

# 30.08 - 03.09

Status
  * all plugins are loaded now, need to test with IxE
  * IM is booting but port is not showing link state up
  * write documentation, return at debugging in a couple of days
  * getting a reference for correct IM initialization
    * get a x86_64 IM + IxStack setup
    * look at standard IxVM setup for reference

Planning
  * continue to write documentation

# 06.09 - 10.09

Status
  * make Rustic setup
  * still having IM on rpi boot issues, vCard setup going down
  * rustic setup failed, solve IM on rpi boot issues
  * working on im+ixstack init issues on rpi
  * unclear why ports are not showing link state up

Planning
  * architectural diagram for the project

# 13.09 - 17.09

Status
  * ports still now showing green in IxE, we're likely running into an issue
  with stats
  * made progress understanding stats, trying to understand why "ports not
  ready"
  * takes a long time to compile IxS, meanwhile working on docs

Planning
  * debug stats

# 20.09 - 23.09

Status
  * ports are up in IxE (DoD issue, but we don't have DoD on RPi so we hacked
  IxS

Future work
  * rpi fault tolerance scripts
  * load protocol layers

# Project milestones {#proj-milestones-anchor}

* separating IM from IxOS in new git repository
* running IM in QEMU
* running IM in lab setup
* build protocols for ARM64
* performance testing

# Porting tasks by Tanaka et al.

* Advance preparations
  * Surveying development environment
  * Surveying OS
  * Surveying program for porting
  * Adjusting WS development environment
  * Adjusting target environment
  * Initial source code modifications (i don't know what to say about this..)
* Workstation testing (this seems to be what we did in qemu)
  * Standalone testing on WS (tesing per modules/units)
  * Linked testing on WS (testing the program as a whole)
* Target testing (this does not take into account cross-compiling)
  * File-making
  * File system creation (is this still relevant?)
  * Installation on target
  * Test program creation
  * Linked test on target
* General duties
  * Documentation
    * changes made to source code
    * porting impediments that are "hacked" must be revised
  * Progress tracking
  * Discussions

## Our specific case: porting IxOS

* Advance preparations
  * Surveying development environment
    * 05.07 - 09.07
  * Surveying OS
    * 02.08 - 06.08 (when ran into /dev/kmem issues)
  * Surveying program for porting
    * 05.07 - 09.07 (surveyed the dependencies)
  * Survey documentation
    * 30.08 - 10.09 (get a reference for correct IM initialization)
  * Adjust versioning system
    * 19.07 - 23.07
  * Adjusting WS development environment
    * 05.07 - 09.07
  * Adjusting target environment
    * 02.08 - 06.08
  * Initial source code modifications
* Building for target system
  * File-making (this includes modification to build system)
    * 05.07 - 06.08
    * 17.08 - 27.08
  * Installation on remote env (WS or target)
    * 05.07 - 20.08
    * 30.08 - 03.09
  * Reviewing inconsistencies between source and remote envs
    * 05.07 - 20.08
    * 30.08 - 17.09
  * Solve problems with external libraries
    * 23.08 - 27.08
  * Test program creation (deploying vCard+vChassis+IxE)
    * 02.08 - 06.08
    * 10.08 - 13.08 (solve problems with deployment: license, vChassis rebuild)
    * 20.09 - 23.09 (solve problems with deployment: dod in vChassis)
* Workstation testing
  * Standalone testing on WS
  * Linked testing on WS
    * 05.07 - 30.07
* Target testing
  * Standalone testing on target
  * Linked test on target
    * 02.08 - 20.08
    * 30.08 - 03.09
    * 20.09 - 23.09
* General duties
  * Documentation
    * 30.08 - 03.09
    * 13.09 - 23.09
  * Progress tracking
    * each week
  * Discussions
    * each week

Note: I use the term "remote" to describe the system on which the ported program
will run, the term "target" is already taken in this context.
Note:
  * standalone testing - unit/module testing
  * linked testing     - whole program testing

### Most time consuming porting tasks

Based on the number of weeks these are the most time consuming porting tasks:
  * Reviewing inconsistencies - 10 weeks
  * Linked testing (WS + target) - 9 weeks
  * Installation on remote env - 8 weeks
  * File making - 7 weeks

We did not reserve a whole week for a single task. During a week we did a total
ammount of 4-5 porting tasks (this is a rough esitmation). So a better approach
would be to further sort the above tasks based on their difficulty:
  * Reviewing inconsistencies - 10 weeks
  * Linked testing (WS + target) - 9 weeks
  * File making - 7 weeks
  * Installation on remote env - 8 weeks

To be honest, installing the binaries on the remote env was not such a big deal,
we had to issue scp(1) that lasted at most 5 minutes, depending on the network
speed.

### Critique to Tanaka's porting model

Why is there a need to include "initial source code modifications" in Advance
preparations stage? I would expect this to be the first phase of the porting
process where the team tries to understand the requirements and the
peculiarities of the parts involved in porting: dev env, OS, program, target
env, documentation and versioning system. After the team discusses and has an
understanding of how the porting process should look like, they can create
a roadmap of the porting process. It's foolish to assume that they can make
modifications right from the beginning. Now that I mentioned the word "roadmap",
I think this should be a sub-task in Advance preparations too. Me and LucianM
(mostly LucianM) did this in [Project milestiones](#proj-milestones-anchor).

Note on the above paragraph: After reading this article [I ported the new Hare compiler to OpenBSD](https://briancallahan.net/blog/20220427.html)
it seems that the "initial source code modifications" stage really makes sense.
In the "Getting started" section Brian explains that he had to do some
modifications in order to match the errno and syscall conventions from OpenBSD.
After that he explains in "The first build errors" the "Building for remote
system" stage described below.

Workstation testing should follow the same sub-task as target testing, the
only difference being that the "linked test on target" should be changed to
"linked test on WS". For this to happen I propose to change this structure:
  * Workstation testing (this seems to be what we did in qemu)
    * Standalone testing on WS (tesing per modules/units)
    * Linked testing on WS (testing the program as a whole)
  * Target testing (this does not take into account cross-compiling)
    * File-making
    * File system creation (is this still relevant?)
    * Installation on target
    * Test program creation
    * Linked test on target
to the following structure:
  * Building for remote system (this is not the best title)
    * File-making (this includes modification to build system)
    * Installation on remote env (WS or target)
    * Reviewing inconsistencies between source and remote envs
    * Solve problems with external dependencies (libraries mostly)
    * Test program creation (this should be renamed to: create testing
    infrastructure)
  * Workstation testing
    * Standalone testing on WS
    * Linked testing on WS
  * Target testing
    * Standalone testing on target
    * Linked test on target

Is it relevant to mention that we also test our to-be-ported program in a WS
(which is a terrible name btw) environment? I would say yes because working
with simulators and emulators is critical when you don't have available
hardware or when the costs of testing on hardware are too high. On the other
hand for a to-be-ported application there should be no difference between
a simulated/emulated environment and a "real" environment.

My last point in this critique is the following: I is it relevant to mention
file system creation? Shouldn't the OS handle this task or do I miss something
essential about systems programming from the 90's? I would say it's the second
point, the authors should have a strong reason for separating "file system
creation" from "adjusting target environment". Some other valid option would
be that I don't understand what "file system" means in this context and I should
read more carefully the paper.
