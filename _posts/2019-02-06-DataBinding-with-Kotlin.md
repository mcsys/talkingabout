---
title: "DataBinding with Kotlin"
date: 2019-02-06 15:40:00 -0400
---

apply plugin: 'kotlin-android'                       
apply plugin: 'kotlin-kapt'
android {
    ....
    dataBinding {
        enabled = true
    }
}
dependencies {
    ...
    // notice that the compiler version must be the same than our gradle version
    kapt 'com.android.databinding:compiler:2.3.1'
}
