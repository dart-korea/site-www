---
title: 이펙티브 Dart
description: 다트를 일관성있고, 유지보수 가능하고, 효과적으로 사용 할 수 있는 최고의 방법들을 소개합니다.
permalink: /guides/language/effective-dart
nextpage:
  url: /guides/language/effective-dart/style
  title: Style
---

최근 몇 년 동안, 우리는 많은 양의 Dart 코드를 작성하였고, 많은 것들을 배웠습니다. 우리는 여러분들과 함께 일관성 있고, 강직하고, 빠른 코드를 작성하는 법을 살펴볼 것입니다. 여기에 두 가지 중요한 주제가 있습니다.

 1. **일관성을 유지하십시오.** 코드의 포매팅과 컨벤션과 관련해서, 
    어느 쪽이 더 나은지는 주관적인 부분이 강하며 해결할 수 없습니다. 하지만 *일관성*을 유지하는것이 객관적으로 도움이 된다는 것 입니다.

    만약 두 개의 코드 조각이 다르게 보인다면, 그건 두 개의 코드가 *각각* 다른 뜻으로 표현되었다는 것입니다. 몇몇 코드가 눈에 띄어야 한다면, 그에 따른 유용한 이유가 있어야 합니다.

 2. **간략히 하십시오.** Dart는 C, Java, JavaScript 등등
    많은 언어의 문법과 표현을 상속받아 친숙하게 설계되었습니다. 하지만 다른 언어들이 제공하는
    것들을 개선할 여지가 많았기 때문에, 다트를 만들었습니다.
    우리는 여러분들이 더욱 간략하고 쉽게 여러분들의 의도를 표현하도록 돕기 위해서
    문자열 보간에서 초기화 형식까지, 많은 기능을 추가했습니다.
    
    만약 어떤것을 표현하기위해 방법이 여러가지라면, 
    여러분들은 일반적으로 가장 간략한 방법을 선택해야 합니다.
    전체 프로그램을 한 줄에 짜 넣는 데 있어 자신을 [코드 골프][code golf]를 해야한다는 것은 아닙니다. 목표는 *밀도*가 아닌 *경제적* 인 코드입니다.

[code golf]: https://en.wikipedia.org/wiki/Code_golf

Dart 분석기는 여러분들이 코드를 좋고 일관성 있게 짜도록 도와주는 린터를 가지고 있습니다.
가이드라인을 따르는 데 도움이 되는 린터 법칙이 있다면, 가이드라인이 해당 규칙에 연결됩니다. 여기 예시가 있습니다: 

{% include linter-rule.html rule="prefer_collection_literals" %}

