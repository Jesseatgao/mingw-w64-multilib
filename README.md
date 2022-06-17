# mingw-w64-multilib
MinGW-w64: cross compile multilib toolchain docker image based on centos7 targetting win64 and win32

## Docker Images with Tags
* `cgdoc/mingw-w64-multilib:posix-v1.4`
    * Source
        * [Dockerfile](https://github.com/Jesseatgao/mingw-w64-multilib/releases/tag/posix-v1.4)
	* Base Image
		* Centos 7
	* Cross Compilation Toolchain
		* `MinGW-w64`: 10.0.0
		* `GCC`: 10.3.0
		* `Binutils`: 2.38
		* Thread model: `posix`
		* Languages: C, C++
		* Thread support: C++ 11 Thread, POSIX Threads (winpthreads)
	* Native Compilation Toolchain
		* `GCC`: 9.3.1
		* `Binutils`: 2.32
		* Thread model: `posix`
		* Languages: C,C++,FORTRAN
	* Build System
		* `make`: GNU Make 4.2.1
		* `cmake`: 3.23.2
		* `meson`: 0.61.5
		* `rake`: Ruby Make 13.0.6 (Ruby 2.6)
	* Repos
		* CentOS 7 Base
		* CentOS 7 SCL
		* EPEL 7

* `cgdoc/mingw-w64-multilib:win32-v1.4`
    * Source
        * [Dockerfile](https://github.com/Jesseatgao/mingw-w64-multilib/releases/tag/win32-v1.4)
	* Base Image
		* Centos 7
	* Cross Compilation Toolchain
		* `MinGW-w64`: 10.0.0
		* `GCC`: 10.3.0
		* `Binutils`: 2.38
		* Thread model: `Win32`
		* Languages: C, C++
		* Thread support: C++ 11 Thread ([mingw-std-threads](https://github.com/meganz/mingw-std-threads)), POSIX Threads ([pthreads4w](https://sourceforge.net/projects/pthreads4w), aka [pthreads-w32](https://www.sourceware.org/pthreads-win32))
	* Native Compilation Toolchain
		* `GCC`: 9.3.1
		* `Binutils`: 2.32
		* Thread model: `posix`
		* Languages: C,C++,FORTRAN
	* Build System
		* `make`: GNU Make 4.2.1
		* `cmake`: 3.23.2
		* `meson`: 0.61.5
		* `rake`: Ruby Make 13.0.6 (Ruby 2.6)
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
* working with WSL:
1. Create a temporary container from an image, say, cgdoc/mingw-w64-multilib:win32-v1.4
```shell
docker create --name centos7-extended cgdoc/mingw-w64-multilib:win32-v1.4
```
2. Export the container as a tar archive
```shell
docker export centos7-extended > centos7-extended.tar
```
3. Import the distro tar file into WSL
```shell
wsl --import centos7-extended . centos7-extended.tar
```
4. (optional) Remove the container and the tar file
```shell
docker rm centos7-extended
del /f centos7-extended.tar
```
5. Run the imported CentOS Linux distro
```shell
wsl -d centos7-extended
```

## Donation
    If you like the project, please support it by donation
    [![PayPal donate button](https://img.shields.io/badge/paypal-donate-yellow.svg)](
    https://www.paypal.com/cgi-bin/webscr?cmd=_xclick&business=changxigao@gmail.com&item_name=Donation%20in%20support&currency_code=USD)