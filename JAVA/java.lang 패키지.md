# java.lang 패키지

## java.lang 패키기지의 대표적인 클래스
- `Object` : 모든 자바 객체의 부모 클래스
- `String` : 문자열
- `Integer` , `Long` , `Double` : 래퍼 타입, 기본형 데이터 타입을 객체로 만든 것
- `Class` : 클래스 메타 정보
- `System` : 시스템과 관련된 기본 기능들을 제공

<br>

## Objsct 클래스

모든 클래스의 최상의 부모 클래스는 항상 `object` 이다.
<br>

```
public class Parent {
// 묵시적으로 Object 클래스 상속
    public void parentMethod() {
        System.out.println("Parent.parentMethod");
    }
}
```

```
public class Child extends Parent {
// 명시적 상속
    public void childMethod() {
        System.out.println("Child.childMethod");
    }
}
```

<br>

### 자바에서 Object 클래스가 최상위 부모 클래스인 이유
1. 공통 기능제공
   <br><br>
   toString, equals, getClass 등과 같은 공통 기능들을 상속받아 사용할 수 있다.<br>
   이에 따라 프로그래밍이 단순하고 일관성을 가지게 된다.

2. 다형성의 기본 구현
    <br><br>
    모든 자바 객체는 object 타입으로 처리될 수 있다.

* Object 다형성 
```
public class Car {
    public void move() {
        System.out.println("자동차 이동");
    }
}
```

```
public class Dog {
    public void sound() {
        System.out.println("멍멍");
    }
}
```
와 같은 두개의 클래스가 존재할 때, 

```
    public static void main(String[] args) {
        Dog dog = new Dog();
        Car car = new Car();

        action(dog);
        action(car);
    }

    private static void action(Object obj) {
        //obj.sound(); // 컴파일 오류, Object는 sound()가 없다.
        //obj.move(); // 컴파일 오류, Object는 move()가 없다.

        //객체에 맞는 다운캐스팅 필요
        if (obj instanceof Dog dog) {
            dog.sound();
        } else if (obj instanceof Car car) {
            car.move();
        }
    }
```
<br>

장점과 단점 
* 장점 : 어떤 객체든 인자로 전달 할 수 있다.
* 단점 : `Object` 통해 전달받은 객체를 호출하려면 각 객체에 맞는 다운캐스팅 과정이 필요하다.

<br>

## Object 배열
`Object` 는 모든 타입의 객체를 담을 수 있다. 따라서 `Object[]` 을 만들면 세상의 모든 객체를 담을 수 있는 배열을 만들 수 있다.

* size() 메서드 <br>
배열에 담긴 객체의 수를 세는 역할을 담당한다. 이 메서드는 `Object` 타입만 사용한다. <br>
`Object` 타입의 배열은 모든 객체를 담을 수 있기 때문에 새로운 클래스가 추가되거나 변경되어도 메서드를 수정하지 않아도 된다.

## toString() 메서드 
`Object.toString()` 메서드는 객체의 정보를 문자열 형태로 제공한다. 그래서 디버깅과 로깅에 유용하게 사용된다. <br>
이 메서드는 `Object` 클래스에 정의되므로 모든 클래스에서 상속받아 사용할 수 있다.<br>
`Object`가 제공하는 toString 메서드는 기본적으로 패키지를 포함한 객체의 이름과 객체의 참조값을 16진수로 제공한다.

<br>

