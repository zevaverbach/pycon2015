# Talk: systems programming as a swiss army knife

# When I go to google.com, kernel code runs for:

* typing in the address
* handling every network packet
* writing history files to disk
* allocating memory
* communicating with the graphics card

You don't have to worry about these things because your operating system deals with it.

# How to call operating system code

## System calls

* interface to your operating system
* write files

# Using systems knowledge to debug your programs

## strace = tracing system calls

* it tells you every single system call a given program makes
* presenter made a 'zine about it!  must get.

### e.g. `strace -e open bash`

* that'll tell you whether your bash is reading .bashrc or .bash_profile

## others

* `write` for log files
* `execve` for starting programs

# The case of the French website

* when going to a website, it displays "Welcome to PyCon!"
* when `curl`-ing that same website, it displays, "Bienvenue a PyCon!"
* solved somehow with `ngrep` which discovered an 'accept only English signal of some kind'

## network spying tools

* `ngrep`
* `tcpdump`
* `wireshark`
* `mitmproxy`

## `time` (mystery #1)

* `time python py_file.py` --> tells you how long it took to run

### "What is the program waiting for?"

* `pgrep -f py_file`
* some network-ish stuff appears: "It's waiting for the network!"

# Mystery program #2

* use a Python profiler if `pgrep` shows 99% CPU

# Mystery program #3

* `time python mystery_3.py` -- the first time it ran quickly and used 62% CPU; second time was 10%
* pgrep shows a lot of `write`-related things
* but why does it take different amounts of time
* `dstat` -- tells you how much stuff your OS is writing right now
* the program kept writing even after it said it was done.  this is because the OS tells you the program is done, but then caches everything and writes stuff to disk afterwards.  

# Awesome tools

* /proc
* all the stuff from above
* dtrace (OS X)
* if you learn about your operating system, you can do a lot more -- across all programming languages
* Recurse Center -- where she learned everything she knows
* @bork = Julia Evans
