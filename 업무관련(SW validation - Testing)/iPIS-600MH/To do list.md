> [!CAUTION]
> Daily check

STR
- STR documentation
	- [x] Copy STR from iPIS-500
	- [x] Data modification
	- [ ] Data update
- Dashboard
	- 대시보드 구성 - 다이나믹 대시보드
		- 컨트롤러 - 프로젝트 선택
		- 페이즈, 차수별 전체 결함수 그래프
		- 
~~TC 설계 및 verification
- ~~TC 만들면서 test 및 mal function시 버그등록

600MH test plan
- 이미 세팅된 값을 건드리지 않는 선에서 모든 기능을 세세히 검증해야함
- Full Run (lot)
	- [ ] Probe 비활성화 (random 조합) 후 Run
	- [ ] Magazine 1, Magazine 2, Both
		- [ ] Magazine에 Boat를 랜덤하게 집어넣고 검사
		- [ ] 패키지를 중간중간 비워놓고 검사
		- [ ] 
	- [ ] CS에서 셋업한 여러 레시피를 바탕으로 항목을 변경해가며 테스트
- [ ] Pad change
	- [ ] 패드를 이리저리 빼보는 조합
		- Front의 1번 패드 제외
		- Front의 2번 패드 제외
		- Rear의 1번 패드 제외
		- Rear의 2번 패드 제외
		- Front의 1, 2번 패드 제외
		- Rear의 1, 2번 패드 제외
		- 3번 패드를 섞음
	- [ ] 1번 패드가 장착된 상태에서 2번 패드를 쓰는 레시피를 불러오고 Lot을 실행했을때 
	- [ ] Vision 이미지를 제대로 획득하는지 촬영한 이미지가 제대로 검사되는지 확인
	- [ ] 