# Kotlin

- [Kotlin](#kotlin)
  - [Object](#object)
    - [Object expressions](#object-expressions)
      - [Creating anonymous objects from scratch](#creating-anonymous-objects-from-scratch)
      - [Inheriting anonymous objects from supertypes](#inheriting-anonymous-objects-from-supertypes)
      - [Using anonymous object as return and value types](#using-anonymous-object-as-return-and-value-types)
      - [Accessing variables from anonymous objects](#accessing-variables-from-anonymous-objects)
    - [Object declarations](#object-declarations)
      - [Companion objects](#companion-objects)
      - [Semantic difference between object expressions and declarations](#semantic-difference-between-object-expressions-and-declarations)
    - [References](#references)

## Object

경우에 따라 새 하위 클래스를 명시적으로 선언하지 않고 일부 클래스를 약간 수정한 개체를 생성해야 하는데, 코틀린은 이런 케이스를 다루기 위해서 `object`를 제공한다.

### Object expressions

`Object expressions`는 익명의 클래스 객체를 생성한다. 즉, `class` 선언으로 명시적으로 선언되지 않은 클래스를 생성한다.

이런 클래스들은 한번만 사용하기에 편리하다. 우리는 처음부터 정의하거나, 기존 클래스에서 상속하거나, 인터페이스를 구현으로부터 `object`를 정의할 수 있다.

익명 클래스의 인스턴스는 이름이 아닌 expression으로 정의되므로 익명 객체(`anonymous objects`)라고도 한다.

#### Creating anonymous objects from scratch

`Object expressions`는 `object`라는 키워드로 시작한다.

만약 `nontrivial supertypes`이 없는 그냥 object만 필요하다면, `object` 뒤 `{ }` 안에 object 의 멤버들만 넣으면 된다.

```kt
fun main() {
    val helloWorld = object {
        val hello = "Hello"
        val world = "World"
        // object expressions extend Any, so `override` is required on `toString()`
        override fun toString() = "$hello $world"
    }
    print(helloWorld)
}
// Hello World
```

#### Inheriting anonymous objects from supertypes

To create an object of an anonymous class that inherits from some type (or types), specify this type after object and colon (: ). Then implement or override the members of this class as if you were inheriting from it:

어떤 타입(들)에서 상속되는 익명의 클래스의 object를 생성하기 위해서, `object :` 뒤에 그 타입을 지정한다. 그런 다음 이 클래스의 구성원을 상속받는 것처럼 구현하거나 재정의한다.

```kt
window.addMouseListener(object : MouseAdapter() {
    override fun mouseClicked(e: MouseEvent) { /*...*/ }

    override fun mouseEntered(e: MouseEvent) { /*...*/ }
})
```

만약 supertypes 가 생성자를 가지고 있다면, 적절한 생성자 파라미터들을 넣어줘야 한다. 여러 개의 supertypes들을 `:` 뒤에 `,`로 리스트 형태로 나열해서 지정할 수 있다.

```kt
open class A(x: Int) {
    public open val y: Int = x
}

interface B { /*...*/ }

val ab: A = object : A(1), B {
    override val y = 15
}
```

#### Using anonymous object as return and value types

Anonymous object가 `local` 또는 `private` 타입으로 사용되지만 `inline declaration` (function or property)이 아닌 경우, 해당 객체의 모든 멤버는 다음 function 또는 property을 통해 액세스할 수 있다.

```kt
class C {
    private fun getObject() = object {
        val x: String = "x"
    }

    fun printX() {
        println(getObject().x)
    }
}
```

이 function 또는 property이 public 또는 private inline인 경우 실제 type은 다음과 같다.

- Anonymous object가 선언된 supertype을 가지지 않은 경우, `Any`
- 정확히 하나의 선언된 supertype이 존재하면, 그 `선언된 supertype`
- 선언된 supertype이 여러 개 존재하면, `명시적으로 선언된 supertype`

```kt
interface A {
    fun funFromA() {}
}
interface B

class C {
    // The return type is Any. x is not accessible
    fun getObject() = object {
        val x: String = "x"
    }

    // The return type is A; x is not accessible
    fun getObjectA() = object: A {
        override fun funFromA() {}
        val x: String = "x"
    }

    // The return type is B; funFromA() and x are not accessible
    fun getObjectB(): B = object: A, B { // explicit return type is required
        override fun funFromA() {}
        val x: String = "x"
    }
}
```

#### Accessing variables from anonymous objects

object expressions의 코드는 동봉된 범위(enclosing scope)에서 변수에 액세스할 수 있다.

```kt
fun countClicks(window: JComponent) {
    var clickCount = 0
    var enterCount = 0

    window.addMouseListener(object : MouseAdapter() {
        override fun mouseClicked(e: MouseEvent) {
            clickCount++
        }

        override fun mouseEntered(e: MouseEvent) {
            enterCount++
        }
    })
    // ...
}
```

### Object declarations

Singleton 패턴은 몇 가지 케이스들에 대해서 유용할 수 있고, 코틀린은 singletons를 쉽게 정의할 수 있게 해준다.

```kt
object DataProviderManager {
    fun registerDataProvider(provider: DataProvider) {
        // ...
    }

    val allDataProviders: Collection<DataProvider>
        get() = // ...
}
```

이것은 `object declaration`이라고 부르고, 언제나 `object` 뒤에 이름이 항상 따라온다.

변수(variable) 선언처럼, `object` 선언도 표현식(`expression`)이 아니며 assignment statement 의 우변에 사용할 수 없다.

`object` 선언의 초기화는 thread-safe 하며, 첫번째 접근때 끝난다.

`object`를 참조하려면 그것의 이름을 곧바로 사용하면 된다.

```kt
DataProviderManager.registerDataProvider(...)
```

어떤 `object`들은 supertypes를 가질 수 있다.

```kt
object DefaultListener : MouseAdapter() {
    override fun mouseClicked(e: MouseEvent) { ... }

    override fun mouseEntered(e: MouseEvent) { ... }
}
```

> `object` 선언은 로컬(즉, 함수 내에 직접 중첩될 수 없음)일 수 없지만 다른 `object` 선언 또는 non-inner classes에 중첩될 수 있다.

#### Companion objects

#### Semantic difference between object expressions and declarations

### References

- [https://kotlinlang.org/docs/object-declarations.html](https://kotlinlang.org/docs/object-declarations.html)
- [https://play.kotlinlang.org/byExample/03_special_classes/04_Object](https://play.kotlinlang.org/byExample/03_special_classes/04_Object)
