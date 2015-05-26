# let's write an application

* an application with users
* users want certain features

## real-world testing

* users do the testing -- you only find out about problems via the live app
* unavoidable
* expensive
* worth minimizing

## application testing

* for application users' benefit
* realistic: end-to-end
* manual or automated
    * automated will miss things
    * might want both
* confirm that 
    * current features work
    * new features don't break old ones
* can't handle transformational change

### transformational change

* redo user interface from scratch
* reuse code for new application
* current application tests can't help

#### from applications to libraries

* reusable application code >> library code
* use library to do the above transformational changes

## Let's write libraries

* minimize pure app code, maximize library code
* libraries are the setable foundation that allows for application flexibility
* how do we ensure reliable, stable libraries?

### Library testing

* for application developers
* testing code should call the public API
* manual or automated -- mostly automated

## Developing a library the wrong way

* library that counts work frequency
* bug report: "All for one, one for all." returns the wrong count for "all"
    * turns out it's because the inputs aren't being lower()'d before counting
    * fix must be to add ".lower()" to the count() function

### be paranoid: don't trust your code or anyone else's
* test that the fix works, manually
* set up and run automated tests after every change

#### BUT how do you know your tests aren't buggy?
* run it against known broken code; it should fail
* if it doesn't fail, your test is useless

#### BUT how do you know whether it's the test or the code that's broken?
* write a docstring about what you were intending to test

#### BUT what if I broke the existing features with this bug fix?
* full test coverage -- tests for all public functions
    * this isn't necessarily realistic
    * add tests as you go
    * book recommendation: `Working Effectively with Legacy Code` -- Michael Feathers
        * legacy_code == "code that doesn't have tests"

## From paranoia to process
1. Test your code
1. automatically and repeatedly
1. ensure tests go from failing to passing
1. document your tests' goals
1. Test all your code.

## Test-driven development

1. software has requirements
1. encode requirements in automated tests that initially fail
1. write code to meet the specification
1. 
1. 

### Bug fixing, the TDD way

1. write test first
1. write docstring for test
1. run test, ensure it fails
1. fix code
1. run test, ensure it passes

### Feature development, the TDD way

1. Exploratory design
1. write detailed requirements
1. for each requirement:
    1. Write a test, make sure it fails
        * if writing the test is awkward, maybe your new code is awkward
    1. Write code, make sure test passes
        * test the public API!

### E.g.: Let's implement a feature

* instead of getting word count a word at a time, get it all it once.
* first explore design options
* add a stub function of new feature (just a docstring and placeholder `def`)

#### Write detailed requirements

* functionality: "all_counts() returns dict mapping lower-cased counted words to their count."
* edge case: "If no words have been add()ed, all_counts() returns empty dict."
* ambiguity: "Modifying returned dictionary doesn't modify WordCount's counts.

## Recap: Why test?

* ensure correctness of current requirements
* to prevent breakage when requirements change
* for libraries: to allow transformational change in applications

## Recap: Why test first?

* to ensure all new code has tests
* validate test does what we think it does
* for libraries: to eercise API to see if design makes sense
* good tests allow for massive changes without fear

## Resources

* book in progress: http://itamarst.org/softwaretesting/
* slides: http://itamarst.org/softwaretesting/pycon

## Questions

* how to motivate devs to do TDD?  don't incentivize # of lines of code
* what if you forget to use your tests after a while?  Use TravisCI or something to test upon commit. 
