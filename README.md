# HDF5-nar
HDF5 core and high level libraries in nar form

The version corresponds to the HDF5 lib, currently 1.8.14

Releases and fixes will use a qualifier e.g. 1.8.14+nar.1

## Things to note
Currently the following defines are hard-coded in the pom. 

`HDF5_HL`
`INCLUDE_HL`

For tweaking the build similar to a configure file they could be moved to properties and/or profiles.
