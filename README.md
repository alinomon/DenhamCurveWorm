# CURVE-WORM (0.01)

TODO make this info accurate as possible

## Installation

* Summary of set up
* Configuration
* Dependencies
* Database configuration
* How to run tests
* Deployment instructions

### Ubuntu Steps

1. sudo apt-get update
2. git clone <<repository URL>>
3. sudo apt-get install cmake
4. sudo apt-get install libatlas-base-dev
5. Shared SuiteSparse:
    * sudo add-apt-repository ppa:bzindovic/suitesparse-bugfix-1319687
    * sudo apt-get update
    * sudo apt-get install libsuitesparse-dev
6. Static SuiteSparse:
    * sudo apt-get install libsuitesparse-dev
7. sudo apt-get install libopencv-dev python-opencv
8. http://faculty.cse.tamu.edu/davis/suitesparse.html
9. tar -xf archive.tar -C /target/directory
10. sudo apt-get install gfortran
11. Create 'output' folder and 'output-fixed-K' (Capital K) (Name specified in data/model-parameters)
12. Set permissions on 'build' folder (chmod -R 777) (optional)
13. sudo apt-get install paraview

### Mac steps (Incomplete)

###### TODO: Should use MacPorts or Brew ideally (instead of both)...
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