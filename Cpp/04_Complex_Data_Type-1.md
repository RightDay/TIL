# 복합 데이터형

- ## 배열(Array)
  - 데이터형이 같은 여러 개의 값을 연속적으로 저장할 수 있는 데이터 구조이다.

  - 배열에서 각 값은 배열 원소(element)라는 개별 공간에 저장된다.

  - 컴퓨터는 이 모든 원소들을 메모리에 연속적으로 배치한다.

  - 배열은 선언 구문을 사용하여 생성하고, 배열 선언 구문에서는 다음과 같은 세가지를 선언한다.

    - 각 원소에 저장될 값의 데이터형
    - 배열의 이름
    - 배열 원소의 개수

  - ```cpp
    typeName arrayName[arraySize];	//배열을 선언하는 일반적인 형식
    ```

    - 원소의 개수를 나타내는 arraySize는 **값 10** 또는 **const 기호 상수와 같은 정수 상수**이거나 컴파일할 때 값이 결정되는 8 * sizeof(int)와 같은 **상수 수식**이어야 한다.
    - 프로그램이 실행되는 동안 값이 결정되는 변수는 arraySize가 될 수 없다.
    - new연산자를 사용하여 이러한 제약을 피하는 방법도 있다.

  - 배열 원소에 개별적으로 접근할 수 있다.

    - 개별적인 접근을 허용하기 위해 인덱스(subscript) 또는 인덱스(index)를 사용하여 배열 원소에 차례로 번호가 매겨진다.
    - C++의 배열 인덱스는 항상 0부터 시작한다.
    - 대괄호 안에 인덱스를 넣어 배열 원소를 지정한다.
      - ex) months[0]은 months 배열의 첫 번째 원소를 나타낸다.

  - 컴파일러는 사용자가 적법한 인덱스를 사용하는지를 검사하지 않는다.

    - ex) 사용자가 존재하지도 않는 months[101]에 값을 대입해도 컴파일러는 아무 불평하지 않는다.
    - 그러나 이런 무모한 대입은 프로그램이 실행될 때 문제를 일으켜 데이터나 코드를 망가뜨리고, 프로그램이 먹통이 되게 한다.

  - ### 배열 초기화 규칙

    - 초기화 형식은 배열을 정의하는 곳에서만 사용할 수 있다.

      - ```cpp
        int cards[4] = {3, 6, 8, 10};	// Correct
        int hand[4];	// Correct
        hand[4] = {5, 6, 7, 9};	//Wrong
        hand = cards;	//Wrong
        ```

    - 초기화 값의 개수를 배열 원소의 개수보다 모자라게 할 수 있다.

      - ```cpp
        float hotelTips[5] = {5.0f, 2.0f};
        ```

      - 배열을 부분적으로 초기화하면, 컴파일러가 나머지 원소들을 모두 0으로 설정한다.

    - 대괄호([]) 속을 비워 두면, 컴파일러가 초기화 값으 개수를 헤아려 배열 원소의 개수를 결정한다.

      - ```cpp
        short things[] = {1, 5, 3, 8};
        ```

      - 배열 원소의 개수가 4개인 short형의 배열 things를 생성한다.

  - ### C++11 배열 초기화

    - 배열을 초기화 할 때, = 부호를 사용하지 않아도 된다.

      - ```cpp
        double earnings[4] {1.2e4,k 1.6e4, 1.1e4, 1.7e4};
        ```

    - 중괄호를 공백하여 모든 배열을 0으로 초기화할 수 있다.

      - ```cpp
        unsigned int counts[10] = { };	// 모든 배열값을 0으로 초기화
        float balances[100] { };	// 모든 배열값을 0으로 초기화
        ```

    - 리스트 초기화시에 narrowings을 방지할 수 있다.

      - ```cpp
        long plifs[] = {25, 92, 3.0};	//허용 안 됨
        char slifs[4] {'h', 'i', 1122011, '\0'};	//허용 안 됨
        char tlifs[4] {'h', 'i', 112, '\0'};	//허용
        ```

      - plifs[]는 부동 소수점형에서 정수형으로 변환되기 때문에, 초기화가 실패한다.

      - slifs[4]는 1122011이 char 변수가 가지는 크기를 넘어서기 때문에 초기화가 실패한다.

      - tlifs[4]는 112이 int 값이지만 char 변수가 가지는 크기를 넘지 않기 때문에 초기화가 성공하게 된다.



