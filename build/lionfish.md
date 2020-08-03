
# Lionfish

## Android source code

>Lionfish$ repo init -u ssh://android.garmin.com.tw:29419/android/alishan/manifests -b lionfish -m lionfish_v3.81_20200117.xml --repo-url=git://android.garmin.com.tw/tools/repo.git --no-repo-verify

>hydra$ git submodule update --init --recursive

## build
>Lionfish$ docker container start lionfish
>Lionfish$ tmux attach lionfish

>root@c6a9deb073db:/# su build
>build@c6a9deb073db:/$ bash
>build@c6a9deb073db:/$ cd /android/

>build@c6a9deb073db:/android$ . mbldenv.sh

> build@c6a9deb073db:/android$ cat mbldenv.sh
> 
	#!/bin/bash
	###########################################################
	# ALPS(Android4.1 based) build environment profile setting
	###########################################################
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
>build@c6a9deb073db:/android$ . tools/garmin/garmin-wrapper.sh
>build@c6a9deb073db:/android$ glunch
>build@c6a9deb073db:/android$ gmmm vendor/garmin/system/hydra/

## Certificate PKIX exception

### copy cert file

###  change jre secur

The "Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files" answer did not work for me but The BouncyCastle's JCE provider suggestion did.

Here are the steps I took using Java 1.6.0_65-b14-462 on Mac OSC 10.7.5

1) Download these jars:

-   [bcprov-jdk15on-154.jar](https://www.bouncycastle.org/download/bcprov-jdk15on-154.jar)
    
-   [bcprov-ext-jdk15on-154.jar](https://www.bouncycastle.org/download/bcprov-ext-jdk15on-154.jar)
    

2) move these jars to $JAVA_HOME/lib/ext

3) edit $JAVA_HOME/lib/security/java.security as follows: security.provider.1=org.bouncycastle.jce.provider.BouncyCastleProvider
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDk3NDYwNjE5LC04Mjg4MzM1NDIsMTczMT
Y1NDEzNl19
-->