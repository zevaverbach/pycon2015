# Making Web Development Awesome with Visual Diffing Tools 

* http://bit.ly/pycon2015-visual-diffs

* unit tests check for things that might break
* screenshot tests check for things you can't imagine happening

## Screenshot tests

* bring up a test server
* take screenshots in set configurations -- PhantomJS or Selenium
* track pixel changes over time

## Tools for generating screenshots

* CasperJS
* Huxley
* Wraith
* PhantomCSS
* dpxdt
* Hardy aka GhostStory
* Needle
* Cactus
* CSSCritic
* seltest

## Commit your screenshots to git repo!

* creates visual history of the website
* GitHub has a nice image viewer and also supports showing image diffs

## import webbrowser

* dreamy way of building websites
* uses React

## Issues

* either make sure everyone's using the same OS version and PhantomJS v., or.. SauceLabs

## uses

* QA on your releases
...

## When to write a pdiff test?

* if you find yourself reloading your browser over and over again when making changes, or checking for responsiveness, write a unit test instead (with pdiff)