- ## 문자열(String)

  - 메모리에 바이트 단위로 연속적으로 저장되어 있는 문자들이다.

  - 문자들이 메모리에 바이트 단위로 연속적으로 저장된다는 것은, 문자열을 char형 배열에 저장할 수 있다는 것을 의미한다.

  - 모든 문자열의 마지막 문자가 반드시 널 문자(null character)여야 한다.

    - 널 문자는 \0로 쓰며, ASCII코드가 0인 문자이다.

    - ```cpp
      char dog[4] = { 'b', 'e', 'a', 'd' };	//문자열이 아니다.
      char cat[5] = { 'c', 'a', 's', 'h' '\0' };	//문자열이다.
      ```

    - 두 배열 모두 char형 배열이나 두 번째 배열만이 문자열이다.

    - 문자열 처리 함수들은 널 문자를 만날 때까지 문자 단위로 문자열을 처리한다.

  - char형의 배열을 문자열로 초기화한다.

    - ```cpp
      char bird[7] = "Cheeps";	//\0을 저장한다.
      char fish[] = "Bubbles";	//컴파일러가 알아서 처리한다.
      ```

    - 큰 따옴표로 묶인 문자열을 문자열 상수(string constant 또는 string literal)이라 한다.

    - 문자열 상수는 널 문자를 암시적으로 가지고 있다.

  - (큰따옴표를 사용하는) 문자열 상수와 (작은따옴표를 사용하는) 문자 상수는 서로 바꾸어 쓸 수 없다.

    - ```cpp
      char shirt_size = 'S';	//ASCII 'S'는 83이므로 맞다.
      char shirt_size = "S";	//두 개의 문자(S와 \0)로 구성된 문자열이다. 데이터형 불일치
      ```

  - ### 문자열 상수의 결합

    - C++에서는 문자열 상수들을 결합할 수 있다.

    - 빈칸, 탭, 캐리지 리턴과 같은 화이트스페이스(white space)로 분리된 두 개의 문자열 상수는 하나의 문자열 상수로 결합된다.

    - ```cpp
      cout << "I'd give my right arm to be" "a great violinist.\n";
      cout << "I'd give my right arm to be a great violinist.\n";
      cout << "I'd give my right ar"
          "m to be a great violinist.\n";
      ```

    - 결합된 문자열에는 빈칸이 추가되지 않는다.

    - \0을 뺀 첫 번째 문자열의 마지막 문자에 두 번째 문자열의 첫 문자가 이어진다.

  - ### 배열에 문자열 사용

    - **문자열 상수로 초기화하는 방법**과 **키보드 입력이나 파일 입력을 배열에 저장하는 방법**이 있다.

      - ```cpp
        #include <iostream>
        #include <cstring>	//strlen() 함수를 사용하기 위해
        int main()
        {
            using namepspace std;
            
            const int size = 15;
        	char name1[Size];
        	char name2[Size] = "C++owboy";	//문자열 상수로 초기화된 배열
        
        	cin >> name1;	//키보드 입력을 이용으로 초기화된 배열
        
        	cout << sizeof(name1) << endl;	//배열 크기 출력
        	cout << strlen(name1) << endl;	//문자열 크기 출력
            
            name2[3] = '\0';	//널 문자 삽입
            
            cout << name2 << endl;	//name[2]까지만 출력
        }
        ```

      - sizeof 연산자는 배열의 전체 크기를 리턴한다.

      - strlen() 함수는 널 문자는 제외한 문자열의 크기를 리턴한다.

      - 인덱스를 사용하여 배열에 저장되어 있는 문자들에 개별적으로 접근할 수 있다.

      - 널 문자를 만나면 뒤에 문자들이 있더라도 문자열을 끝낸다.

  - ### 문자열 입력

    - ```cpp
      const int ArSize = 20;
      char name[ArSize];
      char dessert[ArSize];
      
      cout << "이름 입력 : \n";
      cin >> name;	//Allistair Dreeb 입력
      cout << "디저트 입력 : n";
      cin >> dessert;	//Dreeb을 입력받는다.
      ```

    - cin은 빈칸, 탭 캐리지 리턴과 같은 화이트 스페이스가 있으면 그 위치에서 문자열이 끝난 것으로 간주한다.

    - "Alistair Dreeb"과 같은 문자열을 입력하게 되면 Alistair를 name 배열에 저장한다.

    -  Dreeb은 입력 큐(input queue)에 남겨 놓는다.

    - cin이 다시 입력 큐를 검사할 때, Dreeb을 두 번째 문자열로 읽어 dessert 배열에 저장한다.

  - ### 한 번에 한 행의 문자열 입력 읽기

    - #### getline()을 이용한 행 단위 입력

      - Enter 키에 의해 전달되는 개행 문자를 입력의 끝으로 간주한다.

      - cin.getline()을 함수 호출로 사용함으로써 이 메서드를 호출할 수 있다.

        - ```cpp
          cin.getline(name, 20);	//20개의 원소를 가진 name 배열에 저장한다.
          ```

        - 두 번째 매개변수는 널 문자를 포함한 문자들의 최대 개수이다.

        - 행의 끝을 표시하는 개행 문자까지 읽지만 개행 문자는 저장하지 않는다.

        - 개행 문자는 null로 대체된다.

    - #### get()을 이용한 행 단위 입력

      - getline() 함수처럼 동작하지만, 개행 문자를 입력 큐에 남겨 둔다.

        - ```cpp
          cin.get(name, ArSize);
          cin.get(dessert, ArSize);	//문제 발생
          ```

          - 첫 번째 호출이 입력 큐에 개행 문자를 남겨 두기 때문에, 두 번째 호출은 개행 문자를 첫 문자로 만난다.

        - ```cpp
          cin.get(name, ArSize);	//첫 번째 행을 읽는다.
          cin.get();	//개행 문자를 읽는다.
          cin.get(dessert, ArSize);	//두 번째 행을 읽는다.
          ```

          - cin.get()을 사용하여 개행 문자를 읽어서 처리하고 다음 행의 입력으로 넘어갈 수 있다.

        - ```cpp
          cin.get(name, ArSize).get();
          ```

          - cin.get(name, ArSize)가 cin 객체를 리턴한다.
          - 리턴된 cin 객체는 뒤에 결합된 get() 함수를 호출하는 객체로 사용된다.

      - ##### getline() 대신에 get()을 사용하는 이유

        - 구식 C++에는 getline()이 없다.
        - getline()보다 에러 체킹이 쉽다.
          - 배열에 한 행을 저장하기 위해 get()을 사용했다고 가정한다.
          - get()이 배열의 수납 범위를 벗어나지 않는 전체 행을 읽어들였는지 알려고 할 때, 그 다음 입력 문자를 살펴보면 된다.
          - 다음 문자가 개행 문자이면 행 전체를 다 읽은 것이고, 개행 문자가 아니라면 그 행은 여전히 읽을 것이 남아 있는 것이다.

    - #### 빈 행과 기타 문제점

      - get()이 빈 행을 읽으면 failbit라는 것이 설정된다.

        - 계속되는 입력을 막고, 입력을 복원하려면 다음과 같은 명령을 사용해야 한다는 것이다.

        - ```cpp
          cin.clear();
          ```

      - 입력 문자열이 대입된 공간보다 더 길 수 있다.

        - 입력 행이 지정된 문자 수보다 길면, getline()과 get()은 나머지 문자들을 입력 큐에 그대로 남겨 둔다.
          - getline()은 failbit를 설정하고 더 이상의 입력을 받지 않는다.

  - ### 문자열과 수치의 혼합 입력

    - cin이 문자열을 읽어들이고, Enter 키가 만들어 내는개행 문자를 입력 큐에 남겨 두면, 다음 입력에서 개행 문자를 빈 행으로 읽어들인다.

      - 해결 방법

        - ```cpp
          cin >> year;
          cin.get();	//또는 cin.get(ch);
          ```

        - ```cpp
          (cin >> year).get();	//또는 (cin >> year).get(ch);
          ```



