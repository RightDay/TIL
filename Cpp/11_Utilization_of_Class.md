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

## 연산자 오버로딩 예제

```cpp
// mytime.h -- Time 클래스
#ifndef MYTIMEO_H_
#define MYTIMEO_H_

class Time
{
private:
    int hours;
    int minutes;
public:
    Time();
    Time(int h, int m = 0);
    void AddMin(int m);
    void AddHr(int h);
    void Reset(int h = 0, int m = 0);
    Time Operator+(const Time & t) const;
    Time Sum(const Time & t) const;
}
```

```cpp
// mytime.cpp -- Time 클래스의 메서드 구현
#include <iostream>
#include "mytime1.h"

Time::Time()
{
    hours = minutes = 0;
}

Time::Time(int h, int m)
{
    hours = h;
    minutes = m;
}

void Time::AddMin(int m)
{
    minutes += m;
    hours += minutes / 60;
    minutes %= 60;
}

void Time::AddHr(int h)
{
    hours += h;
}

void Time::AddHr(int h)
{
    hours += h;
}

void Time::Reset(int h, int m)
{
    hours = h;
    minutes = m;
}

Time Time::operator+(const Time & t) const
{
    Time sum;
    sum.minutes = minutes + t.minutes;
    sum.hours = hours + t.hours + sum.minutes / 60;
    sum.minutes % = 60;
    return sum;
}

void Time::Show() const
{
    std::cout << hours << "시간, " << minutes << "분";
}
```

- operator+() 메서드 호출

```cpp
total = coding.operator+(fixing);	//함수 표기
total = coding + fixing;	//연산자 표기
```

컴파일러는 피연산자의 데이터형을 판단하여 자기가 해야 할 일을 결정한다.

- 두 개 이상의 객체들의 덧셈

```cpp
t4 = t1 + t2 + t3;
t4 = t1.operator+(t2 + t3);	//덧셈 연산자가 왼쪽에서 오른쪽으로 결합하기 때문에 이와 같이 해석됨.
t4 = t1.operator+(t2.operator+(t3));	//함수 매개변수 자체가 함수 호출로 해석됨.
```

## 오버로딩 제약

- 오버로딩된 연산자는, 적어도 하나의 피연산자가 사용자 정의 데이터형일 것을 요구한다. 이 제약은 표준 데이터형을 위해서 사용되는 연산자들을 오버로딩하는 것을 막아준다. 그러므로 뺄셈 연산자(-)를 두 개의 double형 값의 차(difference)가 아닌 합(sum)을 산출하도록 재정의할 수 없다.

- 오버로딩된 연산자를, 오리지널 연산자에 적용되는 문법 규칙을 위반하는 방식으로 사용할 수 없다. 예를 들면, 하나의 피연산자에만 적용할 수 있도록 나머지 연산자(%)를 오버로딩할 수 없다.

  ```cpp
  int x;
  Time shiva;
  % x;	//나머지 연산자로 사용할 수 없다.
  % shiva;	//오버로딩된 연산자로 사용할 수 없다.
  ```

  마찬가지로, 연산자 우선순위도 변경할 수 없다.

- 연산자 기호를 새로 만들 수 없다. 예를 들면, 거듭제곱(exponentiatoin)을 나타낼 목적으로 operator**() 와 같은 함수를 정의할 수 없다.

- 일부 연산자들은 오버로딩할 수 없다.(sizeof, 멤버 연산자, 멤버 지시 포인터 연산자 사용 범위 결정 연산자 등)

- 대입 연산자, 함수 호출 연산자, 배열 인덱스 연산자, 클래스 멤버 접근 포인터 연산자는 오버로딩하는 데 멤버 함수만 사용할 수 있다.

