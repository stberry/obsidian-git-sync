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

0827 장비설명 (정리 후 confluence 페이지)
- 오전 11시 ~, 장소 : A동 공장
- 빈 트레이가지고 테스트 (BGA-37.5 X 37.5)
- iPIS-500 GANTRY - 기존 iPIS-500 장비에 GANTRY 장비를 덧붙인 장비로 CART에 패키지 트레이를 담아 일괄검사를 지원
- SW 버전 : Handler - 3.312.00.0230DD (development debug 버전, RD - release debug), Vision - 1.312.999.0120 Release Version
- Lot 단위로 검사 (any tray)
- 검사 단계
	1) interlock 확인
	2) init handler : 모터들의 영점을 잡아주는 역할
	3) setup : 2d top / bottom, 3d bottom enable 확인, (side, 3d top disable)
	4) 여러가지 동작 모드가 있으나 operator 권한에서는 보통 run mode를 많이 사용 (기계 제어를 위해서는 run mode가 일반적)
	5) option parameter
		- [ ] lot split : 이전 lot과 구분짓기 위해 사용 (거의 사용하지 않음)
		- [ ] all tray are loaded
		- [ ] rejects are not sorted : sort 여부에 대한 옵션, 체크시 불량체크 하지 않음
		- [ ] debug log : 상세 로그 기록
	6) 

stand alone 실험 경과 (해결된 것 체크, supported by 김동규 선임, 김철민 선임)
1. [x] interlock 안된상태에서 init handler 하면 경고
       → 경고메시지 확인 후 interlock 확인
2. [x] Tray load (loading elevator, empty elevator)
       → 해당칸에 트레이 배치 (3개씩)
3. [x] z1 motor 빨간불 (세팅매뉴얼?)
       → 어떻게 조치해야 하는가? 대부분의 trouble shooting은 init handler로 가능
4. 

==**거창한거 만들생각 말고 일단 시작부터

