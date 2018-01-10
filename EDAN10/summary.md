Author: Måns Ansgariusson

# Configuration management
CM is the art of identifying, organizing, management of the software being built by programming team. The goal is to maximize productivity and minimize mistakes.
* Minimize confusion by organization and communication

# Three problems of SCM
* Double maintenance - An update needs to be made on several locations.
  Keeping multiple identical copies. 
* Shared data - Working concurrently on the same file( literally: think google
  docs).
* Simultaneous update - An update may be overwritten by a later commit.

# Construction site metaphor
* The construction site is the shared repository
* communication and coordination between teams.
* API
* Airplane door example.
* Team play is key!

# Library metaphor
* What do we keep track of in our SCM-tool.
* Metadata, library, documentation, files. Everything that is a soft copy.
* soft copy - Everything that part of software but not a tool or external
  library.

# Study metaphor
* Your own workspace
* Test the code, no affect on the "real" repo (upstream repo).
* Study sends updates to the construction site.

# Distributed development
 - locally
 - distance working
 - co-located
 - distributed
**High cohecence, low coupling** is the goal for any SCM but especially a
Distributed team.

### Issues
Awareness, harder to communicate.
Different countries, different time zones, culture, language, this effects the communication, coordination and control, delays, lack of baseline plan, lack of coding standard.
### How to solve
avoid direct conflict (changes made by two or more developers on the same artifact), indirect conflicts (changes in one artifact that has affect on other artifact), well defined tasks, exclusive area responsibility, mailing lists, telephone calls, place all developers at the same site, all developers needs to agree on a common management process
# Feilers models
* checkout/check-in model - two parts, the repository and the build tool. User have to “checkout” a file to work on it and then “check-in” a new version of the file into the repository. Can be done with branches as well as files and merging them together. - **PROBLEMS** - double maintenance (can be), and simultaneous update.
* Long transaction model - Demands that the files you've changed is up to date with the master branch. **PROBLEMS** - double maintenance
* Strict long transaction model - says that all the files needs to have the latest revision before pushing to the shared repository. **PROBLEMS** - double maintenance
* change-set model - Git patches, atomic changes thats made. Pull request,
  patch. All or nothing gets accepted into the master branch. **problems** -
  double maintenance, "simultaneous updates"
* Composition model - an outgrowth of the checkout/check-in model.  Gives a
  list of all components from a system, version selection rules indicate which
  version to be chosen for each component. Gives a support for management of
  system variants.

# Automation
* continuous Integration - branch often and merge often.
* continuous delivery - every commit is a release
* continuous deployment - every commit is deployed in production right away

# Branches
Why we use branching:
* Isolation ( new codeline, security of the main codeline)
* Easier to make logical changes.
* Variations
* quality assurance

Why branches are bad:
* Double maintenance
* deferred merge - merge conflicts of doom
* added complexity

Liveliness - measures the activity on a branch.

Stale branch - a branch wich has no activity.
## Our project
GitFlow:
* Bad:
  * increased complexity
  * Difficulty to create a release
Good:
* a lot of reasons, pick one.

Branch by release:
* Bad:
  * horrible traceability
  * double maintenance. (HUGE AMOUNTS)
Good:
  * easy to roll back
  * easy to maintenance
  * release speed

# CBB - Change control board
* Chang requests -
* Understand the role and working of the CCB (change control board)-  A committee that has the final authority to act on proposed changes at its level. Also establish baselines. Consists of Chairperson (usually the program manager), secretary (configuration manager) , members (represents the major components of the program) and specialists (called to meetings case-by-case). Non Voting committee, the chairperson is the final decisionmaker, but gets inputs from the rest to make the best decision. should be formal meetings with agenda and good documentation, such as change description, date for implementation  verification.
* Ivory tower effect - Putting CCB on wrong level in the organization. To high - removed from developers, to low - to little impact in the organization.
* Considerations -  can a component be reused? scrapped? and so on, it will affect the cost and may be rejected by the CCB.
* Dependency analyses - relations among program entities
* impact analyses - provides a detailed examination of the consequences of a change. major goal is to identify the product affected by changes. Analysing the software-life-cycle-objects and produce a list of items that should be addressed with a change. More or less, what are the risks with a change.  keep track of “ripple effect”- small change that have impact on many other parts.
* Product owner
* Secretary - CM

**CBB for agile teams:**
* Stand-up meeting.

# Configuration Identification
* what do we want to keep in our library?

# Status accounting
* allow people to easily find information
* incorrect data is worse than no data

# PDM - Product Data managment
*  PDM - focuses more on maintenance and production,and SCM focuses on development. PDM always has a physical existence.
* Hardware development
* Vendors
* Whats in stock?
* All the metadata from real objects.

**SCM-vendors**: opensource code.

# Glossary
* Program family - a set of modules that build a program (library). a set modules is called a configuration.
* Configuration - a set of files and/or revisions.
* revision - linear progression of a file.
* variation - different files that does the same thing. Different modules for
* Difference between revisions and variants – a revision is a new version intended to supersede the old. Unlike revisions variants does not supersede the old
different purposes.
* reproducibility - being able to reproduce a certain time in the development.
* Baseline - shared project database (master)
* charge out/charge in model - locks the next revision to be your changes.
* Delta files - git blob, changes from last revision.
* CI - can be changed, there is revision
* Artifact - Binary files.
* Difference between what is CI and what is not – A CI is a Configuration Item that is any part of the development and/or deliverable system which needs to be independently identified, stored, tested, reviewed, used, changed and maintained. Ex. Contracts, technical documents, deliverable software, standards for inventories of development and test environments, baseline drawings, demonstration to customer.
A good question to ask: ”would our ability to deliver the right system, on time and within budget, be impacted in any way if a particular document, drawing, piece of software or hardware kit were lost or corrupted, or were used incorrectly or at the wrong version?”
* Agile SCM - audits is replaced by acceptance tests. It is test-driven development, integrate with many small tests.  Collective ownership.

* SCM audit - A quality assessment of the SCM status and the quality gates.

# Agile developement SCM
What is important:
* Configuration Audit -> verfifying Quality Assurance
* Planning Game -> CCB (Configuration Control)

Everything in SCM is important though, but some factors need to be highlighted.

Continuous integration needs heavy support from configuration audit.

# Variants
* Variation Segregation (branching)
* Single Source Variation (Single source, conditional compilation)

## The Eight functional areas of software configuration management
* Version and configuration control
* Configuration item structuring
* Construction of configurations
* Change Management
* Teamwork support
* Process management
* Auditing
* Status Reporting
