## Native Dependencies for Sigar

http://support.hyperic.com/display/SIGAR/Home

I've included native dependencies for Mac and Windows.

This is for pushing onto clojars following the article here

http://nakkaya.com/2010/04/05/managing-native-dependencies-with-leiningen/

-----

The native libs have to be compiled and then the files are put in the `native` directory like this:

    /native/<platform>/<architecture>/
   
for example, for the mac, it has to be placed:

    /native/macosx/x86/libsigar-universal-macosx.dylib
    
The naming conventions are:
   
    Platforms:
    ---------------------
    Mac OS X -> macosx
    Windows  -> windows
    Linux    -> linux
    SunOS"   -> solaris

    Architectures
    --------------------
    amd64    -> x86_64
    x86_64   -> x86_64
    x86      -> x86
    i386     -> x86
    arm      -> arm
    sparc    -> sparc


Then jar them up:

    jar -cMf sigar-native-deps-<version>.jar native

and push to cljars

    scp pom.xml sigar-native-deps-<version>.jar clojars@clojars.org: