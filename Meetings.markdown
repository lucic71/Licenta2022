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
