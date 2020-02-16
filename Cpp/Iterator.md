# 반복자(Iterator)

* 컨테이너에 저장된 원소를 순회하면서 접근하는 방법을 제공한다.

* 컨테이너와 알고리즘이 하나로 동작하게 해주는 인터페이스 역할을 한다.

* 모든 컨테이너의 반복자는 공통적으로 멤버 함수 begin()과 end()가 있고 이는 순차열의 시작과 끝을 가르킨다.

  * end()는 실제 원소를 가르키는게 아니라 끝을 표시하는 원소이다.(past the end)

* ```cpp
  #include <iostream>
  #include <vector>
  
  int main()
  {
      std::vector<int> v;
      v.push_back(0);
      v.push_back(1);
      v.push_back(2);
      
      std::vector<int>::iterator iter;
      for (iter = v.begin(); iter != v.end(); iter++)
          std::cout<<"vector : " << *iter << std::endl;
      
      iter = v.begin();
      std::cout << iter[0] << std::endl;
      std::cout << iter[1] << std::endl;
      std::cout << iter[2] << std::endl;
      
      return 0;
  }
  ```

* ## 반복자의 종류

  * 입력 반복자(Input Iterator) : 읽기만 가능하고 순방향 이동, 현 위치의 원소를 한 번만 읽을 수 있는 반복자이다.
  * 출력 반복자(Output Iterator) : 쓰기만 가능하고 순방향 이동, 현 위치의 원소를 한 번만 쓸 수 있는 반복자이다.
  * 순방향 반복자(Forward Iterator) : 읽기/쓰기 모두 가능하고 순방향 이동이 가능한 재할당 될 수 있는 반복자
  * 양방향 반복자(Bidirection Iterator) : 읽기/쓰기 모두 가능하고 순/역 방향 이동이 가능한 반복자이다.
  * 임의 접근 반복자(Random Access Iterator) : 읽기/쓰기 모두 가능하고 임의 접근, 양방향 반복자 기능에 +,-,+=,-=, [] 연산이 가능하다.