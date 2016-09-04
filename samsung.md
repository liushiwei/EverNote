---
title: Samsung笔记
tags: ["Android"]
notebook: Android
---

<!-- MarkdownTOC -->

- [安装依赖包](#安装依赖包)
- [删除Overlay](#删除overlay)
- [不编译ODEX](#不编译odex)
- [开机弹错误提示](#开机弹错误提示)

<!-- /MarkdownTOC -->


# 安装依赖包

```shell
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-7-jdk

sudo update-alternatives --config java

sudo apt-get install git gnupg flex bison gperf build-essential zip curl libc6-dev libncurses5-dev:i386 x11proto-core-dev libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-dri:i386 libgl1-mesa-dev g++-multilib mingw32 tofrodos python-markdown libxml2-utils xsltproc zlib1g-dev:i386 dpkg-dev
sudo apt-get install ccache
source ~/.bashrc
#更新GCC
sudo add-apt-repository ppa:ubuntu-toolchain-r/test 
sudo apt-get update

echo export USE_CCACHE=1 >> ~/.bashrc

#解压包
tar -jxvf lollipop-5.1.1_r6-avn-10-8-2016.tar.bz2

cd lollipop-5.1.1_r6-avn 
#添加编译脚本
vi build.sh 
prebuilts/misc/linux-x86/ccache/ccache -M 50G
device/nexell/s5p6818_avn_ref/build.sh -b s5p6818_avn_ref -t android

```

* * *

# 删除Overlay

```shell
#device/nexell/s5p6818_avn_ref/device.mk
#DEVICE_PACKAGE_OVERLAYS := \
        device/nexell/s5p6818_avn_ref/overlay
```

* * *

# 不编译ODEX

```shell
#device/nexell/s5p6818_avn_ref/BoarcConfig.mk
WITH_DEXPREOPT := false
```

# 开机弹错误提示

	frameworks/base/services/core/java/com/android/server/am/ActivityManagerService.java

```java
 if (!Build.isFingerprintConsistent()) {
                Slog.e(TAG, "Build fingerprint is not consistent, warning user");
                mHandler.obtainMessage(SHOW_FINGERPRINT_ERROR_MSG).sendToTarget();
            }
```
	
	framework/base/core/java/android/os/Build.java

```java
 public static boolean isFingerprintConsistent() {
        final String system = SystemProperties.get("ro.build.fingerprint");
        final String vendor = SystemProperties.get("ro.vendor.build.fingerprint");

        if (TextUtils.isEmpty(system)) {  //这里为空
            Slog.e(TAG, "Required ro.build.fingerprint is empty!");
            return false;
        }

        if (!TextUtils.isEmpty(vendor)) {
            if (!Objects.equals(system, vendor)) {
                Slog.e(TAG, "Mismatched fingerprints; system reported " + system
                        + " but vendor reported " + vendor);
                return false;
            }
        }

        return true;
    }
```

	由于ro.build.fingerprint 长度超过了92个字符，修该下面的文件
	system/core/include/cutils/properties.h