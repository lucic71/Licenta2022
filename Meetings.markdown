# 2022 January 4th, Diploma meeting #9

- January 29th -- session starts
- We have:
  - Preliminary structure
  - Abstract
  - List of contributions
- We don't have:
  - Title:
  - System name:
  - Evaluation using IxOS
  - Evaluation using IxNetwork/some other infrastructure
	- Would add another subchapter to architecture
  - LaTeX/git/something collaborative
- Short term plan: title, intro

# 2022 January 11th, Diploma meeting #10

- Short term plan: title
- Review literature on portability -- from OS, software engineering perspective
  - Tanenbaum's paper is a good starting point
  - Deliverable: a set of papers discussing the problems
  - Can we find a better (??) description of the problem domain?

# 2022 February 1st, Diploma meeting #11

- LucianP in exam session
- LucianP will start writing intro or background/related work
- Looked over portability literature from Lucian
  - We have a starting point for background and related work
  - There is little academic work on this, but plenty of web articles

# 2022 February 15, Diploma meeting #12

- LucianP in exam session until end of week
- Semester 2 starts on Feb 28
- 3 July - diploma project must be ready
  + Estimated finish time, June 27
  + 15 weeks of work
- Discussion on paper/thesis structure
- Discussion on why portability is important; and problems related to
  portability
- RD Timeline
  + 28 Feb - start work
  + March 31 - report 1 (document + slides)
  + May 5 - report 2 (document + slides)
  + May 30 - final draft

# 2022 February 28, Diploma meeting #13

- LucianP started working on structure, abstract rework
- LucianM needs to set milestones, no update here
- First order of business: abstract
- Good idea to go through re-review all the articles on next session
- Code work
  + One idea: porting the project to Cosmin's repository
	+ Recompile mini-IM on ARM64
	+ Deploy mini-IM to ARM64
	+ Would be nice to get an opinion/estimate from them regarding effort to port protocols to new IM
	+ Would decouple IM from IxOS
  + The other idea: reusing the code from internship to evaluate (performance, mostly)
	+ Redeploy
	+ Fixing boot issues/bugs (if there are any left)
  + Start with "the other idea" first, since it's code we own
  + Diff with Perforce code?
- Software engineering -- what is the process?
  + "Development" -- writing a new component, integration, porting, documentation, ???

# 2022 March 7, Diploma meeting #14

- Status
  + Have an abstract
  + Intro taking long
- Planning
  + Continue writing
  + Look at Eftime et al., https://www.scientificbulletin.upb.ro/rev_docs_arhiva/full7b9_553681.pdf and other papers on porting
- LucianM: read papers, subscribe to commits in repo

# 2022 March 14, Diploma meeting #15

- Status
  + First draft of intro done
  + Started writing background
- Planning
  + LucianM to look at background
  + LucianP: think about figures

# 2022 March 21, Diploma meeting #16

- Status
  - Returning at Uni (almost) fully physical
  - Writer's block :)
- Planning
  - Outline structure for chapters, based on discussion
  - Ask questions
  - Restructure, rewrite
  - Explore?
- Background/State of The Art
  - Background: context, terminology (definitions), all the notions that you use to write the paper
  - State of The Art: what others have done, where they've failed
  - What is the problem?
  - What is porting?
    - What is a (software, hardware) environment?
    - Multiple things mean "porting"
    - Porting versus rewriting ---> code reusability
      - How much do I need to rewrite?
    - A project is "portable" if most (??) of its code is reusable???
    - A project might simply *facilitate* portability
      - C language and compilers, POSIX, emulators
  - What is portability?
    - Measure of cost of porting: portability is inversely proportional to cost of porting -- there are papers that attempt (and succeed, to some degree) to evaluate this
  - Are there "standard" methods of porting software?
    - The methods are specific to the software and its (source, target) environments
  - Is portability/porting a solved problem?
    - Is there a systematic method to optimize the process of porting?
  - "Portability by design" -- can a project be designed so as it's portable?
    - We have a few guidelines for this
      - Use a portable language (C, C++, ...)
      - Adhere to standards (POSIX) -- many operating systems/compilers/libraries have non-standard features
      - Problems
        - Some software is not standardized at all
        - Some software is not *documented* at all
        - Some code is badly written (can't grasp its meaning from the content)
      - See Tanenbaum
    - How does this apply to our project?
  - Case study: how to port Linux to a new architecture (LWN article)
  - Case study: how to target GCC to a new architecture
  - How does this all relate to my project?
- "Previous" Ixia stuff
  - Ixia architecture
    - Chassis
    - Card
      - Traffic engine (HW, SW): for high-speed traffic generation
      - Ixia Linux environment on HW
        - Ixia kernel (runs on x86, MIPS, PowerPC)
        - Ixia user land: one of them is IM
  - Previous IM + ixstack work
    - Running IM on a generic Linux kernel
  - Discussion (do we want to talk about this??)
    - Cards running with IxOS
    - Protocols decoupled from IxOS
    - Perhaps we don't want to talk about this
- Systematic description of
  - Project components
  - Method of porting -- super
  - Criteria for porting
  - This chapter is usually called "project architecture"
  - First thing that could be a part of this chapter
    - Engineering requirements
      - Want to be able to run protocols on a Raspberry Pi (or another Linux-based ARM board)
      - Want to be able to connect with standard Ixia clients (IxExplorer, IxNetwork)
      - Want to assess performance on new architecture versus old
    - How do the engineering requirements compare with the existing Ixia solution?
    - How to port?
      - Can also mention that this is not a linear process
      - Challenges of porting
- Implementation
  - Experience with porting
  - Implementation challenges
- Evaluation
- ...
- Conclusions and Future work