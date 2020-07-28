# mingw-w64-multilib
MinGW-w64: cross compile multilib toolchain docker image based on centos7 targetting win64 and win32

## Docker Images with Tags
* `cgdoc/mingw-w64-multilib:posix-v1.0`
    * Source
        * [Dockerfile](https://github.com/Jesseatgao/mingw-w64-multilib/releases/tag/posix-v1.0)
	* Base Image
		* Centos 7
	* Cross Compilation Toolchain
		* `MinGW-w64`: 7.0.0
		* `GCC`: 10.1.0
		* `Binutils`: 2.34
		* Thread model: posix
		* Languages: C, C++
	* Native Compilation Toolchain
		* `GCC`: 9.1.1
		* `Binutils`: 2.32
		* Thread model: posix
	* Build System
		* `make`: GNU Make 4.2.1
		* `cmake`: 3.6.2
		* `meson`: 0.54.3
		* `rake`: Ruby Make 13.0.1 (Ruby 2.6)
	* Repos
		* CentOS 7 Base
		* CentOS 7 SCL
		* EPEL 7

* `cgdoc/mingw-w64-multilib:latest`
    * Source
        * [Dockerfile](https://raw.githubusercontent.com/Jesseatgao/mingw-w64-multilib/master/Dockerfile.multi.mingw)
	* Base Image
		* Centos 7
	* Cross Compilation Toolchain
		* `MinGW-w64`: 7.0.0
		* `GCC`: 10.1.0
		* `Binutils`: 2.34
		* Thread model: Win32
	* Native Compilation Toolchain
		* `GCC`: 9.1.1
		* `Binutils`: 2.32
		* Thread model: posix
	* Build System
		* `make`: GNU Make 4.2.1
		* `cmake`: 3.6.2
		* `meson`: 0.54.3
		* `rake`: Ruby Make 13.0.1 (Ruby 2.6)
	* Repos
		* CentOS 7 Base
		* CentOS 7 SCL
		* EPEL 7

## Usage
* For cross-compiling win32 target: see for example
	* [Cross compile Aria2 i686 on CentOS 7](https://github.com/Jesseatgao/aria2-patched-static-build/blob/master/Dockerfile.i686.mingw)
	* [Cross compile common devel packages(header files and libs)](https://github.com/Jesseatgao/mingw-w64-libs)
	* [Cross compile MKVToolNix (mkvmerge)](https://github.com/Jesseatgao/MKVToolNix-static-builds)
* cross-compiling win64 target: see for example
	* [Cross compile Aria2 x86_64 on CentOS 7](https://github.com/Jesseatgao/aria2-patched-static-build/blob/master/Dockerfile.x86_64.mingw)
	* [Cross compile common devel packages(header files and libs)](https://github.com/Jesseatgao/mingw-w64-libs)
	* [Cross compile MKVToolNix (mkvmerge)](https://github.com/Jesseatgao/MKVToolNix-static-builds)
