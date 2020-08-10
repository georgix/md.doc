Docker build environment
=========================



rsync
-----------

    rsync -arvh zhangjin@172.16.6.11:/media/f4/opt /media/f4

Docker
------------------

- Docker system

    docker system
    docker system info
    docker system info df
    docker system events
    docker config
    docker config ls
    docker network ls
    docker network
    docker network info a506d4725b2f
    docker network inspect a506d4725b2f
    sudo cat /etc/docker/key.json

Flush changes:

    $ sudo systemctl daemon-reload

Restart Docker:

    $ sudo systemctl restart docker

- Docker image

    docker image ls
    docker commit 2e43badecb3f piranha
    docker ps -a

- Docker container

    docker run -it --name piranha-2 -v /media/f4/Piranha:/android -v /media/f4/opt:/opt piranha
    docker container ls
    docker container ls -a
    docker container rm piranha-1
    docker container start piranha-2
    docker container attach piranha-2
    docker container top piranha-1
    docker container diff piranha-1
    docker container update piranha-1

- Docker detach
    Ctrl-p Ctrl-q

## Alchemy

    sudo apt-get install chrpath default-jre diffstat faketime gawk lib32ncurses5 libbz2-dev mtools texinfo tftpd-hpa u-boot-tools

    sudo apt-get install build-essential icecc icecc-monitor chrpath default-jre faketime gawk lib32ncurses5 lib32stdc++6 lib32z1 libbz2-dev nfs-kernel-server texinfo tftpd-hpa u-boot-tools bc

    zhangjin@ubuntu:/media/fusion/RAY/alchemy_morty$ cat /etc/docker/daemon.json
    {
        "data-root": "/media/fusion/Docker",
        "storage-driver": "overlay2",
        "selinux-enabled": true,
        "ipv6": false,
        "insecure-registries" : ["docker-registry.garmin.com"],
        "bip": "192.168.1.1/24",
        "fixed-cidr": "192.168.1.1/24",
        "dns": ["10.130.0.66","10.130.0.67"]
    }

## Android Exynos

    sudo docker build --file=optimus-developer_14.04.dockerfile --build-arg GID=1000 --build-arg UID=1000 --build-arg UNAME=zhangjin  --pull --force-rm --no-cache -t docker-registry.garmin.com/consumer_tools/optimus-developer:14.04 .
## Android 6.0

## Android 4.4

### Lionfish

    sudo apt-get install lsb-release

    zhangjin@ubuntu:/media/f4/Lionfish$ cat mbldenv.sh
    #!/bin/bash
    # ##########################################################
    # ALPS(Android4.1 based) build environment profile setting
    # ##########################################################
    # Overwrite JAVA_HOME environment variable setting if already exists
    # JAVA_HOME=/mtkoss/jdk/1.6.0_45-ubuntu-10.04/x86_64
    JAVA_HOME=/opt/java/jdk1.6.0_45
    export JAVA_HOME

    # Overwrite ANDROID_JAVA_HOME environment variable setting if already exists
    #ANDROID_JAVA_HOME=/mtkoss/jdk/1.6.0_45-ubuntu-10.04/x86_64
    ANDROID_JAVA_HOME=$JAVA_HOME
    export ANDROID_JAVA_HOME

    # Overwrite PATH environment setting for JDK & arm-eabi if already exists
    PATH=$JAVA_HOME:$PWD/prebuilts/gcc/linux-x86/arm/arm-linux-androideabi-4.7/bin:$PWD/prebuilts/gcc/linux-x86/arm/arm-eabi-4.7/bin:$PWD/prebuilts/misc/linux-x86/make:$PATH
    export PATH

    # Add MediaTek developed Python libraries path into PYTHONPATH
    if [ -z "$PYTHONPATH" ]; then
    PYTHONPATH=$PWD/mediatek/build/tools
    else
    PYTHONPATH=$PWD/mediatek/build/tools:$PYTHONPATH
    fi
    export PYTHONPATH

    export ANDROID_NDK_ROOT=/opt/android-ndk-r8e
    export ANDROID_SDK_ROOT=/opt/adt-bundle-linux-x86_64-legacy/sdk

