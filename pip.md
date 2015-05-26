# Central Tenets

* deploying should be as easy as pushing a button
* reverting should also be easy as pushing a button
* bad deployment processes impede development speed and innovation 
    * they create a negative feedback loop of anxiety and fewer pushes
* good deployment proesses foster development and innovation
* code isn't useful until it's being used

## Hypothetical

* you have a new feature or a bug fix that's in a rush
* deploy: what's the worst that could happen?  Disaster.

## Do you have more than one way to 

* deploy code across teams?
* deploy code amongst a team?
* deploy a single app?

* having a single process is best, especially in the latter two bullets

## Our old deployment setup

* Debian packaging -- process wasn't maintained, people started wanting a new way to deploy code
* SCP un-versioned tarballs -- miserable failure
* Chef installing packages -- worked for a little while, but Chef deployed every 30 mins whether you liked it or not
* pip installations -- today's talk

## Choose one deployment method and stick with it

### Python-based packaging

* Python & Setuptools to build packages
* PEP 440 versioned packages
* pip to install Python packages
* Jenkins for CI and package building
* Chef for initial deploy and service discovery
* Fabric for gluing the pieces together

### How does it work?

* Github used internally
* Jenkins job runs tests, builds a package, uploads it to an internal PyPI server
* Project-specific Jenkins job triggers generic deployment job
* Generic deployment job queries Chef server via Fabric
* SSH into each node and upgrade the Python package, pip install 'u
* job restarts service which loads new code: kill -HUP <pid>, test the new code
* control flow returns to the project-specific job
* notify monitoring that a deploy happened, include v. and timestamp (HipChat, New Relic)
* rinse and repeat for all nodes

## Key takeaways

* choose one deployment strategy and iterate on it -- team-wide or org-wide
* code can be deployed in parallel
* services should be bounced sequentially
* centralized deployment job makes for easy rollbacks
* other codebases can use similar deployment setup

## Shortcomings

* fixing old code deployemnt is very painful
* strongly coupled with Chef for service discovery- not great with edge cases
* Jenkins not the greatest continuous deployment server 
* initial hacky usage of Fabric in early stages

# New vocabulary for me

* "internal PyPi repo"


