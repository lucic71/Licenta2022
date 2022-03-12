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