- ## string 클래스

  - 문자열을 저장하는 데 문자 배열을 사용하는 대신에, string형 변수(또는 객체)를 사용한다.

  - string 헤더 파일을 포함시켜 사용한다.

  - 여러 면에서 string 객체를 문자 배열과 동일한 방식으로 사용할 수 있다.

    - C 스타일 문자열로 string 객체를 초기화할 수 있다.
    - cin을 사용하여 string 객체에 키보드 입력을 저장할 수 있다.
    - cout을 사용하여 string 객체를 디스플레이할 수 있다.
    - 배열 표기를 사용하여 string 객체에 저장되어 있는 개별적인 문자들에 접근할 수 있다.

  - ```cpp
    string str1;	//빈 string 객체를 생성한다.
    string str2 = "panther";	//초기화된 string 객체를 생성한다.
    ```

    - str1 선언은 길이가 0인 string 객체를 생성한다.

    - ```cpp
      cin >> str1;	//str1은 입력에 맞게 크기가 조절된다.
      ```

    - 입력을 읽어 str1에 넣을 때 str1의 크기를 자동으로 조절한다.

  - ### C++11 문자열 초기화

    - 문자열과 문자열 객체에 리스트 초기화를 가능케 해준다.

    - ```cpp
      char first_date [] = {"Le Chapon Dobu"};
      string second_date [] = {"The Bread Bowl"};
      ```

  - ### 대입, 결합, 추가

    - string 클래스는 배열보다 조작이 간단하다.

      - string 객체를 다른 string 객체에 간단하게 대입할 수 있다.

      - ```cpp
        char charr1[20];	//빈 배열을 생성한다.
        char charr2[20] = "jaguar";	//초기화된 배열을 생성한다.
        string str1;	//빈 string 객체를 생성한다.
        string str2 = "panther";	//초기화된 string 객체를 생성한다.
        charr1 = charr2;	//틀리다, 배열 대입 no
        str1 = str2;	//맞다, 객체 대입 ok
        ```

    - string 클래스는 문자열 결합과 추가를 간단하게 처리한다.

      - \+연산자를 사용하여 두 개의 string 객체를 하나로 결합할 수 있다.

      - += 연산자를 사용하여 기존의 string 객체의 끝에 또 다른 string 객체를 덧붙일 수 있다.

      - ```cpp
        string str3;
        str3 = str1 + str2;	//결합된 두 string 객체를 str3에 대입한다.
        str1 += str2;	//str1의 끝에 str2를 추가한다.
        ```

  - ### 다른 형태의 문자열 상수

    - C++은 char형 이외에도 wchar_t형이 있고, C++11에는 char16_t와 char32_t를 추가로 가지고 있다.

      - 이러한 형들의 배열과 문자열 상수가 가능하다.

      - C++은 문자열 상수를 초기화하기 위해 L, u, U의 접두사를 가지고 있다.

        - ```cpp
          wchar_t title[] = L"Chief Astrogator";	//w_char 문자열
          char16_t name[] = u"Felonia Ripova";	//char_16 문자열
          char32_t car[] = U"Humber Super Snipe";	//char_32 문자열
          ```

    - C++11은 raw 문자열을 지원한다.

      - raw 문자열에 있어서 문자들은 독립적으로 존재한다.
      - R의 접두사를 가지고 있다.
      - ex) \n이 newline 문자가 아닌 backslash와 n이라는 두개의 문자로 인식된다. 



