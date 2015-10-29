# HDF5-nar
HDF5 core and high level libraries in nar form

The version corresponds to the HDF5 lib, currently 1.8.14

Releases and fixes will use a qualifier e.g. 1.8.14+nar.1

## Things to note

### Dependencies

Currently you'll need two that aren't in a maven repo. Clone and build them; it's very quick; they are tiny.

[zlib](https://github.com/markjohndoyle/zlib)

[szip](https://github.com/markjohndoyle/szip-nar)

### Configure stage and CMAKE

#### Generator

The generator is available as a pom property, it is currently set as follows:

'<cmake-generator>MSYS Makefiles</cmake-generator>'

You can override this by changing this value, deleting the line to use the defaults, or overriding it on the command line:

`mvn install -Dcmake-generator="Unix Makefiles"`

*don't forget the quotes otherwise maven will this Makefiles is a goal*


#### 64 bit Linux issues
The configure module uses cmake and the existing config files to configure the project. You can pass options to this just like any other cmake project.

The cmake plugin uses it's own cmake binary independent of the one on your system. The binary is a 32bit version which apparently is all the cmake team will release. There are 64 bit versions in dist packages.  Anyway, if you are on a 64 bit linux OS you'll see file not found errors which are actually the incompatible libraries causing the cmake binary to fail.

The [workaround](http://www.howtodoityourself.org/how-to-fix-libld-linux-so-2-bad-elf-interpreter-no-such-file-or-directory.html) is to make the 32 bit libs available:

On any RPM based distribution (CentOS/RedHat/Fedora/Suse/Mandriva):

`yum -y install glibc.i686`

On any DEB based distribution (Debian/Ubuntu/Mint/Crunchbang):

`apt-get update`
`apt-get install ia32-libs`
