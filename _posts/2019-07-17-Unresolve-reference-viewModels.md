---
title: "Unresolve reference: viewModels"
date: 2019-07-17 17:04:09 -0400
---


androidx.fragment.app.viewModels 를 찾지 못해서
Unresolve reference: viewModels 발생하는 경우,

dependencies {
  implementation "androidx.fragment:fragment-ktx:$rootProject.fragment_version"
}

$rootProject.fragment_version 을 1.1.0-alpha03 이상으로 변경한다
(1.1.0-alpha01 / 1.1.0-alpha02 의 경우 내부 구현이 조금 다르다)