- ## 구조체(structure)

  - 서로 관련된 정보를 하나의 단위로 묶어서 저장할 수 있다.

  - 하나의 구조체 안에 여러 종류의 데이터를 저장하 수 있기 때문에 배열보다 융통성이 있다.

  - 구조체는 두 단계를 거쳐 생성된다.

    - 구조체 서술(structure description) : 구조체 안에 저장할 여러 가지 데이터형들을 서술하고 이름을 정한다.

      - ```cpp
        struct inflatable	//구조체 선언
        {
            char name[20];	//멤버
            float volume;
            double price;
        };
        ```
        - 키워드 struct는 이 코드가 구조체 서술을 정의하고 있다는 것을 나타낸다.
        - inflatable은 태그(tag)라고 부르며 새로 만들어지는 데이터 형의 이름으로 사용된다.
        - { } 안에는 이 구조체를 구성하는 데이터형들의 리스트를 넣는다.
          - 이 리스트의 각 항목을 멤버(member)라고 부른다.

    - 구조체 변수(structure variable) : 구조체 데이터 객체를 생성하는 단계이다.

      - ```cpp
        inflatable hat;	//inflatable형의 구조체 변수
        inflatable woopie_cushion;	//inflatable형의 구조체 변수
        inflatable mainframe;	//inflatable형의 구조체 변수
        ```

      - C 언어에서는 구조체 변수를 선언할 때 키워드 struct를 요구하지만 C++에서는 생략이 가능하다.

      - C++에서는 구조체 태그를 기본 데이터형의 이름처럼 사용할 수 있다.

      - 멤버 연산자(.)를 사용하여 구조체의 개별적인 멤버에 접근할 수 있다.

  - ### 프로그램에 구조체 사용하기

    - 구조체는 선언을 두는 위치를 정하는 두 가지 방법이 있다.
      1. main() 함수의 안에 여는 중괄호 바로 뒤에 선언을 둔다.
      2. main() 함수의 앞에 선언을 둔다.
         - 외부 선언(external declaration)이라 한다.
    - 외부 선언은 선언 이후에 나오는 모든 함수들이 사용할 수 있다.
    - 내부 선언은 그 선언이 들어 있는 함수에서만 사용할 수 있다.
    - 일반적으로 프로그래머들은 모든 함수들이 구조체를 사용할 수 있도록 구조체를 외부적으로 선언하고 있다.
    - 변수는 외부 변수의 사용은 가급적 금지한다.

  - ### C++11의 구조체 초기화

    - ```cpp
      inflatable duck {"Daphne", 0.12, 9.98};	//C++에서는 '='을 생력할 수 있다.
      ```

    - ```cpp
      inflatable mayor {};	//각각의 멤버에 대하여 0으로 초기화한다.
      ```

  - ### 구조체의 기타 특성

    - C++에서는 사용자가 정의한 데이터형을 내장 데이터형과 동일한 방식으로 다룰 수 있다.

      - 구조체를 함수에 매개변수로 전달할 수 있다.
      - 구조체를 리턴 값으로 사용할 수 있다.
      - 대입 연산자(=)를 사용하여 하나의 구조체를 같은 데이터형의 다른 구조체에 대입할 수 있다.
        - 이와 같이 멤버 단위로 대입되는 것을 멤버별 대입(memberwise assignment)이라 한다.

    - 구조체 템플릿의 정의와 구조체 변수의 생성을 하나로 결합할 수 있다.

      - ```cpp
        struct perks
        {
            int key_number;
            char car[12];
        } mr_smith, ms_jones;	//두개의 perks형 변수
        ```

    - 변수를 생성할 때 초기화도 함께 처리할 수 있다.

      - ```cpp
        struct perks
        {
            int key_number;
            char car[12];
        } mr_glitz =
        {
            7,	//mr_glitzs.key_number 멤버의 값
            "Packed"	//mr_glitz.car 멤버의 값
        }
        ```

    - 데이터형 이름이 없는 구조체를 생성할 수 있다.

      - ```cpp
        struct	//태그가 없다.
        {
            int x;	//두개의 멤버
            int y;
        } position;	//구조체 변수
        ```

      - position.x와 같이 멤버 연산자를 사용하여 멤버에 접근할 수 있다.

      - 데이터형 이름이 없기 때문에 이후에 같은 형의 다른 변수를 생성할 수 없다.

  - ### 구조체의 배열

    - #### 구조체의 배열을 만드는 방법

      - 기본 데이터형의 배열을 만드는 것과 같다.

      - ex) inflatable형 구조체 100개를 원소로 가지는 배열 생성

        - ```cpp
          inflatable gifts[100];	//inflatable형 구조체 100개의 배열
          ```

    - #### 구조체의 배열을 초기화하는 방법

      - 구조체 초기화 규칙과 배열 초기화 규칙을 하나로 결합하는 것이다.

      - 배열 원소가 구조체이므로 배열 원소의 각 값을 구조체 초기화 형식으로 나타낸다.

      - 그렇게 묶여진 배열 원소 값을 리스트를 콤마로 다시 분리하고 중괄호로 묶는다.

      - ```cpp
        inflatable guests[2] =
        {
            {"Babi", 0.5, 21, 99},	//첫 번째 배열 원소인 구조체
            {"Godzilla", 2000, 565, 99}	//두 번째 배열 원소인 구조체
        }
        ```

  - ### 구조체 안의 비트 필드

    - 구조체 멤버들이 각각 일정 비트 수를 차지하도록 지정할 수 있다.

    - 어떤 하드웨어 장치에 들어 있는 레지스터에 대응하는 데이터 구조를 만들 때 편리하다.

    - 필드 형은 정수형이나 열거자여야 한다.

    - 사용할 비트 수는 콜론을 찍고 그 뒤에 적는다.

    - 이름이 없는 필드를 사용하여 간격을 줄 수 있다.

    - 이러한 각 멤버를 비트 필드라고 한다.

    - ```cpp
      struct togle_register
      {
          unsigned int SN : 4;	//SN 값(4비트)
          unsigned int : 4;	//사용하지 않음(4비트)
          bool goodIn : 1;	//유효한 입력(1비트)
          bool goodTorgle : 1;	//토글에 성공(1비트)
      }
      ```

    - 보통의 방식으로 필드들을 초기화할 수 있다.

      - ```cpp
        torgle_register tr = {14, true, false};
        ...
        if (tr.goodIn)
        ...
        ```



