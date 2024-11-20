- Jira issue 구성 사례 (MED/PRD)
    - Epic : MED Level-2 (project functional requirement)
    - Story : MED Level-3
    - Task : PRD Level-3 (개발팀에 적는 부분)  
        ※ PRD Level-1은 MED Level-2, PRD Level-2는 MED Level-3와 매핑
    - Bug : 테스팅 팀에서 등록
        - Bug 등록은 Story의 하위 이슈로 등록됨, Task와 같은 레벨
    - Test request : 개발팀에서 테스트를 위해 요청할때 사용

- 릴리스 기능
    - 프로젝트의 릴리스 : 버전 구분을 위한 기능으로 테스팅 팀에서는 TR phase의 의미로 사용
    - 세부사항의 릴리스 : 프로젝트의 릴리스와는 다른 의미로 기능플래그를 사용하여 수정사항을 확인
    - 릴리스 기능을 통해 버전을 관리함
        - 버전은 수행할 때마다 릴리스에 계속 쌓임
        - 버그가 발견되는 버전, test version, 현재 테스트하는 버전, 테스터가 입력
        - 버그가 수정되는 버전, 버그를 수정하고 개발자가 입력

- 차수 진행은 Main test - Confirmation test - Regression test로 진행
    - 기대 결과
        - Main test - Bug submit
        - Confirmation test - Bug 상태 변경 : reolved -> reopen or close
        - Regression test : Confirmation test 진행 후 수정된 버전에 대한 테스트? close Bug에 대한 테스트?
- TR은 차수검증(차수테스트)시 매 차수마다 작성
    - TR은 Jira이슈 - confluence 페이지(SQA)에서 프로젝트단위로 관리(이슈링크)
    - TR과 TC는 1세트
    - 1차 테스트 범위
        - TC
        - MED/PRD 기반 TC (작업완료된 task)
        - 1차 테스트 Bug (resolve)
    - 2차 테스트 범위
        - 1차 테스트 Bug (reopen)
        - MED/PRD 기반 TC (작업완료된 task)
        - 2차 테스트 Bug (resolve)
    - …
        

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
        - Test result report는 Jira 기본 기능인 릴리스 기능을 이용하여 연결된 이슈를 파악하고 Confluence페이지로 생성할 수 있음  
            

- TC의 작성
    - TC는 TR과 세트로 관리한다.
    - TC의 작성은 기능리스트 도출 → 예상 TC 도출(제목) → 도출 결과 리뷰 → 상세화 과정을 거친다.
        - iPIS-500에서 setup의 경우 모든 항목을 TC화 한다.
        - 향후 TC리뷰 과정에 관련 TC를 그룹화 하거나 TC가 삭제될 수 있다.
        - Bottom2D, Bottom3D, Top2D, Top3D, Side vision 등 Vision 모듈은 Job을 불러올때 데이터가 잘 불러와지는지, Vision PC와 데이터를 잘 주고받는지, Vision PC에서 변경했을때 변경사항이 Host에 잘 변경되는지, Host에서 변경했을때 Vision에 잘 반영되는지, 변경사항 반영 후 Lot 수행과 Inspection 결과가 제대로 나오는지를 파악한다. (향후 TC항목 추가)
        - Handler teaching이나 Vision Tune과 같은 초기 세팅 후 operating에서 변하지 않는 옵션들은 변경되면 operation에 큰 영향을 줄 수 있기에 변경정도를 파악하는 TC를 설계한다.
    - 리뷰 과정에서 범위와 TC의 상세도를 결정한다.

- Testing process
    - Test plan
    - Test
    - Test result

- TMS : document list, ※문서는 기본적으로 Confluence page에 작성하되 부득이한 경우 sharepoint를 이용한다. (문서 양식은 를 참고한다.)
    - STP : 테스팅 계획
        - Testing environment : 장비 / 버전 / 검사대상(pkg+tray) / Line 상황 (외부통신, 라인구성 및 동작 등)
        - Test item → Test range
            - Functional test : **TC based Test, Confirmation Test**, Scenario based Test
            - non-Functional test : Long-run Test
    - TC : sharepoint link
    - (Pre-STR) : pre-test (alpha test, 사전검증)의 결과
    - STR : Bigbang test(본검증) 의 결과
    - SSTR : Bigbang test 중 각 차수(step)의 결과 (1 page 내 간단히 작성)