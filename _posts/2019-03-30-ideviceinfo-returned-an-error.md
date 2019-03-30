---
title: "ideviceinfo returned an error"
date: 2019-03-30 15:50:12 -0400
---

Flutter Debug 실행시 아래와 같은 오류가 발생

Exception: ideviceinfo returned an error:
ERROR: Could not connect to lockdownd, error code -21

아래를 하나씩 실행
(brew install --HEAD usbmuxd 요기까지만 진행해도 정상적으로 debug가 되긴 한다)

brew update
brew uninstall --ignore-dependencies libimobiledevice
brew uninstall --ignore-dependencies usbmuxd
brew install --HEAD usbmuxd
brew unlink usbmuxd
brew link usbmuxd
brew install --HEAD libimobiledevice
brew install ideviceinstaller