* ## 공용체(union)

  * 서로 다른 데이터형을 한 번에 한 가지만 보고나할 수 있는 데이터 형식이다.

  * 구조체와 달리 공용체는 데이터형 중에 한 번에 어느 하나만 보관할 수 있다.

  * ```cpp
    union one4all
    {
        int int_val;
        long long_val;
        double double_val;
    };
    
    one4all pail;
    pail.int_val = 15;	//int형을 저장
    cout << pai.int_val;
    pail.double_val = 1.38;	//double형을 저장, int형 값은 소실
    cout << pail.double_val;
    ```

  * 공용체의 크기는 가장 큰 멤버의 크기가 된다.

  * 여러 가지 데이터형을 사용할 수는 있지만 이들을 동시에 사용할 수없을 때, 공용체를 사용하면 메모리를 절약할 수 있다.



* ## 열거체(enumeration)

  * const를 사용하여 기호 상수를 만드는 것에 대한 또 다른 방편을 제공한다.

  * 제한적이기는 하지만 새로운 데이터형을 정의할 수 있게 해준다.

  * ```cpp
    enum spectrum {red, orange, yellow, green, blue, violet, indigo, ultraviolet};
    ```

    * spectrum을 새로운 데이터형의 이름으로 만든다. enum형 변수를 열거체(enumeration)이라 부른다.
    * red, orange, yello ... 등을 0에서 7까지의 정수 값을 각각 나타내는 기호 상수로 만든다. 이 상수들을 열거자(enumerator)라 부른다.

  * 기본적으로 첫 번째 열거자에 0이 대입되고, 두 번째 열거자에 1이 대입되는 방식이다.

  * 열거체의 이름을 사용하여 열거형의 변수를 선언할 수 있다.

    * ```cpp
      spectrum band;	//band는 spectrum형의 변수
      ```

  * 열거체의 변수에는 데이터형을 정의하는 데 사용된 열거자 값들만 대입할 수 있다.

    * ```cpp
      band = blue;	//맞다, blue는 열거자이다.
      band = 2000;	//틀리다, 2000은 열거자가 아니다.
      ```

  * 열거체는 대입 연산자만 사용하도록 정의되어 있다. (산술 연산 허용 X)

    * ```cpp
      band = oragne;	//맞다.
      ++band;	//틀리다.
      band = orange + red;	//틀리다.
      ```

  * 열거자들은 정수형이며 int형으로 승급될 수 있다. 그러나 int형이 자동으로 열거체로 변환되지는 않는다.

    * ```cpp
      int color = blue;	//맞다, spectrum형이 int형으로 승급된다.
      band = 3;	//틀리다, int형이 spectrum형으로 변환되지 않는다.
      color = 3 + red;	//맞다, red가 int형으로 변환된다.
      ```

  * 명시적인 데이터형 변환을 사용하면, int형 값을 열거체 변수에 대입할 수 있다.

    * ```cpp
      band = spectrum(3);	//3을 spectrum형으로 데이터형 변환
      ```

  * 상수만 사용할 계획이고 열거체 변수를 만들 생각이 없다면 열거체 이름을 생략할 수 있다.

    * ```cpp
      enum {red, orange, yellow, green, blue, violet, indigo, ultraviolet};
      ```

  * ### 열거자 값의 설정

    * 대입 연산자를 사용하여 열거자의 값을 명시적으로 지정할 수 있다.

      * ```cpp
        enum bits {one = 1, two = 2, four = 4, eight = 8};
        ```

      * 이때 대입되는 값들은 정수여야 한다.

    * 일부 열거자에만 명시적으로 값을 대입할 수 있다.
    
      * ```cpp
        enum bigstep (first, second = 100, third);
        ```
    
      * 이러한 경우, first는 기본적으로 0이고, 뒤에 오는 초기화하지 않은 열거자들은 바로 앞의 열거자보다 1만큼 크다. 그래서 thrird는 101이 된다.
    
    * 하나 이상의 열거자들이 같은 값을 가질 수 있다.
    
      * ```cpp
        enum {zero, null = 0, one, numero_uno = 1};
        ```
    
      * zero와 null이 0이고, one, numero_uno가 1이다.
    
  * ### 열거체의 값 범위

    * 각 열거체는 값 범위를 가진다.

    * 어떤 정수값이 그 범위 안에 들어 있으면, 그것이 열거자 값이 아니더라도 데이터형 변환을 통하여 열거체 변수에 대입할 수 있다.

      * ```cpp
        enum bits {one = 1, two = 2, four = 4, eight = 8};
        bits myflag;
        
        myflag = bits(6);	//맞다, 6이 bits 범위 안에 들어 있다.
        ```
