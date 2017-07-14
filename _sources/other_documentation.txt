===================
Other Documentation
===================

ATBD
====

The `OCO-2 algorithm theoretical document <http://disc.sci.gsfc.nasa.gov/OCO-2/documentation/oco-2-v6/OCO2_L2_ATBD.V6.pdf>`_ describes the algorithms in the RT Retrieval Framework used to retrieve the column-averaged CO2 dry air mole fraction XCO2 and other quantities included in the Level 2 (L2) Product from the spectra collected by the Orbiting Carbon Observatory-2 (OCO-2). It identifies sources of input data, describes the physical theory and mathematical background underlying the use of this information in the retrievals; includes implementation details; and summarizes the assumptions and limitations of the adopted approach.

Doxygen
=======

`Doxygen <http://www.stack.nl/~dimitri/doxygen/>`_ documentation can be created from the build directory::

    $ make doc

The resulting documentation will be available in the ``doc/html`` subdirectory.
