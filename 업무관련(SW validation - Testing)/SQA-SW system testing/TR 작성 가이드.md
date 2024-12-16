
1. TR, Test Request 는 테스트 요청서로써 개발팀에서 SQA 팀으로 테스트를 의뢰할때 사용합니다.
2. TR은 Jira issue로 등록합니다.
	1. Jira issue 생성 (이슈 만들기 -> 이슈 유형 : Test Request)
	2. 입력 필드 및 값
		- 요약 : (모델명) (프로젝트명) (차수) SW검증 의뢰
		- Model : 모델명 입력 (ex. iPIS-500I)
		- 수정버전 : 버전 입력 (ex. H3.312.00.0210, V1.313.800.0220)
		- Step : 차수 입력
		- Due Date : 테스트종료일 입력
		- Description(설명) : 개발 완료된 아이템 목록 (3에서 설명)
3. 해당 TR 차수에 변경된 항목을 등록합니다. 매크로-Jira 이슈 기능을 이용하여 이슈 목록을 필터링하여 삽입합니다.
![[Jira issue list (filter).png]]
4. Smart 커밋( https://do-intekplus.atlassian.net/wiki/x/BoA0I ) 을 사용하여 빌드를 진행합니다. 이때 TR 이슈키를 삽입하여 빌드 후 버전이 TR 이슈에 댓글로 자동 삽입됩니다.
