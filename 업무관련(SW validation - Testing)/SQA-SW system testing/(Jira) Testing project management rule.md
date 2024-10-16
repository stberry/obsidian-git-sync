- 차수 진행은 Main test - Confirmation test - Regression test로 진행
	- 기대 결과
		- Main test - Bug submit
		- Confirmation test - Bug 상태 변경 : reolved -> reopen or close
		- Regression test : Confirmation test 진행 후 수정된 버전에 대한 테스트?  close Bug에 대한 테스트?
- TR은 차수검증(차수테스트)시 매 차수마다 작성

1. TR 요청시 (개발자)
	- TR 이슈를 생성하고 테스트가 필요한 개발 Task를 연결
	- 이슈 연결방안
		- TR 생성시 관련 Task를 한번에 연결 (Test request -> Task)
		- Task에서 개별적으로 TR과 연결 (Task -> Test request)
2. TR 관리 (테스팅 팀)
	- Submit->Open(Review) : accept/reject 결정, reject시 반려이유 작성
	- Testing : 버그 등록 후 TR과 Task에 연결
		- Task -> Bug : Task를 추적하기 위함
		- TR -> Bug : 최종 종료 단계 이전에 Bug 해결 상황을 한눈에 확인할 수 있음
	- 승인자(default : SE팀/김효승)의 승인 후 TR 종료
		- TR 종료시 Test result report 업로드
		- Test result report는 
		- Jira 기본 기능인 릴리스 기능을 이용하여 연결된 이슈를 파악하고 Confluence페이지로 생성할 수 있음