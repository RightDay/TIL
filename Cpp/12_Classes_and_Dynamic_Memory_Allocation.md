# 클래스와 동적 메모리 대입

## 동적 메모리와 클래스

C++의 메모리 대입 전략은 사용할 메모리의 크기를 컴파일할 때 결정하지 않고 프로그램을 실행할 때 상황에 따라 융통성 있게 결정하는 것이다.

다시 말해, 메모리 사용을 기억 공간들의 확정된 규칙에 따르지 않고 프로그램의 요구에 맞출 수 있다.

메모리를 동적으로 제어하기 위해서, C++는 new와 delete 연산자를 사용한다.

### 복습을 위한 예제와 static 클래스 멤버

StringBad 클래스를 통해 new와 delete를 복습하고, static 클래스 멤버라는 새로운 기억 공간을 살펴보자.

```cpp
// stringbad.h -- 결함이 있는 string 클래스 정의
#include <iostream>
#ifndef STRNGBAD_H_
#define STRNGBAD_H_
class StringBad
{
private:
    char * str;	//문자열을 지시하는 포인터
    int len;	//문자열의 길이
    static int num_strings;	//객체의 수
public:
    StringBad(const char * s);	//생성자
    StringBad();	//디폴트 생성자
    ~StringBad();	//파괴자
//프렌드 함수
    friend std::ostream & operator<<(std::ostream & os, const StringBad & st);
};
#endif
```

