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

[Read more](/guides/language/language-tour#libraries-and-visibility) about libraries and visibility in Dart,
including library prefixes, `show` and `hide`, and lazy loading through the `deferred` keyword.


## Classes

Here's an example of a class with three properties, two constructors,
and a method. One of the properties can't be set directly, so it's
defined using a getter method (instead of a variable).

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

You might use the `Spacecraft` class like this:

<?code-excerpt "misc/test/samples_test.dart (use class)" plaster="none"?>
{% prettify dart %}
var voyager = Spacecraft('Voyager I', DateTime(1977, 9, 5));
voyager.describe();

var voyager3 = Spacecraft.unlaunched('Voyager III');
voyager3.describe();
{% endprettify %}

[Read more](/guides/language/language-tour#classes) about classes in Dart,
including initializer lists, optional `new` and `const`, redirecting constructors,
`factory` constructors, getters, setters, and much more.


## Inheritance

Dart has single inheritance.

<?code-excerpt "misc/lib/samples/spacecraft.dart (extends)"?>
{% prettify dart %}
class Orbiter extends Spacecraft {
  num altitude;
  Orbiter(String name, DateTime launchDate, this.altitude)
      : super(name, launchDate);
}
{% endprettify %}

[Read more](/guides/language/language-tour#extending-a-class) about extending classes, the optional `@override` annotation, and more.


## Mixins

Mixins are a way of reusing code in multiple class hierarchies. The following class can act as a mixin:

<?code-excerpt "misc/lib/samples/spacecraft.dart (mixin)"?>
{% prettify dart %}
class Piloted {
  int astronauts = 1;
  void describeCrew() {
    print('Number of astronauts: $astronauts');
  }
}
{% endprettify %}

To add a mixin's capabilities to a class, just extend the class with the mixin.

<?code-excerpt "misc/lib/samples/spacecraft.dart (mixin use)" replace="/with/[!$&!]/g"?>
{% prettify dart %}
class PilotedCraft extends Spacecraft [!with!] Piloted {
  // ···
}
{% endprettify %}

`PilotedCraft` now has the `astronauts` field as well as the `describeCrew()` method.

[Read more](/guides/language/language-tour#adding-features-to-a-class-mixins) about mixins.


## Interfaces and abstract classes

Dart has no `interface` keyword. Instead, all classes implicitly define an interface. Therefore, you can implement any class.

<?code-excerpt "misc/lib/samples/spacecraft.dart (implements)"?>
{% prettify dart %}
class MockSpaceship implements Spacecraft {
  // ···
}
{% endprettify %}

[Read more](/guides/language/language-tour#implicit-interfaces) about implicit interfaces.

You can create an abstract class to be extended (or implemented) by a concrete class. Abstract classes can contain abstract methods (with empty bodies).

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

Any class extending `Describable` has the `describeWithEmphasis()` method, which calls the extender's implementation of `describe()`.

[Read more](/guides/language/language-tour#abstract-classes) about abstract classes and methods.


## Async

Avoid callback hell and make your code much more readable by
using `async` and `await`.

<?code-excerpt "misc/test/samples_test.dart (async)" replace="/async/[!$&!]/g"?>
{% prettify dart %}
const oneSecond = Duration(seconds: 1);
// ···
Future<void> printWithDelay(String message) [!async!] {
  await Future.delayed(oneSecond);
  print(message);
}
{% endprettify %}

The method above is equivalent to:

<?code-excerpt "misc/test/samples_test.dart (Future.then)"?>
{% prettify dart %}
Future<void> printWithDelay(String message) {
  return Future.delayed(oneSecond).then((_) {
    print(message);
  });
}
{% endprettify %}

As the next example shows, `async` and `await` help make asynchronous code
easy to read.

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

You can also use `async*`, which gives you a nice, readable way to build streams.

<?code-excerpt "misc/test/samples_test.dart (async*)"?>
{% prettify dart %}
Stream<String> report(Spacecraft craft, Iterable<String> objects) async* {
  for (var object in objects) {
    await Future.delayed(oneSecond);
    yield '${craft.name} flies by $object';
  }
}
{% endprettify %}

[Read more](/guides/language/language-tour#asynchrony-support) about
asynchrony support, including async functions, `Future`, `Stream`,
and the asynchronous loop (`await for`).


## Exceptions

To raise an exception, use `throw`:

<?code-excerpt "misc/test/samples_test.dart (throw)"?>
{% prettify dart %}
if (astronauts == 0) {
  throw StateError('No astronauts.');
}
{% endprettify %}

To catch an exception, use a `try` statement with `on` or `catch` (or both):

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

Note that the code above is asynchronous;
`try` works for both synchronous code and code in an async function.

[Read more](/guides/language/language-tour#exceptions) about exceptions, including stack traces, `rethrow`, and the difference between
Error and Exception.


## Other topics

Many more code samples are in the
[language tour](/guides/language/language-tour) and the
[library tour](/guides/libraries/library-tour).
Also see the [Dart API reference,]({{site.dart_api}})
which often contains examples.
