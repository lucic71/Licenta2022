# Project Structure:

- Intro
  + systems and software engineering -> software platfrms (portability problems) -> portability
  + software portability
  + abstract decomposition
  + the domain is not well explored (not in an academic way, the internet is full of people sharing porting experiences)
  + the first part must introduce the reader into the subject, the second will explain the structure of the article, another part will need to provide our contributions
- Background
  + quantitative portability paper
  + portability layers (hw, system, application)
- Implementation (give this chapter a more specific name: porting IM on RPi)
  + how did we port the IM? (the methodology)
  + what problems occured because the system was to complex?
- Experimental Evaluation [WIP]
  + how "easy" (??) was the porting process
  + comparative performance evaluation of the "before" and "after"?
- Discussion
  + what role does the documentation play in the porting process?
  + what role does the familiarity of the person working with the system play in the porting process?

# Project Milestones

- 28 Feb - start work
- March 31 - report 1 (document + slides)
  - should have draft for intro + background by now
- April 15 - architecture/implementation draft
- May 5 - report 2 (document + slides)
  - some preliminary evaluation work should be done
  - tight loops for eval + planning here
- May 30 - final draft
  - discussion draft should be done by here
- June 15
  - what Lucian calls "final draft": thesis should be mostly ready to
    be delivered at this point
  - leftover evaluation/implementation tasks

# Evaluation ToDos

- Determine a set of relevant metrics for porting evaluation
- Determine a set of relevant metrics for experimental evaluation
- Evaluation testbed
  - Redeploy old experiment
  - Fix any remaining bugs (this is a *risk* factor)
  - Bring-up many test interfaces etc., measure convergence time
	- IxOS protocols: IPv4, IPv6, DHCP

# Ideas to write about

- how well are defined software processes other than porting? (see Sommerville)
- what lessons can we learn from Linux as it's the most popular ported software system?

# Report 1

- [Google Slides link](https://docs.google.com/presentation/d/15sXp6gKmoUbNaJJearsRxT79vbwc3U4E/edit?usp=sharing&ouid=102915141630231344771&rtpof=true&sd=true)
# 2022 April 4, Diploma meeting #18 comments
Encompass the technical work within a more general framework of
software development process of porting:
	- people motivation: porting is not trivial, it has various costs associated with it.
	people put a lot of effort into porting complicated systems. the reasons for porting
	are diverse: deprecation of hardware or availability on as many as possible platforms.
	we must ask ourselves: how to engineers estimate the porting workload? or what are
	the metrics they use to evaluate their work? the reasons for asking such questions are:
	engineers have other things to do, so it is good to know how much time they spend on
	porting so that they can optimise their overall work; and it is even better to know
	the strengths and weaknesses of the porting process so that the engineer can optimize
	the work of porting in the future. (what I'm trying to say here is that the engineering
	work is important, ofcourse, but as important as it (or maybe more important) is the
	retrospective work, as in: are we satisfied with what have we done? or do we have
	something to improve? these are not easy questions most of the time because they force
	you to think very deeply about the work you have done, about the process of doing that
	work. however if the questions are answered, people involved in the discussion are better
	off as they know understand what they did good and wrong.)
	- contributions: we calculate the costs of porting IxOS testing infrastructure on
	ARM SBC's so that next time when we will face a porting process we will be prepared
	to estimate the costs and evaluate our work at every point of the process. (in other
	words, we make a retrospective on our work)
	- background/related work: should maybe focus on
	 porting/portability metrics
	- architecture: "before and after" (existing IxOS architecture,
	 new project architecture -- clarification here, regarding
	 integration between our project and IxOS), and also, an
	 estimation of porting costs
	- implementation: description of porting process, challenges -->
	 those ate some porting time
	- evaluation
	 * performance evaluation (not so important)
	 * porting evaluation (!!!)
	- discussion: limitations, what we can do next
	- conclusions and future work
