---
title: "ideviceinfo returned an error"
date: 2019-03-30 15:50:12 -0400
---

Flutter Debug 실행시 아래와 같은 오류가 발생

Exception: ideviceinfo returned an error:
ERROR: Could not connect to lockdownd, error code -21

아래를 하나씩 실행
(brew uninstall --ignore-dependencies libimobiledevice 이것만 실행하면 오류 해결 가능)

brew update
brew uninstall --ignore-dependencies libimobiledevice
brew uninstall --ignore-dependencies usbmuxd
brew install --HEAD usbmuxd
brew unlink usbmuxd
brew link usbmuxd
brew install --HEAD libimobiledevice
brew install ideviceinstaller

