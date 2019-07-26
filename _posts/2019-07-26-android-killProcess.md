---
title: "Unresolve reference: viewModels"
date: 2019-07-17 17:04:09 -0400
---


아래와 같은 명령어를 통해서 앱을 종료하는 경우,
android.os.Process.killProcess(android.os.Process.myPid())

앱이 정상적인 프로세스로 종료되지 않을수 있다
(onPause / onDestory 등이 호출되지 않는다)


가급적이면 사용하지 않는 것이 좋다
