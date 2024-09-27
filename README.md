# dynamixel_controller
순서대로 실행

```
git clone https://github.com/power-on-github/dynamixel_controller
```

```
conda create -n dynamixel python=3.7 -y
```

```
conda activate dynamixel
```

```
pip install dynamixel-sdk
```

```
python3 dynamixel_controller.py
```

## 사용법

우선, dynamixel_controller.py 파일 안의 세팅값들을 사용중인 다이나믹셀에 맞게 바꾸세요.

그 후, 다이나믹셀을 움직일 객체를 다음과 같이 생성합니다. 

``` python
# single dynamixel
xel = DynamixelController(dxl_id=1, initial_pos=512, torque_on=True)
# multiple dynamixel
xel = DynamixelController(dxl_id=[1, 2, 3], initial_pos=[512, 512, 512], torque_on=True)
```

`dxl_id`: 다이나믹셀의 id입니다. Dynamixel Wizard를 통해 확인 가능합니다. 

`initial_pos`: 다이나믹셀의 초기 위치를 지정합니다. 아무 입력도 넣지 않을 수 있으며, 이 경우 초기에 셀은 이동하지 않습니다. 또한, `torque_on` 옵션이 `True` 여야 동작합니다.

`torque_on`: 다이나믹셀에 토크를 걸지에 대해 결정합니다. 기본값은 `True` 입니다. 토크가 걸려있지 않다면, 다이나믹셀을 움직일 수 없습니다. 

이제 Dynamixel 객체 안의 다양한 매써드들을 이용하여 셀을 조작할 수 있습니다. 

### torqueOn()
다이나믹셀의 토크를 켭니다. 코드는 다음과 같습니다. 
``` python
xel.torqueOn()
``` 
### torqueOff()
다이나믹셀의 토크를 끕니다. 코드는 다음과 같습니다. 
``` python
xel.torqueOff()
```
### moveDynamixel(dxl_goal_position)
다이나믹셀을 원하는 위치로 옮깁니다. 코드는 다음과 같습니다. 
``` python
# 여러 다이나믹셀이 연결된 경우
dxl_goal_position = [1000, 500, 100] 
# 하나의 다이나믹셀이 연결된 경우
dxl_goal_position = 100

xel.moveDynamixel(dxl_goal_position)
```
### moveSingleDynamixel(dxl_goal_position)
하나의 다이나믹셀만 연결된 경우에만 정상적으로 동작합니다. 
`moveDynamixel` 매써드를 쓰는 것을 보다 추천합니다. 
다이나믹셀을 원하는 위치로 옮깁니다. 코드는 다음과 같습니다. 
``` python
dxl_goal_position = 100

xel.moveDynamixel(dxl_goal_position)
```
### moveGroupDynamixel(dxl_goal_position)
여러개의 다이나믹셀이 연결된 경우에만 정상적으로 동작합니다. 
`moveDynamixel` 매써드를 쓰는 것을 보다 추천합니다. 
다이나믹셀을 원하는 위치로 옮깁니다. 코드는 다음과 같습니다. 
``` python
dxl_goal_position = [1000, 500, 100] 

xel.moveDynamixel(dxl_goal_position)
```
### getPosition()
다이나믹셀의 현재 위치값을 반환합니다. 코드는 다음과 같습니다. 
``` python
xel.getPosition()
```
### getSinglePosition()
하나의 다이나믹셀만 연결된 경우에만 정상적으로 동작합니다. 
`getPosition` 매써드를 쓰는 것을 보다 추천합니다. 
다이나믹셀의 현재 위치값을 반환합니다. 코드는 다음과 같습니다. 
``` python
xel.getSinglePosition()
```
### getGroupPosition()
여러개의 다이나믹셀이 연결된 경우에만 정상적으로 동작합니다. 
`getPosition` 매써드를 쓰는 것을 보다 추천합니다. 
다이나믹셀의 현재 위치값을 반환합니다. 코드는 다음과 같습니다. 
``` python
xel.getGroupPosition()
```

