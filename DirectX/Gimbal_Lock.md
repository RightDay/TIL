* # 짐벌락 현상 (Gimbal Lock)

* 짐벌(Gimbal)
  * ![gimbal](./image/Gimbal_Lock/gimbal.gif)
  * 물체가 회전하도록 중심축을 가진 구조물이다.
  * 3차원 공간에서는 오일러 각도를 사용하여 **세 번의  회전**을 통해 얻는다.
  
* 오일러 각(Euler Angle)
  
  * 3차원 공간에서 각 **x, y, z 축의 회전량을 정해진 순서 대로 적용**했을 때 물체의 모든 방향을 표현할 수 있는 방법이다.
  
* 짐벌락(Gimbal Lock)

  * x축(Pitch), y축(Yaw), z축(Roll)의 세축이 회전 하다가 특정 축이 특정각으로 회전 했을 때, 두 축또는 세 축이 겹쳐서 한 축이 소실되는 현상이다.
  * 오일러 각 회전을 **순차적**으로 하기 때문에 발생한다.



* # D3DXMatrixRotationYawPitchRoll

  * z, x, y 순의 회전하여 짐벌락 현상을 회피할 수 있다.

  * D3DXMatrixRotationYawPitchRoll(

    D3DXMATRIX * pOut,  //회전이 되어 나오는 행렬

    FLOAT Yaw,					//y축으로 radian 값만큼 회전한다.

    FLOAT Pitch,				  //x축으로 radian 값만큼 회전한다.

    FLOAT Roll 					//z축으로 radian 값만큼 회전한다.

  ​		);

  ![YawPitchRoll](./image/YawPitchRoll.png)

  * ### Yaw(Vertical axis)
  
  * 물체의 바닥을 향하는 축이다.
    * 물체를 오른쪽으로 회전시키는 것이 양의 방향으로 움직인 것이다.

  * ### Pitch(Lateral axis)
  
  * 물체의 오른쪽으로 향하는 축이다.
    * 물체의 앞 부분을 위로 드는 것이 양의 방향으로 움직인 것이다.

  * ### Roll(Longitudinal axis)
  
    * 물체의 앞쪽으로 향하는 축이다.
    * 축을 중심으로 물체를 오른쪽으로 회전시키는 것이 양의 방향으로 움직인 것이다.

