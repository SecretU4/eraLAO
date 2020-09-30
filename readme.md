# eraLAO 리드미

본 게임은 카카오봇 파티마봇의 에라라오 또는 에라라오PE의 요소를 기반으로 하여 emuera 엔진을 활용해 제작한 게임입니다.  
emuera 엔진 활용 과정에서 eraTWKR와 eraTHYMKR의 시스템 코드를 일부 인용 및 참고, 악마메이드의 시스템 코드를 참고했습니다.  
본 문서의 작성 당시의 게임 버전은 v0.992 이며, beta 버전이기에 아직 구현되지 않은 기능들이 존재하며 다양한 버그들이 혼재하고 있습니다. 발생한 버그를 보고해주시면 조속한 시일 내에 처리할 수 있도록 하겠습니다.

## 라이선스 관련사항

* 본 게임 내 시스템 파일의 라이선스는 딱히 정해진 바가 없습니다만 상업적 이용을 하시고자 하실때에는 관리자의 허락을 받으셔야 합니다.
* 본 게임 내 개별 메시지 파일의 라이선스는 개별 라이선스에 따릅니다. 명기된 라이선스가 없다면 시스템 파일의 것과 같습니다.
* 본 게임 내 `resources` 폴더의 이미지 파일은 카카오봇 버전의 것을 가져온 것으로, 카카오봇에서의 저작권을 그대로 따릅니다.
* 본 게임의 구동파일인 *Emuera1824.exe*와 *XEraEmulator.exe*는 개별 라이선스를 따릅니다.

## 이용 방법

* 컴퓨터 사용
  1. 본 파일의 압축을 풉니다.
  2. *XEraEmulator.exe* 를 눌러 실행합니다.
* 스마트폰 사용
  1. 인터넷을 통해 uEmuera 어플리케이션을 다운받습니다.
  2. 해당 어플리케이션의 이용방법을 따라 진행하시면 됩니다.
* *Emuera1824.exe* 사용법  
  *Emuera1824.exe*을 이용해 실행할 경우 `.webp` 포맷을 지원하지 않기 때문에 해당 이미지 파일들의 포맷을 변경하셔야 합니다.
  1. 본 파일의 압축을 풉니다.
  2. *EZworkEra*의 [convert_helper.exe](https://github.com/SecretU4/EZworkEra/releases/tag/v3.6.2)를 받습니다.
  3. 해당 툴을 이용해 `resources/` 디렉토리의 `.webp` 이미지 파일을 `.png` 이미지 파일로 변경합니다.
  4. 툴을 사용할 때 CSV/ERB 파일은 `resources/` 디렉토리 안의 것만 바꿔주시면 됩니다.
  5. *Emuera1824.exe*를 눌러 실행합니다.

## 원본 대비 구현사항 v 0.992

| 분류 | 항목 | 구현여부 | 분류 | 항목 | 구현여부 |
| --- | --- | --- | --- | --- | --- | --- |
| 시스템 | 홈 화면 | 구현 완료 |  | 상태보기 | 구현 완료 |
| | 랭킹보기 | 구현 불가 |  | 처음부터 | 구현 완료 |
|  | 헤어진다 | 구현 완료 |  | 종료 | 구현 완료 |
|  | 이름변경 | 구현 완료 |  | 대상변경 | 구현 완료 |
|
| 게임기능 | 요리 | 구현 완료 |  | 상점 | 구현 완료 |
|  | 연애 | 구현 완료 |  | 휴식 | 구현 완료 |
|  | 프롤로그 | 구현 완료 |  | 출격 | 구현 완료 | 
|
| 개별기능 | 개별대사 | 부분구현 |  | 개별화상 | 부분구현 |
|  | 엔딩 | 구현 완료 |  |  |  |

* 자료가 없는 개인 메시지 미구현

## 수정 예정사항

본 사항들은 v1.00 기반으로 작성되었음.

### 확인된 문제

1. 연애 커맨드
    * 순차적으로 나와야 할 내용이 랜덤 또는 한꺼번에 출력됨 - 수동으로 만져야 함
2. 개인 메시지 누락
    * `msg_collector.py`와 `EZworkEra`를 사용해 데이터베이스 내 개인 메시지(`json`)를 `ERB` 형태로 처리하고 있음
    * 누락된 메시지의 경우 수중에 있는 데이터가 없어 추가할 수 없거나 기계 처리시 누락된 것임.
        * 데이터가 없는 경우 데이터 획득시 추가 가능
        * 일부 문장/분기 등이 누락된 경우, 복잡한 경우가 아니라면 보고시 수동으로 수정 가능함.

### 추후 처리

1. 주석 가필  
  코드 수정을 용이하게 하기 위한 함수별 설명문 추가 예정.
2. 개인 메시지 출력 방식 개선  
  현 방식은 원판에 최대한 대응하여 개인 메시지 데이터의 기계적인 처리만으로도 어느정도 활용 가능하도록 되어 있으나 해당 방식으로 처리하기 위해 희생한 부분이 많음.(불필요한 `CFLAG`,`CSTR` 데이터의 생성 등)  
  따라서 기회가 된다면 개인 메시지 파일 안에서 최대한 처리할 수 있도록 수정할 계획이 있음.
