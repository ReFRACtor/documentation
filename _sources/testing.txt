=======
Testing
=======

.. highlight:: console

There are several types of testing that can be run either through the build system or independently. `CTest <https://cmake.org/Wiki/CMake/Testing_With_CTest>`_ is used as the test runner.

Unit Testing
============

Unit tests check individual pieces of the system. The focus of this testing is on the software itself: did it build correctly, are the individual classes calculating expected results.

The unit tests are fully automated. You can run them with the following command from a build directory::

    $ make unit_test

This runs through all the unit tests that don't take a long time to run, and in the end says if the tests are successful or not (i.e., there is no analysis on your part, the test either succeeds or it doesn't).

A longer, more complete set of tests can be run using the command::

    $ L2_FP_LONG_CHECK=1 make unit_test

This runs all the tests that ``make unit_test`` does, plus additional tests that take longer to run. For an optimized build this takes a few minutes to run, for a debug version takes much longer to run. 

By supplying the ``RUN_TESTS=`` option to make, the build system can be instructed to run single tests or groups of tests. The value passed to ``RUN_TESTS`` should be a regular expression that matches the names of the intended tests. For example to only run the lidort_driver tests use the following command line::

    $ make unit_test RUN_TESTS=lidort_driver

Full Tests
==========

A build target ``full_test`` exists that runs two types of tests:

* End to end tests
* Python Nose tests

The results are compared against expected results, printing out the differences.

For example, to run all of these tests, in your build directory run::

    $ make full_test

To run specific tests::

    $ make full_test RUN_TESTS=sample

The end to end test can be run using the ``full_test_regular`` make target. The Python Nose tests can be run with the ``full_test_python`` target.

Parallel Testing
================

Tests can be run in parallel by specifying the ``CTEST_PARALLEL_LEVEL=<num>`` environment variable on  the command line. It works when running tests through make or CTest. For instance::

    $ CTEST_PARALLEL_LEVEL=5 make unit_test

Test Names
==========

The names of tests that are seen by CTest have a prefix of their type to make it easier to match against them. If ``ctest`` is run without any arguments then all unit, python and full tests would be run. The prefixes are as follows:

============= ============
Prefix        Type of Test
============= ============
unit/         Unit Tests
full/regular  End to End Tests
full/python   Nose Tests
============= ============

Testing Targets
===============

The following a list of all make targets available:

================== ===========
Target             Description
================== ===========
unit_test          Unit tests
full_test          Run regular and Python tests
full_test_regular  End to end tests
full_test_python   Python Nose tests
================== ===========

Advanced Testing
================

If the ``RUN_TESTS`` option is not sufficient for specifying what to run, CTest can be run directly. In the ``test/`` subdirectory of the build directory is a script named ``ctest_wrap.sh``. This script provides some environmental variables needed by the unit tests then calls ``ctest``. It is created by the build system when ``cmake`` is first run. You must change to the ``test/`` directory for it to run correctly.

For example, to run just the LIDORT driver unit test using the CTest wrapper, do the following::

    $ cd test/
    $ ./ctest_wrap.sh -R lidort_driver

The value given to ``-R`` is a regular expression that matches test names that can be seen when running all tests. Any CTest option will be passed through the wrapper script. See the `CTest manual <https://cmake.org/cmake/help/v3.0/manual/ctest.1.html>_` manual page for more details on what can be specified.
