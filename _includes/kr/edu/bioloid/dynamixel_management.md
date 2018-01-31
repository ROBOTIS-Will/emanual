로봇 관절로 사용되는 다이나믹셀은 매우 많은 기능들을 내장하고 있습니다. 여기서는 로봇을 만들면서 다이나믹셀의 설정을 바꾸는 방법에 대해 설명합니다.

#### ID바꾸기

다이나믹셀의 ID는 다음과 같이 변경할 수 있습니다.

1. 제어기가 연결된 포트를 설정합니다.
2. 연결 버튼을 누릅니다.

    ![](/assets/images/edu/bioloid/id_change_1_kr.png)

3. 왼쪽에서 연결된 다이나믹셀의 리스트를 확인할 수 있습니다. ID를 바꾸려는 다이나믹셀을 클릭합니다.
4. 컨트롤 테이블의 ID 열을 클릭합니다.
5. ID 목록 콤보박스를 클릭하면 현재 바꿀 수 있는 다이나믹셀의 ID를 볼 수 있습니다. 바꾸고자 하는 ID를 선택하고 적용 버튼을 누르십시오.

    ![](/assets/images/edu/bioloid/id_change_2_kr.png)

{% capture bioloid_beginner_01 %}
`ID변경시 유의사항`
- RoboPlus Motion과 로보플러스 태스크에서 사용하기 위해서는 ID의 범위를 다음과 같은 범위 내로 설정해야 합니다.  
  - 액츄에이터는 0~25 사이의 ID로 설정해야 합니다.  
  - AX-S1은 100~109 사이의 ID로 설정해야 합니다.
{% endcapture %}

<div class="notice">{{ bioloid_beginner_01 | markdownify }}</div>

#### 동작 모드 변경
다이나믹셀은 아래와 같은 2 가지 모드로 동작할 수 있습니다.

- 바퀴 모드 : 일반 모터와 같이 360도 회전하는 모드 (무한 회전 모드)
- 관절 모드 : 일반적인 서보 모터와 같이 0도 ~ 300도 사이의 정해진 각도로 움직이는 모드

모드 변경 방법은 아래와 같이 RoboPlus Manager 를 통해 변경할 수 있으며, 한 번 모드를 설정하면 전원을 차단해도 설정값이 유지됩니다.

1. 제어기가 연결된 포트를 설정합니다.
2. 연결 버튼을 누릅니다.   

    ![](/assets/images/edu/bioloid/mode_change_1_kr.png)
    
3. 왼쪽에서 연결된 다이나믹셀의 리스트를 확인할 수 있습니다. 모드를 변경하려는 다이나믹셀을 클릭하고, 컨트롤 테이블의 CW/CCW 위치 제한 열을 클릭합니다.
4. 바퀴 모드를 설정하려면 CW/CCW 위치 제한 컨트롤 테이블의 값을 모두 0으로 변경하면 됩니다. 다음과 같이 바퀴 모드 버튼을 클릭하여 쉽게 설정할 수도 있습니다.

    ![](/assets/images/edu/bioloid/mode_change_2_kr.png)

5. 다시 관절 모드로 설정하려면, CW/CCW 위치 제한 컨트롤 테이블 값을 0 이외의 값으로 설정하면 됩니다. 관절 모드 초기값은 CW 위치 제한 : 0, CCW 위치 제한 1023입니다.  

#### 문제 해결
RoboPlus Manager에서 다이나믹셀을 찾을 수 없는 경우가 발생합니다. 이런 경우는 다음과 같이 시도해보세요.

1. 다이나믹셀을 1개만 연결해서 ID가 중복되는지 확인해보세요.  
  1개만 연결했을 때 왼쪽 리스트에 다이나믹셀이 보이면 ID가 중복될 가능성이 큽니다. ID 변경하기를 통해 ID를 바꿔 주시기 바랍니다.   
2. 만약 다음 그림과 같이 리스트에서 다이나믹셀을 확인할 수 없다면 상세 검색 버튼을 누르시기 바랍니다.  
  상세 검색 기능은 다이나믹셀의 통신 속도가 1Mbps로 설정되어 있지 않은 경우, 속도를 1Mbps로 재설정하며 제어기에서 인식할 수 있도록 해 줍니다.

  ![](/assets/images/edu/bioloid/dxl_search_kr.png)  

  위와 같은 방법으로도 문제가 해결되지 않는다면, 다이나믹셀이 고장이 났을 가능성이 높습니다. 구입처에 A/S를 의뢰하시기 바랍니다.