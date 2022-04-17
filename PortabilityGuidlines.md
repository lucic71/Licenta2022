Lyon's [paper](https://akapugsblog.files.wordpress.com/2018/05/inter-unix_portability.pdf)
gives some insights about the challenges of porting Unix C code from PDP-11 to Interdata 8/32.
At the end he proposes guidelines for portability, they are quite old and it seems to me that
it's common sense to apply them nowdays. Here are some of the guidelines:
  * don't use machine dependant tricks
  * use header files for modularity
  * use meaningful names for constants
  * use new features as typedef and sizeof
  * don't duplicate code
  * use a linter (now that's a good one)

I mean.. everybody uses these guidelines when writing code, even if they don't have portability
in mind. It seems that programming was very different back then, maybe because of the limited
resources or because they didn't take into account the fact that the code might be reused
sometime in the future or because the software processes were not formalized and everybody
did the job in their own way.

45 years later, I shall give my own portability (or porting?) guidelines based on the experience of porting
IM et al.:
  * document _each step_ of the porting process from the beginning (porting)
  * avoid unportable build systems (portability)
  * avoid fancy tricks in build script, eg the problems we had with the tarballs (portability)
  * document the build scripts with comments as it's tedious to read hundreds of lines of commands (porting)
  * prefer a top-down approach when porting the code (this clearly needs some explanations) (porting)
  * write scripts for preparing the new environment (the code will be tested hundred of times,
  you dont' want to make boring work in this process) (porting)
  * don't waste time understanding every component of the systems, if it works go to the next one and
  come back when there are problems (this might sounds controversial) (porting)
  * make the system work in the new environment by any means (even if they are clumsy) then think about ways
  to make the ported parts prettier (porting)
  * avoid using unportable code, eg boost problem (portability)
  * avoid using code that just works™, eg ifdefs with code that doesnt compile on else branch (portability)
  * don't create hard dependencies on one environment, eg proc entries from ixia kernel (portability)

Maybe these steps will become self evident 45 years in the future. That makes me think about the fact that
porting/portability did not even reach their adolescence. We don't have anything that resembles a mathematical
model of porting, the only way of doing porting is based on the experience of others and about our experience
on working with software. I don't even know if other software processes have a mathematical model or what this
mathematical model should look like. I'm just guessing and writing my random thoughts.
 
At the end of the day, the IM et al. code was very portable. We modified code only in the areas where
functional inconsistencies appeared (not communicating correctly with IxServer) or where we needed to
add macro definitions for the new architecture. The rest of the code compiled successfully with the
ARM toolchain.
