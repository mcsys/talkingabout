---
title: "Found an unexpected Mach-O header code"
date: 2019-02-19 10:59:12 -0400
---


Found an unexpected Mach-O header code

로그가 다음과 같은 경우,
Failed to generate distribution items with error

잘못된 바이너리가 프레임워크 등이 포함되어 있는지 살펴보고 제거한다.
Remove any frameworks or folders with frameworks from Build Phases -> Copy Bundle Resources:
