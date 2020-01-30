# D3DXMatrixRotationYawPitchRoll

* D3DXMatrixRotationYawPitchRoll(

  D3DXMATRIX * pOut,  //회전이 되어 나오는 행렬

  FLOAT Yaw,					//y축으로 radian 값만큼 회전한다.

  FLOAT Pitch,				  //x축으로 radian 값만큼 회전한다.

  FLOAT Roll 					//z축으로 radian 값만큼 회전한다.

  );

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

