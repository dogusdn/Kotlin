# Kotlin

## 변수선언
```kotlin
val data1: Int = 10
var data2: Int = 20
```
* val (value) : 초깃값이 할당되면 바꿀 수 없는 변수 선언
* var (variable) : 초기값이 할당된 후에도 값을 바꿀 수 있는 변수 선언

## 초깃값 할당
* 최상위에 선언한 변수나 클래스의 멤버 변수는 선언과 동시에 초깃값을 할당해야 한다.
* 함수 내부에 선언한 변수는 선언과 동시에 초깃값을 할당하지 않아도 된다. 
  * 단, 변수를 사용하려면 값을 할당하고 사용

## 초기화 미루기
### lateinit
```kotlin
lateinit var data3: String
```
* lateinit은 var 키워드로 선언한 변수에만 사용할 수 있다.
* Int, Long, Short, Double, Float, Boolean, Byte 타입에는 사용할 수 없다.

### lazy
```kotlin
val data4: Int by lazy {
  print("in lazy ...")
  10  // 변수의 초깃값
}
```

## 데이터 타입
* 코틀린의 모든 변수는 객체 이다.
* 따라서 코틀린의 모든 타입은 객체 타입이다.
```Kotlin
fun someFun() {
  var data1: Int = 10
  var data2: Int? = null    // null 대입 가능
  
  data1 = data1 + 10
  data1 = data1.plus(10)    // 객체의 메서드 이용 가능
```
* 코틀린의 모든 타입은 객체이므로 Int 타입의 변수에 10이라는 정수 뿐 아니라, null을 대입할 수도 있다.
* 또한 객체의 메서드도 호출 가능

### Char, String - 문자와 문자열
* Char는 문자를 표현하는 타입으로, 코틀린 코드에서 Char 타입의 데이터는 문자를 작은 따옴표(')로 감싸서 표현
* Number 타입으로 표현할 수 없다.
```kotlin
val str1: Char = 'a'
if (a == 1) { // 오류!
}

val str2 = """
     Hello
     World
"""
```


### Any - 모든 타입 가능
* Any는 코틀린에서 최상위 클래스
* 모든 코틀린의 클래스는 Any의 하위 클래스이다.
  * 따라서 Any 타입으로 선언한 변수에는 모든 타입의 데이터를 할당 가능하다.
```kotlin
val data1: Any = 10
val data2: Any = "Hello"

class User
val data3: Any = User()
```

### Unit - 반환문이 없는 함수
* 함수에서 반환문이 없음을 명시적으로 나타낼 때 Unit 타입을 사용한다.
```kotlin
fun some(): Unit {
 println(10 + 20)
}
 
// 함수 선언시 반환 타입 생략하면 자동으로 Unit 타입!

fun some() {
 println(10 + 20)
}
```

### Nothing - null 이나 예외를 반환하는 함수
* Nothing 으로 선언한 변수에는 null만 대입할 수 있다.
* Nothing 으로 선언한 변수는 데이터로서는 의미가 없다.
```kotlin
val data1: Nothing? = null

fun some1(): Nothing? {
 return null
}
fun some2(): Nothing {
 throw Exxception()
}
```

* 어떤 함수의 반환 타입이 Nothing 이면 반환은 하지만 의미 있는 값은 아니다.
* 항상 null만 반환하는 함수라든가 예외를 던지는 함수


### 널 허용과 불허용
* 코틀린의 모든 타입은 객체이므로 변수에 null을 대입할 수 있다.
* null 은 값이 할당되지 않은 상황을 의미
* 코틀린에서 변수를 선언할 때 null을 대입할 수 있는 변수인지, 대입할 수 없는 변수인지 구분해서 선언
```kotlin
var data1: Int = 10 // null 불허용
data1 = null // 오류!

var data2: Int? = 10
data2 = null // 성공!
```
* 타입 뒤에 물음표(?) 를 추가하면 널허용 // 추가하지 않으면 불허용


### 함수 선언하기
* 코틀린에서 함수를 선언하려면 fun 이라는 키워드를 이용
```kotlin
fun 함수명(매개변수명: 타입): 반환 타입 { ... }
```

* 함수에는 반환 타입을 선언할 수 있으며 생략하면 자동으로 Unit 타입이 적용된다.
```kotlin
// 반환 타입이 있는 함수 선언
fun some(data1: Int): Int {
 return data1 * 10
}
```

* 함수의 매개변수에는 var / var 키워드를 사용 불가능
* val 이 자동으로 적용되며 함수 안에서 매개변숫값을 변경 할 수 없다.
```kotlin
// 매개변수값 변경 오류
fun some(data1: Int) {
 data1 = 20  // 오류 !
}
```

#### 매개변수명 지정해서 호출
```kotlin
// 매개변수명 생략 - 매개변수 순서대로 할당
fun some(data1: Int, data2: Int): Int {
 return data1 * data2
}
println(some(10,20))

// 매개변수명을 지정하여 호출함
some(data2 = 20, data1 = 10)
```
* 매개변수명을 지정하여 호출하는 것을 명명된 매개변수라고 한다.
* 이렇게 하면 함수 선언문의 매개변수 순서에 맞춰 호출 하지 않아도 된다.


## 컬렉션 타입
* 컬렉션 타입이란 여러 개의 데이터를 표현하는 방법이며 Array, List, Set, Map 등이 있다.

### Array - 배열표현
```kotlin
// 배열 선언의 예
val data1: Array<Int> = Array(3, { 0 })
```
* 0으로 초기화 한 데이터를 3개 나열한 정수형 배열을 선언


### arrayOf() - 배열을 선언할 때 값을 할당
```kotlin
fun main() {
 val data1 = arrayOf<Int>(10, 20, 30) // 크기가 3인 Int 배열을 선언하고 10, 20, 30으로 할당
println(
 """
  array size : ${data1.size}
  array data : ${data1[0]}, ${data1[1]}, ${data1.get(2)}
 """
 )
}
```
* 배열 선언과 동시에 값을 할당할 수 있다.



