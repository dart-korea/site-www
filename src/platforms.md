---
title: 플랫폼
description: "모바일 앱, 웹 앱, 커맨드 라인 앱, 백엔드, 더 많은 곳에서 Dart를 사용할 수 있습니다."
toc: true
---

Dart를 사용하여 간단한 스크립트를 작성할 수도 있지만, 완전한 기능을 가진 앱을 작성할 수도 있습니다.
모바일 앱, 웹 앱, 커맨드 라인 스크립트, 서버 사이드 앱 중 어떤 걸 만들어도 Dart를 해결책으로 사용할 수 있습니다.

유연한 컴파일러 기술은 여러분이 목표로 하고 있는 플랫폼과 목적에 따라 
Dart 코드가 서로 다른 방법으로 동작할 수 있게 합니다.

  * **Dart Native**: 기기 (모바일, 데스크탑, 서버 등)를 대상으로 하는 프로그램을 작성할 때 사용할 수 있습니다.
  Dart Native는 Dart VM과 JIT (just-in-time) 컴파일 방식과 
  머신 코드 (machine code)를 만들기 위한 AOT (ahead-of-time) 컴파일 방식을 모두 지원합니다.
  * **Dart Web**: 웹을 대상으로 하는 프로그램을 작성할 때 사용할 수 있습니다.
  Dart Web은 개발할 때 사용하는 컴파일러 (`dartdevc`)와 프로덕션을 만들 때 사용하는 컴파일러 (`dart2js`)를 모두 지원합니다.

<img src="{% asset platforms.svg @path %}" width="800px" alt="Dart platform">

## Dart Native (VM JIT와 AOT)

Dart Native는 Dart 코드를 모바일, 데스크탑, 서버 앱에서 동작하는 네이티브 ARM 또는 X64 머신 코드로 컴파일하여 동작시킬 수 있습니다.

[Flutter framework]({{site.flutter}})는 인기 있는 멀티 플랫폼 UI 툴킷으로,
Dart Native를 사용하여 모바일이나 데스크탑 기기를 지원하고 있습니다.

더 자세한 정보는:
* [Flutter get started documentation]({{site.flutter}}/docs/get-started/)
* [Get started: command-line and server apps](/tutorials/server/get-started)
* [Write command-line apps](/tutorials/server/cmdline)
* [Write HTTP clients and servers](/tutorials/server/httpserver)

### 번개처럼 빠른 개발 흐름 (Dart VM JIT)

빠른 개발 싸이클은 반복 작업에서 중요합니다.

Dart VM은 just-in-time 컴파일러 (JIT)를 가지며,
iOS 기기에서 필요로 하는 pure interpretation과 런타임 최적화를 둘 다 지원합니다.

더 자세한 정보는 [`dart` VM tool](/tools/dart-vm)을 살펴보세요.

### 프로덕션 코드 최적화하기 (Dart AOT)

앱을 프로덕션으로 배포할 준비가 되었을 때,
Dart AOT 컴파일러를 사용해 어플리케이션 코드를 ARM 또는 X64 머신 코드로 ahead-of-time 컴파일할 수 있습니다.
AOT 컴파일된 앱은 빠르게 시작되고 부드럽게 동작합니다.

AOT 컴파일된 코드는 견고한 Dart 타입 시스템과 빠른 객체 할당을 사용한 메모리 관리 및 [generational garbage
collector.](https://medium.com/flutter-io/flutter-dont-fear-the-garbage-collector-d69b3ff1ca30)를 가진 
효율적인 Dart 런타임에서 동작합니다.

더 자세항 정보는 [`dart2aot` tool](/tools/dart2aot)을 살펴보세요.

## Dart Web (JavaScript)

Dart Web enables running Dart code on web platforms powered by
JavaScript. With Dart Web, you compile Dart code to JavaScript code, which in
turn runs in a browser — for example, [V8](https://v8.dev/) inside
[Chrome](https://www.google.com/chrome/).

The [Flutter framework]({{site.flutter}}), a popular multi-platform UI toolkit,
is powered by Dart Web when targeting web apps. The
[AngularDart]({{site.angulardart}}) framework, a popular web app toolkit, is
also powered by Dart Web.


More information: [Get started: web apps](/tutorials/web/get-started)

### Lightning fast developer workflow (Dart dev compiler)

The Dart dev compiler (dartdevc) is a Dart-to-JavaScript compiler
that's optimized for quick turnaround. Instead of using dartdevc directly,
you use it with `webdev`, a tool that supports core developer tasks such as
running, debugging, and building.

More information:
* [`dartdevc` compiler](/tools/dartdevc)
* [`webdev` tool](/tools/webdev)

### Optimized production code (Dart JS compiler)

The `dart2js` tool compiles Dart code to fast, compact, deployable JavaScript.
It employs techniques such as dead-code elimination

More information:
* [Deployment tips](/web/deployment)
* [`dart2js` compiler](/tools/dart2js)
* [`webdev` tool](/tools/webdev)
