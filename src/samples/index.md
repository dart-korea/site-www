---
title: 언어 샘플
description: 자연스럽게 큰 예제와 이어지는 Dart 예제
---

아래 컬렉션이 하나도 빠짐없이 완벽한 건 아닙니다.
아래 컬렉션은 예제를 통해 배우는 걸 좋아하는 사람들을 위해 간단히 Dart를 소개합니다.
언어 및 라이브러리 살펴보기를 통해 더 자세히 Dart에 대해 살펴보세요.

<div class="card-grid">
  <div class="card">
    <h3><a href="/guides/language/language-tour">언어 살펴보기</a></h3>
    <p>
      Dart 언어를 예제와 함께 포괄적으로 살펴봅니다.
      이 페이지 안에 존재하는 대부분의 <em>read more</em> 링크는 언어 살펴보기로 이어집니다.
    </p>
  </div>
  <div class="card">
    <h3><a href="/guides/libraries/library-tour">라이브러리 살펴보기</a></h3>
    <p>
      Dart 핵심 라이브러리를 예제와 함께 소개합니다.
      built-in types, collections, date와 time, stream 등을 어떻게 사용하는 지 살펴봅니다.
    </p>
  </div>
</div>


## Hello World

모든 앱은 하나의 `main()` 함수를 가집니다.
콘솔에 텍스트를 표시하려면 최상위 함수인 `print()` 를 사용할 수 있습니다.

<?code-excerpt "misc/test/samples_test.dart (hello-world)"?>
{% prettify dart %}
void main() {
  print('Hello, World!');
}
{% endprettify %}


## 변수 (Variables)

type-safe Dart 코드일지라도 대부분의 변수에는 명시적 타입을 필요로 하지 않습니다.
타입 추론이 있기 때문입니다.

<?code-excerpt "misc/test/samples_test.dart (var)"?>
{% prettify dart %}
var name = 'Voyager I';
var year = 1977;
var antennaDiameter = 3.7;
var flybyObjects = ['Jupiter', 'Saturn', 'Uranus', 'Neptune'];
var image = {
  'tags': ['saturn'],
  'url': '//path/to/saturn.jpg'
};
{% endprettify %}

