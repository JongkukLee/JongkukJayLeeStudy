---
layout: default
---
# NodeJsAddon
---

>GYP (generate your projects) is a build automation tool. GYP is created by Google to generate native IDE project files (such as Visual Studio Code and Xcode) for building the Chromium web browser and is licensed as open source software using the BSD software license.

>node-gyp is a cross-platform command-line tool written in Node.js for compiling native addon modules for Node.js. It bundles the gyp project used by the Chromium team and takes away the pain of dealing with the various differences in build platforms.

>Node.js native addon build tool. node-gyp is a cross-platform command-line tool written in Node.js for compiling native addon modules for Node.js. ... If you have a native addon for node that still has a wscript file, then you should definitely add a binding.gyp file to support the latest versions of node.

>wscript.exe is a Windows service that allows you to execute VBScript files.


[https://github.com/nodejs/node-gyp](https://github.com/nodejs/node-gyp)

[https://github.com/felixrieseberg/windows-build-tools](https://github.com/felixrieseberg/windows-build-tools)

[https://nodejs.org/dist/latest-v8.x/docs/api/addons.html#addons_c_addons](https://nodejs.org/dist/latest-v8.x/docs/api/addons.html#addons_c_addons)


https://www.youtube.com/watch?v=VPhPOEpZ3cI

https://chromium.googlesource.com/chromium/src/+/master/docs/windows_build_instructions.md


https://medium.com/dailyjs/how-to-build-v8-on-windows-and-not-go-mad-6347c69aacd4

1. npm install -g node-gyp
2. npm install --global --production windows-build-tools
3. input binding.gyp, hello.cc, hello.js
4. node-gyp configure --msvs_version=2015 --python C:\Users\jlee465\.windows-build-tools\python27\python.exe
5. node-gyp build
6. node hello.js
