https://do-intekplus.atlassian.net/browse/SPIL600-289 에서도 동시에 관리 중, ==**동기화 수시 체크

<0818 이슈>
- [ ] 로더 바코드 리더 재튜닝 (AutoID Tuner)
	- 바코드 리더가 고정되지 않아서 많이 흔들림, 인식오류발생
	- 사용자 설정 - 영역 crop - 포커스 - 튜닝 - 인식 테스트
	- 인식률 70% 이상 되어야 안정권?
	- boat 3개 바코드 손상
- [x] 15번 축 44번 알람
	- 원인불명, 하드웨어 문제로 추측되어 전장팀에 문제분석 의뢰
	- 모터 교체
- [x] picker : Homing시 실린더를 업하고 갭 조절 (340/640 기본)
- [ ] 패키지를 집고 있을때 실린더가 업되면 패키지가 떨어짐
	- Vaccum 센서를 통해 감지하여 패키지가 안떨어지도록 안전장치

\<issues>
- [x] [UI] 3D bottom 항목제거 필요
- [x] [New recipe wizard] 3D bottom 항목제거 필요
- [ ] [New recipe wizard] Boat 이미지 변경
- [x] [Package model] Vision option - 3D bottom 항목제거 필요
- [ ] [Boat model] Boat 이미지 변경
- [ ] [Sort model] 3D insp 항목제거 필요
- [ ] [IR TOP] 3D insp 항목이 남아있음, 수정필요
- [ ] [Multipicker setup wizard] 전반적인 세팅 (3D bottom 없애는 것 포함)
- [x] [System option] System ID - 340으로 되어있음, 변경 필요
- [ ] ~~[System option] Use seperate invalid package sorting - 3D bottom invalid sorting rail 항목제거 필요~~
- [x] [System option] Remaining Review Image directory - 3D bottom 항목제거 필요
- [x] [JAM property - Inspect Picker1]3D 관련 메시지 남아있음, 항목제거 필요 (6, 7, 8)
- [x] [JAM property - TOP IR Inspector] 3D 관련 메시지 남아있음, 항목제거 필요 (3)
- [x] [JAM property - Side Inspector] 3D 관련 메시지 남아있음, 항목제거 필요 (18)
- [ ] [Debug] 3D insp 관련 항목이 남아있음, 항목제거 필요
- [ ] [Hanlder map] 600MH 모델로 그림 수정필요
- [ ] [Manual Inspection] Action 버튼 위 드롭박스 3D Ref. Test / Pick boat to JIG / Pick JIG to boat 메뉴, 항목제거 필요
- [ ] [Manual Inspection] Auto Calibration : 동작확인이 필요하나 640HX에서 쓰던기능이며 핸들러 구조가 많이 다르기에 제대로 동작하지 않을것으로 예상됨, 항목제거?
- [x] [Manual Inspection] Auto Focus Tuning - Recipe Z offset - Apply Difference to 3D BTM INSP. Z Offset
- [ ] [Lot] 2D top 메모리 할당 이슈
	- 현재 메모리 64GB, 메모리 부족으로 쓰레드를 적게 할당하여 사용중임, 향후 256GB 까지 늘릴것
- [ ] [PEAR] probe config - 3D bottom 항목
- [ ] [Self Condition Check] 시 Jam 메시지와 함께 UI가 변경됨

\<bug list>
- [ ] ~~[Pad changing] 레시피 미오픈일때 Pad changing을 할 경우 프로그램 크래시~~
	- 최초 설치시 레시피 미오픈 상태, 재현 힘듬
- [x] [Self condition check] Self condition check 클릭시 프로그램 크래시
- [ ] ~~[TTM] Actuator Speed Manager 클릭 시 프로그램 크래시~~
	- 메뉴 없어짐, 재현 불가
- [x] [Lot] Rear Side inspection 시 패키지 픽업 후 촬영할때 motor 오류 발생 (Jira 등록)
	- 모터 교체
	- Jira 상태 업데이트 요청
- [ ] [Manual Inspection] Auto focus tuning - Live 동작 안함 (Jira 등록)
- [ ] [Manual Inspection] Auto focus tuning - JOG 동작 안함 (Jira 등록)
---
---아래 사항부터는 모두 Jira 등록됨---
- [ ] 고질적인 문제 (사소한 문제일 수 있으나 사용성에 신경쓴다면 고치고 넘어가야 함)
	- [ ] insp item setup시 항목을 더블클릭하면 상세항목을 볼 수 있어야 하나 프로그램 크래시 발생 (iPIS340HX에서 발생했던 현상)
	- [ ] ~~insp item setup에서 Use로 되어있는 항목을 체크해제 하고 Cancel 할 경우 변경은 없으나 재진입시 체크 해제된 상태로 보임, 설정에는 큰 변화 없음 (iPIS340HX에서 발생했던 현상)~~ -> ==UI 이슈로 통합하여 올림
	- [ ] surface criteria에서 polygon 추가 후 순서 변경 뒤에 polygon 크기를 변경하거나 이동했을때 프로그램 크래시 (iPIS500I에서 발생했던 현상)
	- [ ] surface criteria에서 상세설정값 입력시에 문자가 그대로 입력되는 현상
- [ ] [Manual Inspection] Side 설정 중 2D 탭에서 offset 설정시 Side 1을 설정하면 Side 2에 적용됨 (서로 교차되어 적용)
	- Package Model - Side Picker offset 에도 동일한 현상인지 체크 필요
- [ ] [Side vision] Stitching Align 후 이후 시퀀스(Emtpy checker Blob, Edge align)에 Stitching 결과가 적용되지 않음, 0 pane을 선택하면 변경되나 Run inspection 시 원본 이미지로 돌아감
- [ ] BGA Ball inspection - Ball align 후 ball의 중심점이 잘못 표시되는 문제
- [ ] image 오픈 후 Pan image와 Show whole image 기능 일시적 비활성화
- [ ] Host에서 고배율 체크 및 해제시 Vision에 Scale 반영 안되는 문제
- [ ] batch inspection 기능 진입 후 quit 시 이미지를 획득하는 현상
- [ ] 레시피 항목 중 2D Bottom Vision Z High Magnification Offset 값 저장 안됨