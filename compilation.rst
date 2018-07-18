===========
Compilation
===========

.. highlight:: console

The Refractor Framework use `CMake <http://cmake.org>`_ as it's build system. 

Building
========

First create a new directory where compilation will occur. If the :doc:`required dependencies <system_configuration>` are installed in standard locations, then at minimum the configuration of the system can be performed with the following command::

    $ cmake /path/to/refractor

But to run unit and full tests the ABSCO and MERRA input's location path need to be specified. In that case supply options as follows to CMake::

    $ cmake /path/to/refractor -DABSCO_DIR=/path/to/absco -DMERRA_DIR=/path/to/merra

Once the build directory has been configured using CMake compilation is done using the standard ``make`` software. With out any arguments the ``all`` target will be use used::

    $ make

If parallel make will be used it is recommended to run the ``thirdparty`` build target first without the ``-j`` option, for example, build ``all`` from scratch as follows::

    $ make thirdparty
    $ make -j 10 all

The following table shows the most meaningful build targets available:

============ =========== 
Target       Description
============ ===========
all          Builds the thirdparty, full_physics, l2_fp and python targets
thirdparty   Builds third party software that is packaged with the source
full_physics Builds the full_physics library
l2_fp        Builds the l2_fp binary that uses the full_physics library
python       Builds the SWIG Python bindings
install      Installs the built system into the configured prefix, by default <build_dir>/install
doc          Creates Doxygen API documentation
unit_test    Runs all unit tests
full_test    Runs all full tests
nose_test    Runs all Python Nose tests
============ =========== 

Using Other Compilers
=====================

To use alternative paths to compilers supply the following environmental variables before running ``cmake``. **Note**: These must be defined before the first run of ``cmake``. You will have to use a clean build directory when changing them:

======== ===========
Variable Description
======== ===========
CC       Defines the C compiler, defaults to gcc
CXX      Defines the C++ compiler, defaults to g++
FC       Defines the Fortran compiler, defaults to gfortran
======== ===========

The values supplied in these variables must be full paths. For example to use a different version of C++ you could do something like this::

    CC=$(which gcc-5) CXX=$(which g++-5) cmake /path/to/refractor

If you use these variables in a script they will need to be exported to the shell environment first, the following is equivalent of the above:::

    export CC=$(which gcc-5)
    export CXX=$(which g++-5)
    cmake /path/to/refractor

Build Options
=============

There are many build options given to CMake that can be used to specify alternative locations of dependencies or to change the way the software is compiled. They are documented below. These are all supplied using the ``-D<option>=<value>`` option to ``cmake``.

======================== ===========
Option                   Description 
======================== ===========
ABSCO_DIR                Path to the base path where ABSCO tables are installed
MERRA_DIR                Path to where the MERRA Aerosol Apriori Database is installed
CMAKE_INSTALL_PREFIX     Path where the ``install`` target should put files, defaults to ``<build_root>/install``
CMAKE_BUILD_TYPE         Determines compiler flags used can be either ``Debug``, ``Release`` or ``RelWithDebInfo``. The default is ``Release``
BUILD_LUA                Set to ``1`` to build the supplied version of Lua even if its detected as installed on the system
BUILD_LUABIND            Set to ``1`` to build the supplied version of Luabind even if its detected as installed on the system
BUILD_PYTHON_BINDING     Set to ``OFF`` to disable building Python bindings, defaults to ``ON``
GSL_ROOT_DIR             Base path to where GSL has been installed in case Cmake can not find it automatically
BOOST_ROOT               Base path to where Boost++ has been installed in case Cmake can not find it automatically
HDF5_ROOT                Base path to where HDF5 library has been installed
SWIG_EXECUTABLE          Path to the SWIG 3.0 executable file
PYTHON_LIBRARY           Location of the Python library (``libpython.so``) in case Cmake can not find it or finds the wrong version
PYTHON_EXECUTABLE        Location of the Python executable in case Cmake can not find it or finds the wrong version
LIDORT_MAXLAYER          Number of atmospheric layers for LIDORT to use if the default value is too small
LIDORT_MAXATMOSWFS       Number of atmospheric jacobians for LIDORT to use if the default value is too small
======================== ===========

Debugging
=========

As noted in the last section, debug builds can be enabled as follows::

    $ cmake /path/to/refractor -DCMAKE_BUILD_TYPE=Debug

The ``Debug`` build type does not use any compiler optimization. An alternative build type that uses compiler optimizations, but also includes debugging symbols, is the ``RelWithDebInfo`` build type. It can be enabled as follows::

    $ cmake /path/to/refractor -DCMAKE_BUILD_TYPE=RelWithDebInfo

The optimizations used with this build type are not as aggressive as with the default build type causing the code to run slightly slower.

When running ``make`` the commands being run can be displayed by running make with the ``VERBOSE`` option::

    $ make VERBOSE=1
