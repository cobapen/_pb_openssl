
# _pb_openssl

repository for distributing prebuilt openssl shared libraries as git submodule

## add as submodule

    git submodule add https://github.com/cobapen/_pb_openssl

## update

checkout to work locally

    git checkout --recursive https://github.com/cobapen/_pb_openssl

1. Install MSYS (for configure & nasm) and Perl for Windows. 
    - https://www.msys2.org/
    - https://www.perl.org/get.html#win32
2. open: Visual Studio Build Tools Command Prompt (x64 Visual Studio 20**)
3. run: perl Configure VC-WIN64A
4. run: nmake
5. run: nmake test
6. copy: libssl.lib and libcrypto.lib
7. copy: libssl-3-x64.dll and libcrypto-3-x64.dll
8. copy: work/include/openssl  (*.in and __DECC_* files can be deleted)
9. copy: work/ms/applink.c to /include/openssl

do not commit pdb files. It may contain sensitive information. 

### CMake

example:

    if (WIN32 AND MSVC_TOOLSET_VERSION EQUAL 143)
        set(OPENSSL_ROOT_DIR    lib/_pb_openssl/prebuilt/msvs2022-x64)
    endif()