[린터 규칙 활성화](/guides/language/analysis-options#enabling-linter-rules)
에 대한 도움말은 
[정적 분석 사용자 정의 문서](/guides/language/analysis-options)를 참조하십시오.

## 가이드

이해를 쉽게 돕기 위해서 가이드을 몇몇 페이지로 분리하였습니다:

  * **[스타일 가이드][style guide]** &ndash; 코드를 배치하고 구성하기위한 규칙 
    또는 최소한 [dartfmt]가 음리하지 않는 부분을 정의합니다.
    또한 스타일 가이드는 식별자의 형식을 지정합니다: `camelCase`, `using_underscores`, 등등.
    
  * **[문서화 가이드][documentation guide]** &ndash; 주석에 무엇이 들어가는 지에
    대해 알아야 할 모든 것을 알려줍니다.
    문서 주석 및 일반 실행 코드 주석입니다.

  * **[사용법 가이드][usage guide]** &ndash; 
    언어의 기능을 최대한 활용하여 동작을 구현하는 방법을 알려줍니다.
    문법이나 표현에 있다면 여기에서 다룹니다.

  * **[설계 가이드][design guide]** &ndash; 가장 가볍게 읽을 수 있는
    가이드이지만 가장 넓은 범위의 안내서입니다.
    라이브러리에 일관되고 사용 가능한 API 설계에 대해 배운 내용을 다룹니다.
    타입 시그니처 또는 선언인 경우에는 이를 넘어갑니다.

모든 가이드라인에 대한 링크는, [요약](#summary-of-all-rules)을 참고하세요.

{% comment %}
<aside class="alert alert-info" markdown="1">
  **Have feedback on the guides?** <br>
  Please create a [new issue][] or comment on one of our [existing issues][].

  [new issue]: {{site.repo.this}}/issues/new
  [existing issues]: {{site.repo.this}}/issues?q=is%3Aopen+is%3Aissue+label%3AEffectiveDart
</aside>
{% endcomment %}

[dartfmt]: https://github.com/dart-lang/dart_style#readme
[style guide]: /guides/language/effective-dart/style
[documentation guide]: /guides/language/effective-dart/documentation
[usage guide]: /guides/language/effective-dart/usage
[design guide]: /guides/language/effective-dart/design

## 가이드는 읽는 방법

각각의 가이드는 몇개의 섹션으로 쪼개어져있습니다. 섹션은 가이드라인의 목록을 포함하고 있습니다.
각각의 가이드는 다음 단어 중 하나로 끝납니다:

* **하세요** 항상 따라야 하는 사례를 설명합니다.
  해당하는 가이드라인을 지키지 않을 이유는 거의 없을 것입니다.

* **하지마세요** 거의 좋지 못한 아이디어에 관해서 설명합니다.
  다행히도 언어의 역사가 짧기 때문에, 다른 언어들에 비해서 많진 않습니다.
  
* **권장합니다** 여러분들이 *따라야* 하는 가이드라인입니다.
 하지만 그렇지 않은 경우가 있을 수도 있습니다.
 여러분들이 따르지 않을 땐, 해당 가이드라인에 대해서 모든 의미를 이해하고 있어야 합니다.

* **피하세요** 여러분들이 하지 말아야 할 것들이지만, 
  드문 경우로 좋은 이유가 있을 수 있습니다.

* **고려해보세요** 상황, 전례 및 자신의 취향에 따라 따르거나 원하지 않는 가이드라인입니다.

몇몇 가이드라인은 *적용하지 말아야* 할 경우에 대한 **예외**에 관해서 설명합니다.

목록에 나와 있는 예외는 완전한 것이 아닐 수도 있습니다.&mdash;다른 경우에 대해서는 여러분들이 판단해야 할 수도 있습니다.

말이안되는것 처럼 들릴수 있습니다.
하지만 가이드라인들은 그렇게 나쁘진 않습니다.
대다수의 가이드라인은 상식선이며, 우린 모두 합리적인 사람들입니다.
어쨋든, 목표는 멋지고, 읽기 좋으며, 유지보수 가능한 코드를 작성하는 것 입니다.

## 어휘

가이드라인을 간략히 유지하기 위해서,
각각 다른 다트 구성을 지칭하기 위해 축약된 용어를 사용할 것입니다.

* **라이브러리 멤버**는 최상위의 필드, 게터, 세터, 또는 함수입니다.
  기본적으로는 타입이 아닌 최상위의 모든 것 입니다.

* **클래스 멤버**는 클래스 안에 선언된 생성자, 필드, 게터, 세터, 함수, 또는 연산자 입니다.
  클래스 멤버는 instance 또는 static, abstract 또는 concrete일 수 있습니다.

* **맴버**는 라이브러리 멤버이거나, 클래스 멤버입니다.

* **변수**는 우리가 보통 사용할 때, 최상위 변수, 파라미터 그리고 지역 변수를 지칭합니다.
  변수는 static 또는 instance 필드를 포함하지 않습니다.

* **타입**은 이름 지어진 타입 선언입니다: class, typedef 또는 enum.

* **속성**은 최상위 변수, 게터(클래스 안 또는 최상위, instance 또는 static), 세터(게터와 동일), 또는 필드(instance 또는 static)입니다.
  대충 "필드와 유사한"이름의 생성자와 같습니다.

## 규칙 요약

{% include_relative toc.md %}
