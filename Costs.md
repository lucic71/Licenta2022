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
  * qemu did not come cheap. it was more accessible than the rpi hardware but
  it was dead slow
