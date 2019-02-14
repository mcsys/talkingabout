---
title: "Unable to instantiate activity"
date: 2019-02-15 00:38:00 -0400
---


2019-02-15 00:33:21.393 9758-9758/com.passionvirus.rxandroidsample E/AndroidRuntime: FATAL EXCEPTION: main
    Process: com.passionvirus.rxandroidsample, PID: 9758
    java.lang.RuntimeException: Unable to instantiate activity ComponentInfo{com.passionvirus.rxandroidsample/com.passionvirus.rxandroidsample.ui.TimerTaskActivity}: java.lang.ClassNotFoundException: Didn't find class "com.passionvirus.rxandroidsample.ui.TimerTaskActivity" on path: DexPathList[[zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/base.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_dependencies_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_resources_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_slice_0_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_slice_1_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_slice_2_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_slice_3_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_slice_4_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_slice_5_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_slice_6_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_slice_7_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_slice_8_apk.apk", zip file "/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/split_lib_slice_9_apk.apk"],nativeLibraryDirectories=[/data/app/com.passionvirus.rxandroidsample-5bImaQ97jh8yBqSy4p6QAg==/lib/x86, /system/lib]]
        at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:2843)
        at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:3048)
        at android.app.servertransaction.LaunchActivityItem.execute(LaunchActivityItem.java:78)
        at android.app.servertransaction.TransactionExecutor.executeCallbacks(TransactionExecutor.java:108)
        at android.app.servertransaction.TransactionExecutor.execute(TransactionExecutor.java:68)
        at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1808)
        at android.os.Handler.dispatchMessage(Handler.java:106)
        at android.os.Looper.loop(Looper.java:193)
        at android.app.ActivityThread.main(ActivityThread.java:6669)
        at java.lang.reflect.Method.invoke(Native Method)
        at com.android.internal.os.RuntimeInit$MethodAndArgsCaller.run(RuntimeInit.java:493)
        at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:858)
        
Kotlin 에서 클래스의 파일 확장자가 kt 가 아니면 오류가 발생할 수 있다

TimerTaskActivity 파일명을 TimerTaskActivity.kt 로 변경하면 문제를 해결할 수 있다.
