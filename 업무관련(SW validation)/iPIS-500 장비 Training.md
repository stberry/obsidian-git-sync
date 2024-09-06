==**0827 장비 OJT (or 0828)
- ~~Training schedule table 작성 ==(금일 점심시간 이전)==~~ ==업로드 완료
- due date : 0826 ~ 0906 (0910 입사직원 교육 예상, 주말 이용하여 교육자료 작성)
- OJT 이후, 금주 목요일부터는 확실하게 개인 Training 가능, 단, 개발부가 사용할 경우 Training 불가
- 따라서 붙잡고 있는 시간에 최대한 많이 장비를 만져볼 수 있도록 할 것 (야근 거의 필수)
- 차주 금요일(0906) 까지 OJT 가능 수준까지 익히는 것을 목표
- OJT시 셋업시퀀스 교육때 들었던 것처럼 동작프로세스를 설명듣고 궁금한 것 질문
  → ~~iPIS-380HX와 크게 다르지 않을것으로 예상됨~~
  → iPIS-500은 기존장비와 크게 다름 ==(중요)
- 9월 7일 ~ 9월 28일 (김동규 선임 출장)
- ~~뭐 물어볼때 김선임 음료라도 챙기기~~

0827 장비설명 (정리 후 confluence 페이지, 시뮬레이터 설치, 실행은 confluence 매뉴얼 페이지 업데이트)
- 오전 11시 ~, 장소 : A동 공장
- 장비는 검사대상과 검사방식에 따라 나뉘며 주 납품 모델은 iPIS-340, 380 쪽
	- 240, 240TR, 340, 340FX, ........, 380, 380HX 등 다수
	- 
- 빈 트레이가지고 테스트 (대상 receipe : KBLG_31X58.5-V10-TRAYSTITCH)
  ![[Pasted image 20240827180443.png]]
- iPIS-500 GANTRY - 기존 iPIS-500 장비에 GANTRY 설비를 덧붙인 장비로 CART에 패키지 트레이를 담아 일괄검사를 지원
	- 현재 GANTRY는 이슈가 있어 잘 동작하지 않으며 설비팀에 문의한 상황
- SW 버전 : Handler - 3.312.00.0230DD (development debug 버전, RD - release debug), Vision - 1.312.999.0120 Release Version
- Lot 단위로 검사
	- TRAY 개수는 상관없으나 loading elevator에는 최소 2 trays(1 tray for cover tray), empty elevator에는 최소 3 trays가 필요함(양품/불량 sort)
- 검사 단계
	1) interlock 확인
	2) init handler : 모터들의 영점을 잡아주는 역할
	3) setup : 2d top / bottom, 3d bottom enable 확인, (side, 3d top disable)
	4) 여러가지 동작 모드가 있으나 operator 권한에서는 보통 run mode를 많이 사용 (기계 제어를 위해서는 run mode가 일반적)
	5) option parameter
		- [ ] lot split : 이전 lot과 구분짓기 위해 사용 (거의 사용하지 않음)
		- [ ] all tray are loaded : 필수 check
		- [ ] rejects are not sorted : sort 여부에 대한 옵션, 체크시 불량체크 하지 않음
		- [ ] debug log : 상세 로그 기록 (operator 모드에 없음을 확인)
	6) 주의사항
		- 안전사고에 항상 유의(도어가 오픈되어있으므로 동작중에는 항상 안전에 유의, 일시정지시 주저말고 emo로 interrupt)
		- EMO 버튼 : 장비에 이상이 있을경우 emo를 눌러 모든 전원을 차단, 조치 후 reset 버튼을 눌러 전원 재인가

stand alone 실험 경과 (해결된 것 체크, supported by 김동규 선임, 김민철 선임)
1. [x] interlock 안된상태에서 init handler 하면 경고
       → 경고메시지 확인 후 interlock 확인
2. [x] Tray load (loading elevator, empty elevator)
       → 해당칸에 트레이 배치 (3개씩)
3. [x] z1 motor 빨간불 (세팅매뉴얼?)
       → 어떻게 조치해야 하는가? 대부분의 trouble shooting은 init handler로 가능
4. [ ] 트레이 jam, emo 이후 복구시 잘 안될때
       → 셋업팀 김경민 대리에 요청
5. [ ] 만약 프로그램이 죽거나 pc를 다시켜야 하는경우
       → D:\\(작업자 이니셜) 폴더에 솔루션 파일 실행 후 빌드 "D:\\DK\\iPIS500-SideVision"
       → Host PC password : 1
