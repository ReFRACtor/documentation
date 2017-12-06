=====
Setup
=====

.. highlight:: console

The following sections describe how to obtain and initialize the tools and source code needed to develop and utilize the resources available for running Refractor. These sections describe a recommended directory structure that can be changed by the user. Operators/developers should feel free to reorganize where they deploy the tools. The organization has been designed to not necessitate any one strict directory organization.

Obtaining the Code
==================

A public copy  of the source code will be available in the future, but at the current time it is available through the JPL Enterprise GitHub server:

:: 

    $ git clone https://github.jpl.nasa.gov/refractor/framework.git

Our repository uses `Git Large File Storage <https://git-lfs.github.com/>`_ to store large binary files. It must be installed on the system you are using for development. Once it is installed you initialize its usage by doing the following from the checked out repository directory::

    $ git lfs install
    $ git lfs update
    $ git lfs pull

Development Environment Organization
====================================

The development environment checked out in the preceding section has the following important sub-directories:

=================  ========================
bindings/          Files related to Python interface binding
doc/               Doxygen documentation configuration
input/             Input files and Lua configuration
lib/               Where most source code lives
support/           Supporting utilities
test/              Inputs, expected results and scripts used by full and unit tests
=================  ========================
