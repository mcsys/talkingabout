---
title: "Make sure to call FirebaseApp.initializeApp"
date: 2019-04-03 11:10:52 -0400
---


파이어 베이스 초기화를 설정했지만
FirebaseApp.initializeApp(this);

아래와 같은 오류가 발생한 경우,
Make sure to call FirebaseApp.initializeApp(Context) first.



build.gradle 설정에서 플로그인을 추가한다.

apply plugin: 'com.google.gms.google-services'

