
1. TR, Test Request 는 테스트 요청서로써 개발팀에서 SQA 팀으로 테스트를 의뢰할때 사용합니다.
2. TR은 Jira issue로 등록합니다.
	2.1 Jira issue 생성 (이슈 만들기 -> 이슈 유형 : Test Request)
	2.2 입력 필드 및 값
		- 요약 : (모델명) (프로젝트명) (차수) SW검증 의뢰
		- Model : 모델명 입력 (ex. iPIS-500I)
		- 수정버전 : 버전 입력 (ex. H3.312.00.0210, V1.313.800.0220)
		- Step : 차수 입력
		- Due Date : 테스트종료일 입력
		- Description
			1) Version URL : Amazon S3 링크 삽입 
			2) Change Request list : 개발 완료된 아이템 목록 
			3) Other CRs (Refactoring, Static Test) 
3. Version URL은 CI/CD 파이프라인을 이용하여 빌드 하신 후 S3 링크를 TR에 삽입합니다.- 
	3.1 S3 링크 예시 ( https://intekplus-ipis-500i.s3.ap-northeast-2.amazonaws.com/staging/vision/iPIS-500I-Vision-20241216_182558.zip )

- Amazon S3 (1)![[Pasted image 20241216182152.png]]
- Amazon S3 (2)![[Pasted image 20241216182212.png]]

- 향후 Smart 커밋( https://do-intekplus.atlassian.net/wiki/x/BoA0I ) 을 사용하여 빌드를 진행하면 TR 이슈키를 삽입하여 빌드 후 버전이 TR 이슈에 댓글로 자동 삽입됩니다.

4. Change Request List : Change Requests, CR은 테스트 요청시 변경된 사항을 말합니다.
	4.1 해당 테스트 차수에 검증이 필요한 항목을 해결된 스토리(Resolved) 기준으로 등록합니다. 
- Jira - Story Workflow
  ![[Pasted image 20241217085932.png]]

	4.2 매크로-Jira 이슈 기능을 이용하여 이슈 목록을 필터링하여 삽입합니다.
- Jira Issue List : filter->MED#6프로젝트 / 스토리 / 완료![[Jira issue list (filter).png]]

5. Other CRs
	5.1 Refactoring : 소스코드에서 리팩토링된 부분이 있다면 숫자로 기입합니다.
	5.2 Static Test : Static Test 결과 중 수정된 부분이 있다면 해결된 이슈 목록을 추가합니다.
	- ![[Pasted image 20241217093127.png]]



