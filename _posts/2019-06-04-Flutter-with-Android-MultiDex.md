---
title: "Flutter 에서 Android MultiDex 적용하기"
date: 2019-06-29 15:18:52 -0400
---


FlutterApplication 상속 받아서 MainApplication(임의의 클래스)을 구현한다.

class MainApplication : FlutterApplication() {

    override fun attachBaseContext(base: Context) {
        super.attachBaseContext(base)
        MultiDex.install(this)
    }

}


Manifest.xml 에서 Application 을 변경한다.

<application
  android:name="io.flutter.app.FlutterApplication"
  android:label="flutter_sample"
  android:icon="@mipmap/ic_launcher">
</application>

<application
  android:name=".MainApplication"
  android:label="flutter_sample"
  android:icon="@mipmap/ic_launcher">
</application>

