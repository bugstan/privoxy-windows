# Privoxy for Windows
![MSBuild](https://github.com/xinlake/privoxy-windows/workflows/MSBuild/badge.svg)

Build and debug [Privoxy](https://www.privoxy.org/) using Visual Studio 2019 on Windows. 
privoxy-windows will follow up the official version.

* privoxy

The privoxy.exe project, depends on mbedtls project, it was configured as windows console application with following features enabled:
```C
#define FEATURE_ACL
#define FEATURE_GRACEFUL_TERMINATION
#define FEATURE_CONNECTION_KEEP_ALIVE
#define FEATURE_CLIENT_TAGS
#define FEATURE_HTTPS_INSPECTION
#define FEATURE_HTTPS_INSPECTION_MBEDTLS
```

* mbedtls

[Mbed TLS](https://tls.mbed.org/) Visual Studio static library.

* dftables

This program is used to generate the source file `chartables.c` which is needed by privoxy.

# Build
Download source code and save to a directory, e.g. `Source-Privoxy`, before you build, you might like to know that project intermediate directory is under `Source-Privoxy\.build` and output directory is under `Source-Privoxy\.target`. You can change these settings in the project property page.

1, Open `privoxy.sln` with Visual Studio 2019

2, Build dftables project, Goto the output directory (e.g. `Source-Privoxy\.target\x64\Debug`) and run it to generate the `chartables.c` file:
```
dftables.exe > "..\..\..\privoxy-3.0.29\pcre\chartables.c"
```

3, Build privoxy project.

![](https://github.com/xinlake/privoxy-windows/raw/master/Assets/screen-3.0.29.jpg)
