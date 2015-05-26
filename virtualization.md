## The Landscape

* "You will need a few days to get a development environment set up and working."
* "We added a new service; we should really document that."
* "Are you sure you're running the same version of Python?"
* "It works on my machine!"

That's not how things should be; we should fix it.

## What Do We Want?

Dev environments that

* mirror production as much as possible
* are low-cost
* are disposable
* don't suck to develop on

### Why?

* portability -- for new hire: a setup that just works 
* consistency
* reusability

* Vagrant == most popular tool
    * wraps around other tools: VMWare, virtualbox etc.

## Provisioning tools

* Ansible
* Chef
* Docker
* Puppet
* SaltStack

* tell Vagrant in provisioning that this VM is a development box

## Advantages of virtualization

* different amounts of RAM
* different OSs
* `vagrant share` allows you to share your box with others
