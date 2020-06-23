---
title: "FAILURE: Build failed with an exception."
date: 2020-06-23 11:55:13 -0400
---


> Task :appGoogle:minifyReleaseWithProguard FAILED

Deprecated Gradle features were used in this build, making it incompatible with Gradle 7.0.
Use '--warning-mode all' to show the individual deprecation warnings.
See https://docs.gradle.org/6.1.1/userguide/command_line_interface.html#sec:command_line_warnings
319 actionable tasks: 2 executed, 317 up-to-date
Warning: there were 7 unresolved references to program class members.
         Your input classes appear to be inconsistent.
         You may need to recompile the code.
         (http://proguard.sourceforge.net/manual/troubleshooting.html#unresolvedprogramclassmember)

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':appGoogle:minifyReleaseWithProguard'.
> java.io.IOException: Please correct the above warnings first.

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 7s



R8 에 대한 설정을 비활성화하면 정상적으로 빌드 가능하다.

minifyEnabled false