### Lionfish hydra
    04:43:00.250 [ERROR] [org.gradle.BuildExceptionReporter] FAILURE: Build failed with an exception.
    04:43:00.250 [ERROR] [org.gradle.BuildExceptionReporter]
    04:43:00.250 [ERROR] [org.gradle.BuildExceptionReporter] * What went wrong:
    04:43:00.250 [ERROR] [org.gradle.BuildExceptionReporter] A problem occurred configuring root project 'hydra'.
    04:43:00.251 [ERROR] [org.gradle.BuildExceptionReporter] > Could not resolve all dependencies for configuration ':classpath'.
    04:43:00.251 [ERROR] [org.gradle.BuildExceptionReporter]    > Could not resolve com.android.tools.build:gradle:1.0.1.
    04:43:00.251 [ERROR] [org.gradle.BuildExceptionReporter]      Required by:
    04:43:00.252 [ERROR] [org.gradle.BuildExceptionReporter]          :hydra:unspecified
    04:43:00.252 [ERROR] [org.gradle.BuildExceptionReporter]       > Could not GET 'https://jcenter.bintray.com/com/android/tools/build/gradle/1.0.1/gradle-1.0.1.pom'.
    04:43:00.252 [ERROR] [org.gradle.BuildExceptionReporter]          > peer not authenticated

    diff --git a/build.gradle b/build.gradle
    index 0600679f5f..620a0c5394 100644
    --- a/build.gradle
    +++ b/build.gradle
    @@ -26,7 +26,7 @@ allprojects {
        group = 'com.garmin.android.fleet'

        repositories {
    -        jcenter()
    +        jcenter {url "http://jcenter.bintray.com/"}
        }
        
    diff --git a/wscript b/wscript
    index 356357bb0b..8cc1ee3378 100644
    --- a/wscript
    +++ b/wscript
    @@ -238,6 +238,7 @@ def configure(conf):
                conf.start_msg("Checking for Android tools")
                conf.load( 'android_tools', tooldir=tool_dirs )
                tools = conf.get_ndk_path(None)
    +            Logs.info('Ndk path %s' % tools)
                if tools:
                    conf.setenv( '%s-arm' % environment, base_env.derive() )
                    try:
    @@ -267,7 +268,7 @@ def configure(conf):
                            Logs.pprint( 'GREEN', 'Setting up gradle properties: %s' % gradleconfigfile )
                            if not os.path.exists(gradleconfigdir): os.makedirs(gradleconfigdir)
                            gradle_config = conf.path.make_node('gradle.properties')
    mProp.https.proxyHost=mombasa.garmin.com\nsystemProp.https.proxyPort=9119\nsystemProp.https.nonProxyHosts=*.garmin.com|localhost\n\n#end gradle.properties')emProp.http.nonProxyHosts=*.garmin.com|localhost\nsyst temProp.https.proxyHost=mombasa.garmin.com\nsystemProp.https.proxyPort=9119\nsystemProp.https.nonProxyHosts=*.garmin.com|localhost\n\n#end gradle.properties')emProp.http.nonProxyHosts=*.garmin.com|localhost\nsy
                            shutil.move('gradle.properties', gradleconfigdir)

                    # Set wchar size to 16-bit


    @@ -517,7 +518,7 @@ def exec_gradle_build(bld):
        else:
            shellcmd = ' '.join(['gradlew','clean','build'])

    -    shellcmd = ' '.join([shellcmd, '-PprodManifestPath=%s' % os.path.split(os.path.normpath(bld.android_manifest))[0]])
    +    shellcmd = ' '.join([shellcmd, '--debug -PprodManifestPath=%s' % os.path.split(os.path.normpath(bld.android_manifest))[0]])

        try:
            Logs.info( 'Executing gradle to generate Libraries and dependent files..')

    zhangjin@ubuntu:/media/f4/Lionfish/vendor/garmin/system/hydra/submodules/technology/android/fleet-api$ git diff
    diff --git a/tools/buildscript.gradle b/tools/buildscript.gradle
    index 074e513..c0d7983 100644
    --- a/tools/buildscript.gradle
    +++ b/tools/buildscript.gradle
    @@ -3,7 +3,7 @@
        is how the Android Gradle plugin locates the installation */
    project.buildscript {
        repositories {
    -        jcenter()
    +        jcenter {url "http://jcenter.bintray.com/"}
        }
        dependencies {
            classpath 'com.android.tools.build:gradle:1.0.1'

    zhangjin@ubuntu:/media/f4/Lionfish/vendor/garmin/system/hydra/submodules/technology/android/fleet-reference-app$ git diff
    diff --git a/build.gradle.sdk b/build.gradle.sdk
    index f0ac646..28ecb5b 100755
    --- a/build.gradle.sdk
    +++ b/build.gradle.sdk
    @@ -1,6 +1,6 @@
    buildscript {
        repositories {
    -        jcenter()
    +        jcenter {url "http://jcenter.bintray.com/"}^M
        }
        dependencies {
            classpath 'com.android.tools.build:gradle:1.0.1'
    @@ -11,7 +11,7 @@ allprojects {
        group = 'com.garmin.android.fleet'

        repositories {
    -        jcenter()
    +        jcenter {url "http://jcenter.bintray.com/"}^M
        }
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM3NTU5MzUxOF19
-->