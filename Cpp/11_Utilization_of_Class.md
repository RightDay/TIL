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

### 오버로딩 제약

- **오버로딩된 연산자는, 적어도 하나의 피연산자가 사용자 정의 데이터형일 것을 요구한다.** 이 제약은 표준 데이터형을 위해서 사용되는 연산자들을 오버로딩하는 것을 막아준다. 그러므로 뺄셈 연산자(-)를 두 개의 double형 값의 차(difference)가 아닌 합(sum)을 산출하도록 재정의할 수 없다.

- **오버로딩된 연산자를, 오리지널 연산자에 적용되는 문법 규칙을 위반하는 방식으로 사용할 수 없다.** 예를 들면, 하나의 피연산자에만 적용할 수 있도록 나머지 연산자(%)를 오버로딩할 수 없다.

  ```cpp
  int x;
  Time shiva;
  % x;	//나머지 연산자로 사용할 수 없다.
  % shiva;	//오버로딩된 연산자로 사용할 수 없다.
  ```

  마찬가지로, 연산자 우선순위도 변경할 수 없다.

- **연산자 기호를 새로 만들 수 없다.** 예를 들면, 거듭제곱(exponentiatoin)을 나타낼 목적으로 operator**() 와 같은 함수를 정의할 수 없다.

- **일부 연산자들은 오버로딩할 수 없다.** (sizeof, 멤버 연산자, 멤버 지시 포인터 연산자 사용 범위 결정 연산자 등)

- 대입 연산자, 함수 호출 연산자, 배열 인덱스 연산자, 클래스 멤버 접근 포인터 연산자는 오버로딩하는 데 멤버 함수만 사용할 수 있다.

# 프렌드의 도입

C++는 프렌드(friend)라는 또 하나의 접근 통로를 제공한다. 프렌드는 다음과 같은 세 가지 형태로 사용된다.

- 프렌드 함수
- 프렌드 클래스
- 프렌드 멤버 함수

함수를 어떤 클래스에 대해 프렌드로 만들면, 그 프렌드 함수는 클래스의 멤버 함수들이 가지는 것과 동등한 접근 권한을 갖는다.

어떤 클래스에 대해 이항 연산자(binary operator; 두 개의 피연산자를 요구하는 연산자)를 오버로딩하면, 프렌드를 만들 필요성이 생긴다.

```cpp
A = B * 2.77;
A = B.operator*(2.75);
A = 2.75 * B;	//멤버 함수에 대응시킬 수 없다
A = operator*(2.75, B);	//멤버가 아닌 함수 호출로 다음과 같이 대응
Time operator*(double m, const Time & t);	//함수 원형
```

### 프렌드 생성하기

프렌드 함수를 만들 때는 클래스 선언에 원형을 넣는다. 이때 friend라는 키워드를 앞에 붙여야 한다.

```cpp
friend Time operator*(double m, const Time & t);	//클래스 선언에
```

이 원형은 두 가지 함축적인 의미를 가지고 있다.

- operator*() 함수는, **클래스 선언 안에 선언되지만 멤버 함수가 아니다.** 그러므로 멤버 연산자를 사용하여 호출하지 않는다.
- operator*() 함수는, 그것이 비록 **멤버 함수는 아니지만 멤버 함수와 동등한 접근 권한을 가진다.**

**함수 정의를 작성하는 것으로도 생성 가능하다.** 그것은 멤버 함수가 아니기 때문에, Time:: 제한자를 사용하지 않는다. 또한, 그 정의에 friend라는 키워드도 사용하지 않는다. 그 정의는 다음과 같아야 한다.

```cpp
Time operator*(double m, const Time & t)	//정의에는 friend가 없다.
{
    Time result;
    long totalminutes = t.hours * mult * 60 + t.minutes * mult;
    result.hours = totalminutes / 60;
    result.minutes = totalminutes % 60;
    return result;
}
//이와 같이 선언하고 정의하면, 다음과 같은 구문은
A = 2.75 * B;
//다음과 같이 번역되어, 방금 정의한 멤버가 아닌 프렌드 함수를 호출한다.
A = operator*(2.75, B);
```

간단히 말해서, 어떤 클래스에 대한 프렌드 함수는 멤버 함수와 동등한 접근 권한을 가지는, 멤버가 아닌 함수이다.

#### 프렌드는 OOP에 어울리지 않는다?

**프렌드 함수는 클래스를 위한 확장 인터페이스의 일부**라고 생각해야 한다. 개념상으로 보았을 때 double형 값에 Time 값을 곱하는 것은, Time 값에 double형 값을 곱하는 것과 같다. 전자가 프렌드 함수를 요구하고 후자가 멤버 함수를 요구하는 것은, 개념상에 차이가 있기 때문이다. **프렌드 함수와 클래스 메서드를 둘 다 사용하면, 어느 연산이든지 동일한 사용자 인터페이스로 표현할 수 있다.** 또한, **클래스 선언만이 어느 함수가 프렌드 함수인지를 결정할 수 있고, 그렇게 함으로써 클래스 선언은 private 데이터에 접근하는 함수들을 여전히 통제할 수 있다.** 요약하면, **클래스 메서드와 프렌드는 단순히 클래스 인터페이스를 나타내는 두 개의 서로 다른 메커니즘이다.**

연산자를 어떤 클래스에 적용할 수 있게 오버로딩하여, 클래스 멤버가 아닌 항을 첫 번째 피 연산자로 사용하려면, 피연산자 순서를 바꾸어 주는 프렌드 함수를 사용할 수 있다.

### 프렌드: << 연산자의 오버로딩

클래스의 매우 유용한 기능 중의 하나는, << 연산자를 오버로딩하여 cout과 함께 사용함으로써 객체의 내용을 출력할 수 있다는 것이다.

#### 오버로딩 <<의 첫 번째 버전

```cpp
cout << trip;
```

**클래스가 cout을 사용하려면 프렌드 함수를 사용해야 한다.** 두 개의 객체를 사용하고 있지만, ostream 클래스 객체(cout)를 첫 번째 피연산자로 사용하기 때문에 프렌드 함수를 사용해야 한다.

만약 <<를 오버로딩하기 위해 * 연산자를 오버로딩했을 때 그랬던 것처럼, 객체가 첫 번째 피연산자가 되어야 한다. 그것은 << 연산자를 다음과 같은 방식으로 사용해야 한다는 것을 의미한다.

```CPP
void operator<<(ostream & os, const Time & t)
{
    os << t.hours << "시간, " << t.minutes <<"분";
}
```



