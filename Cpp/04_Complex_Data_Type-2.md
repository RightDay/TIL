* ## 포인터와 메모리 해제

  * 포인터는 값 자체가 아니라 값의 주소를 저장하는 변수이다.

  * 주소 연산자(&)를 변수 앞에 붙이면 그 변수의 주소를 알아낼 수 있다.

    * home이 변수면 &home은 그 변수의 주소이다.

    * ```cpp
      int donuts = 6;
      double cups = 4.5;
      
      cout << "donuts의 값 = " << donuts;
      cout << ", donuts의 주소 = " << &donuts << endl;
      
      cout << "cups의 값 = " << cups;
      cout << ", cups의 주소 = " << &cups << endl;
      ```

      * donuts = 6, donuts의 주소 = 0012FF7C

        cups의 값 = 4.5, cups의 주소 = 0012FF74

    * 16진수 표기가 메모리를 나타내는 가장 일반적인 방법이기 때문에 주소값을 출력할 때 16진수 표기를 사용한다.

    * 이 C++에서는 cups를 donuts보다 낮은 메모리 위치에 저장하였다.

      * 여기서 두 주소 간의 차이는 0012FF7C - 0012FF74이므로 8바이트이다.
      * cups가 8바이트를 사용하는 double형이기 때문이다.

    * C++ 시스템 마다 출력하는 주소가 다르다.

  * ### 포인터와 C++의 철학

    * 객체 지향 프로그래밍은 컴파일 시간이 아닌 실행 시간에 어떤 결정을 내린다는 점을 강조한다.
    * ex) 객체 지향 프로그래밍에서는 배열의 크기를 실행 시간에 결정할 수 있다.
      * 이것이 가능하려면, 프로그램이 실행되는 동안에 배열 또는 그와 동등한 것을 생성할 수 있어야 한다.
      * C++에서는 new라는 키워드를 사용하여 원하는 만큼의 메모리를 대입하고, 이렇게 대입된 메모리의 위치를 포인터를 사용하여 추적할 수 있다.

  * 포인터의 이름이 주소를 나타낸다.

  * 간접값(indirect value) 연산자 또는 간접 참조(dereferencing) 연산자라고 부르는 *를 포인터 이름 앞에 붙이면 그 주소에 저장되어 있는 값이 된다.

    * ```cpp
      int updates = 6;	//int형 변수를 선언
      int * p_updates;	//int형을 지시하는 포인터를 선언
      
      p_updates = &updates;	//int형의 주소를 포인터에 대입
      
      //값을 두 가지 방법으로 표현
      cout << "값 : updates = " << updates;
      cout << ", *p_updates = " << *p_updates << endl;
      
      //주소를 두 가지 방법으로 표현
      cout << "주소 : &updates = " << &updates;
      cout << ", p_updates = " << p_updates << endl;
      
      //포인터를 사용하여 값을 변경
      *p_updates = *p_updates + 1;
      cout << "변경된 updates = " << updates << endl;
      return 0;
      ```

      * 실행 결과

        값 : updates = 6, *p_updates = 6

        주소 : &updates = 0012FF7C, p_updates = 0012FF7C

        변경된 updates = 7