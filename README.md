[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)


ARISE: Crystal-structure recognition via Bayesian deep learning
========================================================

![](./assets/ARISE_logo.pdf)


This package provides code for reproducing the results of 

    A. Leitherer, A. Ziletti, and L.M. Ghiringhelli,
    Robust recognition and exploratory analysis of crystal structures via Bayesian deep learning, arXiv.... (2021)

This repository uses functionalities of ai4materials (https://github.com/angeloziletti/ai4materials, https://ai4materials.readthedocs.io/en/latest/).

ai4materials allows to perform complex analysis of materials science data, using machine learning techniques. It also
provide functions to pre-process (on parallel processors), save and subsequently load materials science datasets,
thus easing the traceability, reproducibility, and prototyping of new models.

Code author: Angelo Ziletti, Ph.D. (angelo.ziletti@gmail.com; ziletti@fhi-berlin.mpg.de), Andreas Leitherer, Ph.D. student (andreas.leitherer@gmail.com, leitherer@fhi-berlin.mpg.de)



------------------
Installation
------------------
Clone this repository, cd into ARISE and execute

    pip install -e .

Currently, this package contains two implementations for the smooth-overlap-of-atomic-positions (SOAP) descriptor, one from quippy (https://github.com/libAtoms/QUIP) and one from DScribe (https://singroup.github.io/dscribe/latest/). These packages are external dependencies that have to be installed manually (see respective documentations).

---------------
Usage
---------------

For global or local analysis of single- or polycrystalline systems, one just needs to define the corresponding geometry file and load a pretrained model for prediction:

    from ai4materials.models import ARISE

    geometry_files = [ ... ]

    predictions, uncertainty = ARISE.analyze(geometry_files, mode='global') 

    predictions, uncertainty = ARISE.analyze(geometry_files, mode='local',
                                              stride=1.0, box_size=12.0)
