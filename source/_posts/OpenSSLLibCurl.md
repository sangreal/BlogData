title: "Build Scripts for OpenSSL and Libcurl for Android"
date: 2016-04-30 18:37:37
tags: [Android, Github]
---

### Build Script for OpenSSL and Libcurl for Android

This script is for the compilation of OpenSSL and Libcurl.
For libcurl there is a limitation, it cannot build for version above `7.46.0`

Tested in Mac OSX El Capitan

#### Instructions:
specify the version of OpenSSL and Libcurl. The scripts will download them automatically.


>  **OpenSSL** :  run buildOpenSSL.sh to build x86 armv5 armv7 libraries

>  **Libcurl** :  run buildLibCurl.sh to build x86 armv5 armv7 libraries



You can find it [here](https://github.com/sangreal/AndroidOpenSSL)
