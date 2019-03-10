Repository Structure
=================

Academy material will have three repositories:
* [Instructors Repository](https://github.com/LDSSA/batch3-instructors)
* [Students Repository](https://github.com/LDSSA/batch3-students)
* [Workspace Repository](https://github.com/LDSSA/batch3-workspace)


## Instructors Repository
This repository will contain all academy materials that will go eventually on
the *Student Repository* and the exercise notebooks containing the solutions.
Repository structure will be as follows:
```
repo
 |
 |- BC01 - Boot Camp Part 1
 |   |
 |   |- SLU01 - Pandas 101
 |   |   |- Exercises Notebook.ipynb
 |   |   |- environment.yml (output of conda env export > environment.yml)
 |   |   ... (extra material)
 |   ...
 |
 |- SPC01 - Binary Classification
 |   |- BLU01
 |   |   |- Exercises Notebook.ipynb
 |   |   ... (extra material)
 |   |
 |   |- BLU02
 |   ...
 ...
```

Besides the placement (and naming) of the exercise file and the environment 
file everything else is left to the learning unit owner.


## Students Repository
The student repository is generated from the *Instructors Repository* by
processing the exercise notebooks to remove exercise solutions.


## Workspace Repository
This repository is only a skeleton with the learning unit directories of
the other repositories but without any content.
Students will fork this to a private personal repository.
When starting to work on a SLU/BLU the student will copy the corresponding 
materials from the student repo and work from the workspace repo.
We will supply a deploy key that will allow us to pull the repository
for grading.

