=======================================================================
Reusable Framework for Retrieval of Atmospheric Composition (Refractor)
=======================================================================

| Jet Propulsion Laboratory, California Institute of Technology. 
| Copyright 2017 California Institute of Technology. U.S. Government sponsorship acknowledged.

This software is continuation of the OCO-2 Level 2 Retrieval Algorithm `(NASA NTR-49044) <http://www.techbriefs.com/component/content/article/ntb/tech-briefs/information-sciences/20330>`_. It retrieves a set of atmospheric/surface/instrument parameters from a simultaneous fit to spectra from multiple absorption bands. The software uses an iterative, non-linear retrieval technique (optimal estimation). After the retrieval process has converged, the software performs an error analysis. The products of the software include all quantities needed to understand the information content of the measurement, its uncertainty, and its dependence on interfering atmospheric properties.

The software provides a flexible, efficient, and accurate tool to retrieve the atmospheric composition from near-infrared spectra. Its unique features are:

* Spectra from ground-based or space-based measurement with arbitrary observation geometry can be analyzed.
* The retrieved parameters can be chosen from a large set of atmospheric (e.g., volume mixing ratio of gases or aerosol optical depth), surface (e.g., Lambertian reflection), and instrument (e.g., spectral shift or instrument line shape parameters) parameters.
* The software uses an accurate, state-of-the-art, multiple-scattering radiative transfer code combined with an efficient polarization approximation to simulate measured spectra.
* The software enables fast and highly accurate simulations of broad spectral ranges by an optional parallelization of the frequency processing in the radiative transfer model.

.. toctree::
   :caption: Table of Contents
   :maxdepth: 2

   setup
   system_configuration
   compilation
   testing
   lua
   python_wrappers
   developer_information
   other_documentation
   acronyms
