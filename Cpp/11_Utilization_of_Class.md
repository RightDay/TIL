# 클래스의 활용

## 연산자 오버로딩

연산자 오버로딩(operator overloading)은 C++가 가진 다형(polymorphism) 특성의 한 예이다.

C++에서는 연산자 오버로딩을 사용자 정의 데이터형에까지 확장할 수 있다.

ex) 일반적으로 2개의 배열을 더하는 경우

```cpp
for (int i = 0; i < 20; i++)
    evening[i] = sam[i] + janet[i];	//원소별로 더한다.
```

ex) 배열을 나타내는 클래스를 정의하고 + 연산자를 오버로딩

```cpp
evening = sam + janet;	//두 array 객체를 더한다.
```

연산자를 오버로딩하려면, 연산자 함수(operator function)라는 특별한 함수를 사용해야 한다.

```cpp
operatorop(argument-list)
```

op는 오버로딩할 연산자를 나타내는 기호이다. ex)  operator+()는 + 연산자를 오버로딩한다.

op는 적법한 C++ 연산자여야 한다. 새로운 기호를 사용할 수 없다.

ex) 영업사원 객체의 판매액을 다른 영업사원 객체의 판매액에 더 할 수 있도록 하기 위해, + 연산자를 오버로딩한 operator+() 멤버 함수를 정의하고 district2, sid, sara가 모두 Salesperson 클래스의 객체들이 있다면

```cpp
district2 = sid + sara;
```

피 연산자들이 Salesperson 클래스에 속한다는 것을 컴파일러가 인식하면, 컴파일러는 그 연산자를 해당하는 연산자 함수로 대체한다.

```cpp
district2 = sid.operator+(sara);
```

그 함수는 합계를 계산하여 리턴하기 위해, sid 객체를 암시적으로 사용하고(메서드를 호출한 객체이므로), sara 객체를 명시적으로 사용한다(매개변수로 전달되었으므로).