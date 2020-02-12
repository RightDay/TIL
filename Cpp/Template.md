# 템플릿(Template)

* 함수나 클래스를 개별적으로 다시 작성하지 않아도, 여러 자료형으로 사용할 수 있도록 하게 만들어 놓은 틀이다.

* C++ 표준 라이브러리에 사용된다.

* 일반화 프로그래밍(Generic Programming)을 할 때 사용한다.

  * 일반화 프로그래밍(Generic Programming)
    * 소프트웨어 라이브러리의 효율성과 재사용성을 높이려는 프로그래밍 패러다임의 하나이다.
    * 데이터 형식에 의존하지 않고, 데이터가 여러 다른 데이터 타입들을 가질 수 있는 것이 중점인 프로그래밍 방식이다.
    * 함수나 클래스 등의 프로그램 내 요소들을 일반화한다.

* ## 함수 템플릿(Function Template)
  
  * 다양한 템플릿 인자에 대한 함수를 정의한 것이다.
  
  * ```cpp
    //T라는 이름으로 아래에 위치한 함수를 템플릿으로 정의한다.
    template <typename T>
    
    //typename을 class로 써도 상관 없다.
    template <typename T> void Func(T arg) {}
    template <class T> void Func(T arg) {}
    
    void main()
    {
        int num = 10;
        Func(num);
        
        char c = 'A'
        Func('c');
    }
    ```
  
* ## 클래스 템플릿(Class Template)

  * 다양한 템플릿 인자에 대한 클래스를 정의한 것이다.

  * ```cpp
    //T라는 이름으로 아래에 위치한 클래스를 템플릿으로 정의한다.
    template <typename T>
    
    class Data
    {
    private:
        T data;
    
    public:
        Data(T data) : data(data) {}
    }
    
    void main()
    {
        Data<int> data1(10);
        Data<char> data2('A');
    }
    ```

  * 템플릿 클래스에선 자료형 정보를 생략해선 안된다.

