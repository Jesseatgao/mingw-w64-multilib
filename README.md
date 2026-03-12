# mingw-w64-multilib
MinGW-w64: cross compile multilib toolchain docker image based on Oracle Linux 9 targetting win64 and win32

## Docker Images with Tags
* `cgdoc/mingw-w64-multilib:posix-v1.8-el9`
    * Source
        * [Dockerfile](https://github.com/Jesseatgao/mingw-w64-multilib/releases/tag/posix-v1.8-el9)
    * Base Image
        * Oracle Linux 9
    * Cross Compilation Toolchain
        * `MinGW-w64`: 13.0.0
        * `GCC`: 15.2.0
        * `Binutils`: 2.46.0
        * Thread model: `posix`
        * Languages: C, C++
        * Thread support: C++ 11 Thread, POSIX Threads (winpthreads)
    * Native Compilation Toolchain
        * `GCC`: 11.5.0
        * `Binutils`: 2.35
        * Thread model: `posix`
        * Languages: C,C++,FORTRAN
    * Build System
        * `make`: GNU Make 4.3
        * `cmake`: 3.26.5
        * `meson`: 1.10.1
        * `rake`: Ruby Make 13.3.1 (Ruby 3.0)
    * Repos
        * Oracle Linux 9 BaseOS
        * Oracle Linux 9 Application Stream
        * Oracle Linux 9 CodeReady Builder
        * Oracle Linux 9 Developer
        * Oracle Linux 9 EPEL

* `cgdoc/mingw-w64-multilib:win32-v1.9-el9`
    * Source
        * [Dockerfile](https://github.com/Jesseatgao/mingw-w64-multilib/releases/tag/win32-v1.9-el9)
    * Base Image
        * Oracle Linux 9
    * Cross Compilation Toolchain
        * `MinGW-w64`: 10.0.0
        * `GCC`: 10.5.0
        * `Binutils`: 2.35.2
        * Thread model: `Win32`
        * Languages: C, C++
        * Thread support: C++ 11 Thread ([mingw-std-threads](https://github.com/meganz/mingw-std-threads)), POSIX Threads ([pthreads4w](https://sourceforge.net/projects/pthreads4w), aka [pthreads-w32](https://github.com/GerHobbelt/pthread-win32))
    * Native Compilation Toolchain
        * `GCC`: 11.5.0
        * `Binutils`: 2.35
        * Thread model: `posix`
        * Languages: C,C++,FORTRAN
    * Build System
        * `make`: GNU Make 4.3
        * `cmake`: 3.26.5
        * `meson`: 1.10.1
        * `rake`: Ruby Make 13.3.1 (Ruby 3.0)
    * Repos
        * Oracle Linux 9 BaseOS
        * Oracle Linux 9 Application Stream
        * Oracle Linux 9 CodeReady Builder
        * Oracle Linux 9 Developer
        * Oracle Linux 9 EPEL

## Usage
* For cross-compiling win32 target: see for example
    * [Cross compile Aria2 i686 on Oracle Linux 9](https://github.com/Jesseatgao/aria2-patched-static-build/blob/master/Dockerfile.i686.x86_64.mingw)
    * [Cross compile common devel packages(header files and libs)](https://github.com/Jesseatgao/mingw-w64-libs)
    * [Cross compile MKVToolNix (mkvmerge)](https://github.com/Jesseatgao/MKVToolNix-static-builds)
* cross-compiling win64 target: see for example
    * [Cross compile Aria2 x86_64 on Oracle Linux 9](https://github.com/Jesseatgao/aria2-patched-static-build/blob/master/Dockerfile.i686.x86_64.mingw)
    * [Cross compile common devel packages(header files and libs)](https://github.com/Jesseatgao/mingw-w64-libs)
    * [Cross compile MKVToolNix (mkvmerge)](https://github.com/Jesseatgao/MKVToolNix-static-builds)
* working with WSL:
1. Create a temporary container from an image, say, cgdoc/mingw-w64-multilib:win32-v1.9-el9
```shell
docker create --name RHEL9-extended cgdoc/mingw-w64-multilib:win32-v1.9-el9
```
2. Export the container as a tar archive
```shell
docker export RHEL9-extended > RHEL9-extended.tar
```
3. Import the distro tar file into WSL
```shell
wsl --import RHEL9-extended . RHEL9-extended.tar
```
4. (optional) Remove the container and the tar file
```shell
docker rm RHEL9-extended
del /f RHEL9-extended.tar
```
5. Run the imported Oracle Linux distro
```shell
wsl -d RHEL9-extended
```
