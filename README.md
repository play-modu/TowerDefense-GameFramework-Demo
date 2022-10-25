# TowerDefense-GameFramework-Demo

## 프로필

이것은 오픈 소스 프레임 워크 [GameFramework][1] (이하 GF라고하는)를 기반으로 한 타워 방어 게임 데모입니다. 데모 프로토 타입은 공식적으로 데모 [타워 방어 템플릿] [2]에 공식적으로 배치된다. 이 프로젝트는 GF를 사용하여 다시 구현되고 데모 프로토 타입으로 확장됩니다. 주로 GF의 개인 학습 및 실습에 사용되며 GF를 공부하는 다른 학생들에게도 제공합니다.

## 버전 정보

- Unity 2019.4.1f1
- GameFramework 2020.07.30
- Tower Defense Template 1.4

#### 게임 프로필

### 게임 미리보기

![소개 1][4]
![소개 2][5]
![소개 3][13]
![소개 4][14]

### 게임 소개

이 게임은 총 5 레벨의 타워 방어 유형입니다. 각 레벨의 지형 환경, 적의 지형 환경, 유용한 타워는 다릅니다. 플레이어는 특정 상황에 따라 적절한 타워를 선택하고 적의 기지를 공격하지 않도록 적절한 위치에 구축합니다.

#### 에너지

플레이어는 레벨에서 소량의 초기 에너지를 가지고 있습니다. 적을 죽이고 에너지 타워를 건설함으로써 에너지를 얻을 수 있으며 에너지는 타워를 구축하고 업그레이드하는 데 사용됩니다.


#### 타워

1. Titani Turret : 고음 속도, 낮은 손상
2. 로켓 포탑 : 높은 AOE 피해 (만지지면 적용 만 공격)
3. 레이저 포탑 : 저율, 높은 손상, 장거리
4. 에너지 타워 : 에너지는 매번 생성됩니다.
5. 전자 펄스 타워 : 근처의 적에 대한 추가 감속 효과
6. 미사일 배열 : 대형 스케일 적에게 높은 피해를 입히고 현장에서 10 초 후에 자체 파괴를 일으 킵니다.
** 타워를 업그레이드 할 수 있으며 업그레이드 후 범위, 손상, 감속 속도, 에너지 생산 효율성 등을 향상시킬 수 있습니다.

#### 적

1. 웜 : 저혈량, 높은 움직임 속도
2. 헬리콥터 : 로켓 포탑의 공격을 피하고 포탑에 의해 도로가 막히면 터렛을 바로 바닥으로 직접 건너 갈 수 있습니다.
3. 탱크 : 높은 혈액량, 낮은 이동 속도
4. 보스 : 울트라 -높은 혈액량, 초고속 속도
5. 슈퍼 웜 : 혈액 혈액 혈액 버그
6. 슈퍼 헬리콥터 : 고혈압 헬리콥터
7. 슈퍼 탱크 : 고혈압 탱크
8. 슈퍼 보스 : 높은 혈액 볼륨 보스
** 적은 일반적으로 탑을 공격하지 않지만 탑이 적의 길을 완전히 막을 때 탑을 공격합니다 (헬리콥터 적은 탑을 공격하지 않고 탑을 직접 건너 갈 것입니다). 베이스이지만 타워가 공격을 방지하기 위해 완전히 차단되지 않았습니다 **

#### 베이스

기지는 적의 범죄의 궁극적 인 목표이며, 플레이어가 보호 해야하는 목표이기도합니다.베이스의 기초가 0이면 게임이 실패합니다.

#### 합의

플레이어가 레벨의 모든 적을 제거하고 기본 혈액량이 0이 아닌 경우, 세관 클리어런스가 성공적입니다. 모든 몬스터가 파괴되면 기본 혈액량이 0으로 공격하면 게임이 실패합니다. 성공적인 관세 클리어런스는 기초의 나머지 혈액량을 기준으로 점수가 매겨 질 것입니다.

## 관련 구현

이 프로젝트에서 GF에 사용된 여러 모듈에는 글로벌 구성, 데이터 테이블, 엔티티, 이벤트, 파일 시스템, 유한 상태 기계, 파일 시스템, 현지화, 객체 풀, 참조 풀, 프로세스, 리소스, 장면, 게임 구성, 사운드, UI 등이 포함됩니다.

### 데이터 구성

![데이터 구성][6]
게임의 모든 데이터는 Excel로 구성되며 이진 파일의 내보내기가로드되고 런타임 후에 읽습니다.

### 현지화
![현지화][7]
현지화 된 모듈 및 변형을 리소스 모듈에 사용하여 현지화를 달성하십시오.

### 견적 수영장
![견적 풀][8]
프로젝트의 많은 재사용 개체는 메모리 분포를 자주 피하기 위해 캐시의 참조 풀을 사용합니다.

### 리소스 포장 구성
![리소스 포장 구성 1][9]
![리소스 포장 구성 2][10]
모든 리소스가 포장 및 할당되었으며 올바른 하청 계약 정보, 파일 시스템이 설정됩니다. 그리고 0 중복 및 0 사이클 참조를 달성하기위한 구축 된 분석 도구를 기반으로합니다.

### 핫 업데이트
![핫 업데이트][11]
게임 시작은 버전 정보를 감지하고 기본 리소스 (즉, 비 레벨의 리소스)를 업데이트합니다.

### 하위 다운로드 다운로드

![핫 업데이트][12]
게임은 각 레벨 리소스에 대해 별도로 하청 계약을 맺습니다. 레벨에 들어가기 전에 해당 리소스를 다운로드하고 업데이트해야하지만 한동안 재생되지 않은 레벨은 한동안 다운로드 할 수 없습니다.
## 지침

이 게임은 편집기에서 기본적으로 편집기 모드로 시작합니다. 즉, 엔지니어링의 리소스 작업이 읽히고 AB 패키지는 읽거나 업데이트되지 않습니다. 이 프로젝트는 포장 정보를 위해 올바르게 구성되었고 해당 열 및 논리 구현을 완료했습니다. 업데이트 모드를 테스트하려면 기본 구성 요소에서 편집기 리소스 모드를 취소하고 리소스 구성 요소의 리소스 모드를 확인해야합니다. 업데이트 가능한 모드입니다. 리소스를 포장하고 리소스를 올바르게 배포 한 후에는 업데이트 모드를 정상적으로 실행할 수 있습니다 (HFS와 같은 도구의 도움으로 로컬로 배포 및 테스트 할 수 있음).

## 결론

저자 [Ellan Jiang][3]가 제공 한 훌륭한 프레임 워크에 감사드립니다.

  [1]: https://github.com/EllanJiang/GameFramework "GF link"
  [2]: https://assetstore.unity.com/packages/essentials/tutorial-projects/tower-defense-template-107692 "Tower Defense Template Link"
  [3]: https://github.com/EllanJiang "Ellan Jiang link"
  [4]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/1.png "소개 1"
  [5]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/2.JPG "소개 2"
  [6]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/3.png "데이터 구성"
  [7]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/4.JPG "현지화"
  [8]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/5.png "인용 된 연못"
  [9]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/6.png "리소스 포장 구성 1"
  [10]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/7.png "리소스 포장 구성 2"
  [11]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/8.png "핫 업데이트"
  [12]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/9.png "서브 포장 다운로드"
  [13]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/10.gif "소개 3"
  [14]: https://github.com/DrFlower/TowerDefense-GameFramework-Demo/blob/master/Doc/11.gif "소개 4"
