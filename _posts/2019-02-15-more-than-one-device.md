---
title: "error: more than one device/emulator"
date: 2019-02-15 15:08:00 -0400
---

콘솔에서 특정 apk 를 설치하려고 하려면 아래와 같은 오류가 발생합니다.
adb install -r install-something.apk 

error: more than one device/emulator
adb: error: failed to get feature set: more than one device/emulator
- waiting for device -
error: more than one device/emulator

실행 가능한 디바이스 혹은 시뮬레이터가 2개 이상인 경우,
실행할 디바이스(시뮬레이터) 이름을 지정해야 합니다.

사용 가능한 디바이스(시뮬레이터) 목록 조회을 조회합니다.
adb devices -l

List of devices attached
4100a672c89bb1e3       device usb:340000768X product:treltektt model:SM_N910K device:treltektt transport_id:5
emulator-5554          device product:sdk_gphone_x86 model:Android_SDK_built_for_x86 device:generic_x86 transport_id:1

명령을 실행한 디바이스 이름을 
adb -s 4100a672c89bb1e3 install -r install-something.apk 



app installation:
 install [-lrtsdg] [--instant] PACKAGE
 install-multiple [-lrtsdpg] [--instant] PACKAGE...
     push package(s) to the device and install them
     -l: forward lock application
     -r: replace existing application
     -t: allow test packages
     -s: install application on sdcard
     -d: allow version code downgrade (debuggable packages only)
     -p: partial application install (install-multiple only)
     -g: grant all runtime permissions
     --instant: cause the app to be installed as an ephemeral install app
