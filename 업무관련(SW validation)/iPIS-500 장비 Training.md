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
- 9월 7일 이전까지는 낮에 
- ~~뭐 물어볼때 김선임 음료라도 챙기기~~

0827 장비설명 (정리 후 confluence 페이지, 시뮬레이터 설치, 실행은 confluence 매뉴얼 페이지 업데이트)
- 오전 11시 ~, 장소 : A동 공장
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

<개별인터퓨(C/S 양창기 과장 (will be SE팀 on 21st, Oct))>

<전반적인 handler의 동작(motor, tray 이동, tray 위치별 검사)>
- (TBD)

<검사 결과화면 분석(vision software)>
- (TBD)

<요청사항>
- 빈 트레이보다는 sort하는 과정까지 같이 봐야할것같음
- 결과 화면에 good/reject 분류가 어떤식으로 일어나는지 보는게 좋아보임
- 셋업팀에서 관리하므로 셋업팀에 직접요청해야 할 수 있음