# C++의 시작

C++ 프로그램에서 가장 기본이 되는 구조를 전반적으로 살펴본다.

```cpp
// myfirst.cpp -- 메시지를 출력한다.

#include <iostream>							//선행처리 지시자

int main()									//함수 머리
{											//함수 몸체의 시작
    using namespace std;					//정의 가시화
    cout << "Hello";						//메시지 출력
    cout << endl;							//새로운 행 시작
    cout << "World";						//또 다른 메시지 출력
    return 0;								//main()을 종료
}											//함수 몸체의 끝
```

* ## main() 함수

  * ```cpp
    int main()
    {
        구문들
        return 0;
    }
    ```

    * int main() : 함수 머리(function header)
    * 중괄호 { } : 함수 몸체(function body)
    * 구문(statement) : 컴퓨터에게 내리는 지시(instruction)
    * return : 함수를 종료하는 역할

  * main() 함수는 프로그램과 운영 체제를 중개하기 위해 컴파일러가 프로그램에 추가하는 시동코드에 의해 호출된다.

  * 모든 C++프로그램에는 main() 함수로부터 실행을 개시한다.

    * 프로그램에 main() 함수가 없으면 완전한 프로그램이 아니다.
      * 일부 예외도 있다. 
        * Windows 프로그래밍에서 동적 링크 라이브러리(DLL) 모듈을 작성
        * 로봇의 컨트롤러 칩 등



* ## C++ 전처리기와 iostream 파일

  * C++의 일반적인 입출력 기능을 사용하려면 다음 두 행을 넣어야 한다.

    * ```cpp
      #include <iostream>
      using namespace std;	//몇 가지 대체 방법이 있다.
      ```

  * ### 전처리기(preprocessor)

    * 컴파일을 하기 전에 소스 파일에 대해 미리 어떤 처리를 수행하는 프로그램이다.
    
    * 특별히 따로 호칠하는 것이 아니라 소스 파일을 컴파일할 때 자동으로 실행된다.
    
    * ```cpp 
      #include <iostream>	//전처리 지시자
      ```
    
      * 이 지시자는 전 처리기에 iostream 파일의 내용을 프로그램에 추가하라고 지시한다.
      * 이와 같이 컴파일되기 전에 소스 코드에 텍스트를 추가하거나 텍스트를 대체하는 것이 전처리기가 수행하는 기본적인 역할이다.
    
    * #### iostream 파일의 내용을 프로그램에 포함시켜야 하는 이유
    
      * i는입력(input), o는 출력(output)을 나타낸다.
      * iostream 파일에는 C++의 몇 가지 입출력 기능이 정의되어 있다.
      *  #include <iostream>행이 iostream 파일의 내용으로 대체된다.
