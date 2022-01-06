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