7. [x] 각 pc의 ip확인 (모든 pc는 tcp/ip로 통신하며 원격으로 제어가능)
       → 10.10.61.1 ? GANTRY
       → 나머지는 직접 찾아봐야 함
       → 각 vision software와 전환이 가능함 (vision-host switch 가능)
       → KVM switch를 사용하여 pc간 전환 (tap scroll lock * 2 rapidly then insert pc number (pc #1 : host pc, #2~6 : vision pc))

<장비 operation 이전 셋업>
- Jig를 사용하여 camera calibration
- 주기적으로 golden device 를 사용하여 vision camera focus나 calibration 작업 수행 (LTSM ?)
- site별로 요구사항에 따라 offset 값 조정
- package 별로 job parameter를 조정함, 이때 offset이나 job teaching 수행

<_Handler Teaching>
![[Pasted image 20240903103031.png]]
- Handler teaching : 핸들러에서 각 모터의 위치를 파악하고 각 모터의 속도, 위치에 대한 초기설정 값을 지정할 수 있다.
- IFM (Input Flipper Module)
- LFE (Loding Front Elevator) : 검사를 위한 package tray를 적재하고 운반
- 

<_Inspection flow>
1. **Empty Tray Input:** 초기 empty tray에서 tray를 한 장 가져가서 IFM의 top에 위치시킴 ==(cover tray 역할)
2. **TFM(Tray Flipper Module):** emplty tray에서 tray를 한 장 가져가서 대기시킴 (empty rail -> loader rail)
3. loading tray에서 검사를 위한 tray를 IFM bottom에 위치시킴 ==(package tray)
	1) loading tray에서 package tray를 계속 보충하며 검사 진행
4. IFM에서 cover tray를 package tray에 덮고 flip후 2d bottom으로 이동
5. **Bottom 2D inspection:** 2d bottom 촬영 (left top -> right bottom, horizontal)
6. **Bottem 3D inspection:** 3d bottom 촬영 (left top -> right bottom, horizontal)
7. TFM으로 이동, cover tray를 씌워 flip 후 top 촬영을 위해 이동
8. 2d top촬영, 3d top 촬영 (right bottom to left top, horizontal)
9. (optional) Side inspection: Side camera 촬영 (상하2면 촬영 후 rotate하여 좌우2면 촬영)
10. **Sorting:** reject tray, buffer tray, good tray를 분류, reject에는 불량만, good에는 양품만 모으는 작업, 그 사이에 buffer를 사용하여 임시로 저장
11. **Tray unloading:** Tray에 reject or good이 꽉차면 배출, 두 칸 모두 아직 배출 이전이라면 새로운 burffer 추가 ==(※여기서 sorter 중 hold 발생, 이유 파악, savelog-log 분석)==

> [!NOTE]
> ==(※ 반복 lot 수행하면서 발견되는 이슈사항은 모두 기록)==

<프로그램 다운 이슈>
- language 탭 선택시 프로그램 die
- +ROI (Region of Interest) 선택 후 -ROI선택했을때 응답없음 메시지, 프로그램 die
- (관리자모드-Intekplus) Setup탭 -> Regulator선택, 프로그램 die

<프로그램 사용 이슈>
- UI 적으로 모든 정보가 표시되지 않아 알아보기 힘듬 (글씨가 잘림)
  → 제어장비라 예쁘진 않더라도 기본사용성 정도는 챙겨야 하지 않을까 생각됨
- tray 세팅할때 가이드 그림이 옆에 있는 것은 좋음
- 이미지가 표시 안되는 것? no images (Handler teaching - Motor monitoring window)
- ~~클릭하면 뭐가 잘 안됨~~ (관리자 모드)
- Vision camera 촬영이 안됨 ==(무슨 옵션인가?)
- Job open이후 Job을 바꾸려고 했을때 에러코드 발생
	- SKXXCC_56.5X76_FOR_SIDEVISION : 정상동작 중 Sorting에서 holding (2lots)
	- SKXXCC_56.5X76_FOR_RUNTEST : 정상동작은 하나 Sorting이 되지 않는것 같음 (1lot, 몇 번 더 해봐야 함)
- Vision parameter size is invalid 오류 ==(어떤문제인지 자세히 파악 필요 (Job configuration))
	- SKXXCC_56.5X76
	- SKXXCC_56.5X76_5UP_V10
	- SKXXCC_56.5X76_5UP_V10_140
- 실험이 필요한 Job
	- SKXXCC_56.5X76_TEST
	- SKXXCC_56.5X76_TEST_OK
	- SKXXCC_56.5X76_TEST2
	- SKXXCC_56.5X76_TrayStitching
- 실험에 사용한 Job들은 비교분석 진행 (각 Job을 구성하는 parameter가 어떻게 다른지 비교, excel에 정리)
	- SKXXCC_56.5X76_FOR_SIDEVISION
	- SKXXCC_56.5X76_FOR_RUNTEST
	- SKXXCC_56.5X76
	- SKXXCC_56.5X76_5UP_V10
	- SKXXCC_56.5X76_5UP_V10_140
	- SKXXCC_56.5X76_TEST
	- SKXXCC_56.5X76_TEST_OK
	- SKXXCC_56.5X76_TEST2
	- SKXXCC_56.5X76_TrayStitching

<검사 대상 패키지(based on Manual)>
- BGA (Ball Grid Array)
	- 패키지에 달린 Ball의 상태를 측정하는 검사

- 검사항목 (inspection item)

| 2D                                                                                                                        | 3D                             | Surface                      |
| ------------------------------------------------------------------------------------------------------------------------- | ------------------------------ | ---------------------------- |
| - Ball offset X<br>- Ball offset Y<br>- Ball Width<br>- Ball Damage<br>- Ball Missing<br>- Ball Contrast<br>- Ball Bridge | - Ball Height<br>- Coplanarity | - Customized Inspection Item |
- 2D
	- Ball Dimention Item (Ball Width, Offset X, Y, R)
		- align이 완료된 좌표의 Width 값과 촬영 데이터 값의 데이터를 비교
	- Ball Grid offset
		- Ball offset과 다르게 Ball들의 Pitch값은 Spec과 차이가 없으나 전체적인 Ball의 위치가 실장되어야 할 위치에서 벗어났는지 offset X, Y를 측정
	- Ball  Quality (Ball Damage)
		- Ball의 손상정도를 측정함
		- Normal Method / Ring Thickness Method
	- Ball Missing
		- 현재 제공되고 있는 모델의 Ball 개수와 실제 Ball의 개수 차이를 검사함
	- Ball Contrast
		- 볼 전체의 Gray Value의 평균값의 차, 즉, 촬영 데이터에서 Ball의 밝기를 측정
	- Ball Bridge
		- Ball 주변에 이물질이 생겨 Ball과 Ball사이가 다리처럼 이어지는 형태를 검사
- 3D
	- Ball height
		- 바닥에서 Ball 상단까지의 수직거리
		- 휨(Warpage)이 있을때와 없을때로 구분
		- iPIS-500에서는 주변 바닥면과 Ball의 높이를 이용하여 정확한 Ball의 높이를 측정함
	- Ball Coplanarity (Ball의 등평면도)
		- 평평한 바닥면에 위치한 Ball이 같은 높이를 이루고 있는지를 측정
		- LMS Plane으로 reference plane을 구하여 global plane으로 만든 후 오차값을 이용해 Coplanarity를 계산
	- Warpage (휨)
		- 바닥면의 휘어짐 정도 측정
		- LMS Plane으로 reference plane을 구하여 global plane으로 만든 후 오차값을 이용해 Warpage를 계산


<검사 결과화면 분석(vision software)> **※ 초안 기입 후 정확히 파악하여 문서화**
- (TBD)
- Vision software는 2D / 3D 비전 사용전에 Jig를 이용하여 초기 값을 장비에 Teaching 한다. 향후 Site에서 사용시 패키지 스펙과 요구사항에 따라 offset값을 조정한다.
- Access level - admin, Job teaching
- 동축, 사축, vision
- vision 검사 process (2D bottom → 3D bottom --(TFM)→ 2D Top → 3D Top → (optional) Side)
- 표준화된 측량값을 일정하게 유지하기 위해 일정주기로 offset값 calibration (LTSM?)
- Vision Tuning : 채널별 값 조정, iPIS-500의 경우 R채널 값을 설정하면 G, B채널의 값이 자동으로 계산되어 추천값을 알려줌(?)
- 매뉴얼 보고 보완

<향후 보완사항>
- 빈 트레이보다는 sort하는 과정까지 같이 보면서, sorter가 어떻게 동작하는지 파악이 필요함
	- 더미패키지 대여 완료, (SKXXCC56.5X72, PICKER 2개(42X42), 패키지 10tray, 빈트레이 6tray)
- 결과 화면에 good/reject 분류가 어떤식으로 일어나는지 보는게 중요함
	- 총 40 unit ? Good : x개 | Reject : y개
- 셋업팀에서 관리하므로 셋업팀에 요청해야 함 (셋업팀 김도경 대리)
- 아진 보드?