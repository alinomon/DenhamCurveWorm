# CURVE-WORM (0.01)

Code for running a simluation of a C. elegans integrated neuro-mechanical locomotion model written in `C++`.

## Prerequisites

`C++` compiler with support for `C++11` (e.g. GNU C++ Compiler version 4.8.5 or above), `CMake` version 2.8 or above,
GNU `make`,
Basic Linear Algebra Subroutines (BLAS) (e.g. atlas-blas),
Suitesparse

(See more detailed description below).

## Synopsis

  ./worm-model ../data/model-parameters [options]

     Run simluation with parameters from `model-parameters`
     file. Extra options can be used which overwrite model-parameters
     using `--parameter=new-value`. Outputs are:

     * worm_*.vtu all solution variables output in a format readable by Paraview
     * Activation.txt ??
     * Beta.txt ??
     * Kappa.txt ??
     * energy.txt ??
     * feedback.txt ??
     * pointx ??
     * pointy ??
TODO jack - add descriptions of these files

## Authors

* Jack Denham, scjed at leeds.ac.uk
* Thomas Ranner, T.Ranner at leeds.ac.uk
* Felix Salfelder, F.Salfelder at leeds.ac.uk

EC Stoner Building, University of Leeds, Leeds. LS2 9JT. UK.

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

    Copyright (C) 2017        Mark Bromley
    Copyright (C) 2017 - 2018 Jack E. Denham
    Copyright (C) 2016        Robert I. Holbrook
    Copyright (C) 2015 - 2017 Thomas Ranner
    Copyright (C) 2017 - 2018 Felix Salfelder

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.

## Extra details for building prerequisites

TODO ensure these are correct

### Ubuntu Steps

Install dependencies:
```
apt-get update
apt-get install -y g++
apt-get install -y libatlas-base-dev
apt-get install -y libsuitesparse-dev
apt-get install -y git
```

Clone and build repository:
```
git clone https://bitbucket.org/leedswormlab/curve-worm-royal-society-paper.git curve-worm
cd curve-worm
mkdir build && cd build
cmake -D CMAKE_BUILD_TYPE=Release ..
make
```

Optionally test:
```
ctest
```

### Mac steps (untested)

Install dependencies

1. git clone <<repository URL>>
2. brew install cmake
3. chmod -R 777 python folder (TODO: Hack - this shouldn't be necessary)
4. brew install gcc
5. remove rt from CMakeLists.txt
6. sudo port -v install SuiteSparse
7. sudo port install opencv

## Running

1. paraview &
2. Open output/worm...vtu
3. Play

## Contribution guidelines ###

* Writing tests
* Code review
* Other guidelines

## Who do I talk to? ###

* Repo owner or admin
* Other community or team contact