[Read more](/guides/language/language-tour#variables)
기본 값, `final` 과 `const` 키워드, 정적 타입 등을 포함하는 Dart의 변수에 대해 살펴보세요.

## 제어 흐름 문 (Control flow statement)

Dart는 흔히 사용하는 제어 흐름 문을 지원합니다.

<?code-excerpt "misc/test/samples_test.dart (control-flow)"?>
{% prettify dart %}
if (year >= 2001) {
  print('21st century');
} else if (year >= 1901) {
  print('20th century');
}

for (var object in flybyObjects) {
  print(object);
}

for (int month = 1; month <= 12; month++) {
  print(month);
}

while (year < 2016) {
  year += 1;
}
{% endprettify %}

[Read more](/guides/language/language-tour#control-flow-statements) 
`break` 와 `continue`, `switch` 와 `case`, `assert` 를 포함하는 Dart의 제어 흐름 문에 대해 살펴보세요.

## 함수 (Functions)

각 함수의 인수와 반환 값에 타입을 정의하는 걸 [권장합니다](/guides/language/effective-dart/design#types).

<?code-excerpt "misc/test/samples_test.dart (functions)"?>
{% prettify dart %}
int fibonacci(int n) {
  if (n == 0 || n == 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}

var result = fibonacci(20);
{% endprettify %}

단일 문을 포함하고 있는 함수에서 간단히 사용할 수 있는 `=>` (_arrow_) 문법이 있습니다.
이 문법은 익명 함수를 인수로 전달하고자 할 때 특히 유용하게 사용할 수 있습니다.

<?code-excerpt "misc/test/samples_test.dart (arrow)"?>
{% prettify dart %}
flybyObjects.where((name) => name.contains('turn')).forEach(print);
{% endprettify %}

(`where()` 의 인수인) 익명 함수를 표시하는 것 외에도,
이 코드에서는 함수를 인수로 사용 가능하다는 것을 보여줍니다.
최상위 `print()` 함수가 `forEach()` 에 인수로 전달되고 있습니다.

[Read more](/guides/language/language-tour#functions) 
선택적 파라미터, 기본 파라미터 값, lexical scope를 포함하는 Dart의 함수에 대해 살펴보세요.

## 주석 (Comments)

Dart 주석은 보통 `//` 로 시작합니다.

{% prettify dart %}
// This is a normal, one-line comment.

/// This is a documentation comment, used to document libraries,
/// classes, and their members. Tools like IDEs and dartdoc treat
/// doc comments specially.

/* Comments like these are also supported. */
{% endprettify %}

[Read more](/guides/language/language-tour#comments)
문서화 도구가 어떻게 동작하는 지를 포함하는 Dart의 주석에 대해서 살펴보세요.

## Imports

다른 라이브러리에서 정의한 API에 접근하기 위해 `import` 를 사용합니다.

<?code-excerpt "misc/test/samples_test.dart (import)" plaster="none"?>
{% prettify dart %}
// Importing core libraries
import 'dart:math';

// Importing libraries from external packages
import 'package:test/test.dart';

// Importing files
import 'path/to/my_other_file.dart';
{% endprettify %}

[Read more](/guides/language/language-tour#libraries-and-visibility)
라이브러리 접두사, `show` 와 `hide`, `deferred` 키워드를 이용한 레이지 로딩을 포함하는
Dart의 라이브러리와 visibility에 대해 살펴보세요.

## Classes

여기 세 개의 속성과, 두개의 생성자, 그리고 하나의 메서드를 가진 class 예제가 있습니다.
속성 중 하나를 직접 설정할 수 없으므로, getter 메서드를 사용해서 정의합니다. (변수 대신 사용합니다)

{% comment %}
The linter rule sort_constructors_first made us put the getter below
the constructors: https://github.com/dart-lang/linter/issues/859.
{% endcomment %}

<?code-excerpt "misc/lib/samples/spacecraft.dart (class)"?>
{% prettify dart %}
class Spacecraft {
  String name;
  DateTime launchDate;

  // Constructor, with syntactic sugar for assignment to members.
  Spacecraft(this.name, this.launchDate) {
    // Initialization code goes here.
  }

  // Named constructor that forwards to the default one.
  Spacecraft.unlaunched(String name) : this(name, null);

  int get launchYear =>
      launchDate?.year; // read-only non-final property

  // Method.
  void describe() {
    print('Spacecraft: $name');
    if (launchDate != null) {
      int years =
          DateTime.now().difference(launchDate).inDays ~/
              365;
      print('Launched: $launchYear ($years years ago)');
    } else {
      print('Unlaunched');
    }
  }
}
{% endprettify %}

`Spacecraft` 클래스를 아래 예제처럼 사용할 수 있습니다.

<?code-excerpt "misc/test/samples_test.dart (use class)" plaster="none"?>
{% prettify dart %}
var voyager = Spacecraft('Voyager I', DateTime(1977, 9, 5));
voyager.describe();

var voyager3 = Spacecraft.unlaunched('Voyager III');
voyager3.describe();
{% endprettify %}

[Read more](/guides/language/language-tour#classes) 
initializer 목록, 선택적 `new` 와 `const`, 리디렉션 생성자, `factory` 생성자, getter, setter 등을 포함하는
Dart의 클래스에 대해서 살펴보세요.

## 상속 (Inheritance)

Dart는 단일 상속을 가집니다.

<?code-excerpt "misc/lib/samples/spacecraft.dart (extends)"?>
{% prettify dart %}
class Orbiter extends Spacecraft {
  num altitude;
  Orbiter(String name, DateTime launchDate, this.altitude)
      : super(name, launchDate);
}
{% endprettify %}

[Read more](/guides/language/language-tour#extending-a-class) 
클래스를 확장하는 법과 선택적 `@override` 어노테이션 등에 대해 살펴보세요.


## 믹스인 (Mixins)

믹스인은 여러 클래스 계층에서 코드를 재사용할 수 있게 합니다. 아래 클래스는 믹스인으로써 사용 가능합니다.

<?code-excerpt "misc/lib/samples/spacecraft.dart (mixin)"?>
{% prettify dart %}
class Piloted {
  int astronauts = 1;
  void describeCrew() {
    print('Number of astronauts: $astronauts');
  }
}
{% endprettify %}

믹스인의 기능을 클래스에 추가하려면, 믹스인으로 클래스를 확장하면 됩니다.

<?code-excerpt "misc/lib/samples/spacecraft.dart (mixin use)" replace="/with/[!$&!]/g"?>
{% prettify dart %}
class PilotedCraft extends Spacecraft [!with!] Piloted {
  // ···
}
{% endprettify %}

이제 `PilotedCraft` 는 `describeCrew()` 메서드와 `astronauts` 필드를 가집니다.

[Read more](/guides/language/language-tour#adding-features-to-a-class-mixins)
믹스인에 대해 더 살펴보세요.

## 인터페이스와 추상 클래스 (Interfaces and abstract classes)

Dart에는 `interface` 키워드가 없습니다. 대신 모든 클래스가 암시적으로 인터페이스를 정의합니다.
따라서 모든 클래스로 구현할 수 있습니다.

<?code-excerpt "misc/lib/samples/spacecraft.dart (implements)"?>
{% prettify dart %}
class MockSpaceship implements Spacecraft {
  // ···
}
{% endprettify %}

[Read more](/guides/language/language-tour#implicit-interfaces)
암시적 인터페이스에 대해 더 살펴보세요.

구상 클래스 (concrete class)를 통해 확장 (또는 구현)될 추상 클래스 (abstract class)를 만들 수 있습니다.
추상 클래스는 (비어있는 바디를 가진) 추상 메서드를 가질 수 있습니다.

<?code-excerpt "misc/lib/samples/spacecraft.dart (abstract)" replace="/abstract/[!$&!]/g"?>
{% prettify dart %}
[!abstract!] class Describable {
  void describe();

  void describeWithEmphasis() {
    print('=========');
    describe();
    print('=========');
  }
}
{% endprettify %}
`Describable` 을 확장한 모든 클래스는 확장한 구현체의 `describe()`를 호출하는,
`describeWithEmphasis()` 메서드를 가집니다.

[Read more](/guides/language/language-tour#abstract-classes)
추상 클래스와 메서드에 대해 살펴보세요.


## Async

콜백 지옥을 비하고 코드를 더 가독성 좋게 만들기 위해 `async` 와 `await` 를 사용할 수 있습니다.

<?code-excerpt "misc/test/samples_test.dart (async)" replace="/async/[!$&!]/g"?>
{% prettify dart %}
const oneSecond = Duration(seconds: 1);
// ···
Future<void> printWithDelay(String message) [!async!] {
  await Future.delayed(oneSecond);
  print(message);
}
{% endprettify %}

위 메서드는 아래와 동일합니다.

<?code-excerpt "misc/test/samples_test.dart (Future.then)"?>
{% prettify dart %}
Future<void> printWithDelay(String message) {
  return Future.delayed(oneSecond).then((_) {
    print(message);
  });
}
{% endprettify %}
 
다음 예제에서는 `async` 와 `await` 가 비동기 코드를 어떻게 읽기 쉽게 만드는 지 보여줍니다.

<?code-excerpt "misc/test/samples_test.dart (await)"?>
{% prettify dart %}
Future<void> createDescriptions(Iterable<String> objects) async {
  for (var object in objects) {
    try {
      var file = File('$object.txt');
      if (await file.exists()) {
        var modified = await file.lastModified();
        print(
            'File for $object already exists. It was modified on $modified.');
        continue;
      }
      await file.create();
      await file.writeAsString('Start describing $object in this file.');
    } on IOException catch (e) {
      print('Cannot create description for $object: $e');
    }
  }
}
{% endprettify %}

스트림 (stream)을 구축할 때 `async*` 을 사용하면 멋지고 가독성 좋은 코드를 만들 수 있습니다.

<?code-excerpt "misc/test/samples_test.dart (async*)"?>
{% prettify dart %}
Stream<String> report(Spacecraft craft, Iterable<String> objects) async* {
  for (var object in objects) {
    await Future.delayed(oneSecond);
    yield '${craft.name} flies by $object';
  }
}
{% endprettify %}


[Read more](/guides/language/language-tour#asynchrony-support)
async 함수, `Future`, `Stream` 과 비동기 루프에 대한 내용을 포함하는 비동기 지원에 대해 살펴보세요.


## 예외 (Exceptions)

예외를 일으키려면 `throw` 를 사용합니다.

<?code-excerpt "misc/test/samples_test.dart (throw)"?>
{% prettify dart %}
if (astronauts == 0) {
  throw StateError('No astronauts.');
}
{% endprettify %}

예외를 캐치하기 위해서 `try` 문을 `on` 또는 `catch` (또는 둘 다) 와 함께 사용할 수 있습니다.

<?code-excerpt "misc/test/samples_test.dart (try)"?>
{% prettify dart %}
try {
  for (var object in flybyObjects) {
    var description = await File('$object.txt').readAsString();
    print(description);
  }
} on IOException catch (e) {
  print('Could not describe object: $e');
} finally {
  flybyObjects.clear();
}
{% endprettify %}

위 코드가 비동기라는 점에 주의하시길 바랍니다.
`try` 는 비동기 함수 내 코드와 동기 코드에서 모두 잘 동작합니다.

[Read more](/guides/language/language-tour#exceptions) 
stack trace, `rethrow`, 에러와 예외의 차이점에 대해서 다루는 예외에 대해서 살펴보세요.


## 다른 주제

더 풍부한 코드 샘플은 
[언어 살펴보기](/guides/language/language-tour)와
[라이브러리 살펴보기](/guides/libraries/library-tour)에 있습니다.
많은 예제를 포함하고 있는 [Dart API reference]({{site.dart_api}})를 보셔도 좋습니다.