---
title: "Rxbinding3 에서 Unresolve reference: RxView 발생 이슈"
date: 2019-07-06 17:32:23 -0400
---

RxView.clicks(view).
            .throttleFirst(1000, TimeUnit.MILLISECONDS, AndroidSchedulers.mainThread())

view.clicks()
            .throttleFirst(1000, TimeUnit.MILLISECONDS, AndroidSchedulers.mainThread())
            
변경해주면 된다.

