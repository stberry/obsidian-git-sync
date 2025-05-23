반도체 외관검사 장비 테스트 3D시뮬레이션 시스템 구축 프로젝트 킥오프 미팅

참석자
(VTI)
권정호 본부장, 지태환 차장, 문혜정 과장, 한정우 대리, 흐엉 대리, 도 개발자
베트남 offshore 개발자 online 참가자 4명

(INTEKPLUS)
강민구 전무
이동활 수석, 곽영보 수석, 이효중 수석
한창진 상무, 양창기 책임, 김효승 책임

킥오프 미팅 주요 내용
- 장비가 크고 
- 25' 5/7 ~ 9/22 (4.5 개월)

- 개발도구 VS2022
- Version 관리 : GIT(GitLab-내부배포) (추후 이관)
- 본 프로젝트 한정으로 테스트는 자동화도구를 사용하지 않고 수동으로 진행, 타 프로젝트에서는 테스트 프레임워크를 통해 자동으로 테스트를 수행함
- CI/CD는 어떤것을 사용하는가?
	- Autobuild? CI/CD는 아예 사용하지 않음, Local build 형태
- 설계부분 (화면 설계, 데이터 구조, 기능요구명세)
	- Figma (UI 설계)
	- Json (시뮬레이터 데이터구조)
	- FRS (기능 요구사항 명세서)
	- (추가요청) 소프트웨어 설계 (코드구조, 최소 HLD 레벨 문서 요청)
- 최종 산출물
	- 소스코드
	- 요구사항 문서
	- 설계 문서 : 화면설계, 데이터구조설계, 기능요구사항명세
	- 테스트 문서 : 통합/시스템 테스트 리포트
	- 배포 매뉴얼

개발자 상주기간 5월, 9월 1개월씩 총2개월

시스템 데모 일정
- 6/2 - 모듈 데모
- 6/17
- 7/4
- 7/17

intekplus R&R
PM - 한창진
TL - 곽영보
TM - (기술이관) 이효중, 이동활
(인수테스트) 양창기, 김효승

- [x] 킥오프 미팅 자료 요청

QnA
- 소프트웨어 설계에 대해 코드레벨의 구조도 설계하는가?
	- 설계하지만 문서화는 별도로 하지 않는다.
- 아키텍처 구조도와 코드설명에 대한 설명(주석)을 문서화 하여 제공해줬으면 좋겠다.

- 통합테스트와 시스템 테스트를 구분하여 진행하는가? 유닛 테스트는 어떻게 진행하는가? 유닛 테스트 도구는 어떤걸 사용하는가?
	- 통합 테스트와 시스템 테스트를 구분하여 테스트를 진행한다. 테스트 케이스를 포함하여 테스트 시나리오 문서를 작성한다.
- 이것은 시스템 테스트이며 통합테스트는 결이 다른것 같은데 설명해 줄 수 있는가?
	- 통합 테스트는 모듈간 통합시 유기적인 연결을 테스트 하는 것으로 알고 있다.
	- 도구는 사용하지 않고 기능 개발시 매뉴얼로 테스트를 진행한다.
	- 유니티 테스트 프레임워크가 있는걸로 아는데 사용하지 않는가? 잘 사용하지 않는다.

- 마일스톤 일정에 따라 모두 회의를 진행하는가? 설계일정 마치고 5/30 전체회의를 진행했으면 한다.
	- 일정대로 진행하겠다.

- 설계 완료와 동시에 모듈데모를 진행하는거 같은데 가능한가?
	- 교육과 동시에 개발을 진행하고 있으며 본사에서 귀국하기 전에 그동안의 결과물을 보고하는 형식이다.

- BrSE의 역할은? 
	- Bridge Software Engineer로 IT지식을 기반으로 하여 offshore 개발자와 고객사를 이어주는 역할이다.
- 기술통역이라고 생각하면 된다.
- BA의 역할은?
	- 고객 요구사항을 분석하여 비스니스 요구사항을 도출하며 요구사항문서, 설계문서 등 다양한 문서를 분석한다.

캐드파일을 주면 3D 에셋으로 사용하여 import 시키는데 조그마한 변경이 있을때 우리가 변경하여 사용이 가능한가?
- 확장성에 대한 내용은 개발범위에 포함되어 있다.
- 새로운 컴포넌트를 만드는 것 까지는 향후 얘기이나 에셋으로 만들어진 컴포넌트를 조립하여 새로운 모델의 장비를 만드는 것은 범위 내에 있다.
- 500과 340을 동시에 진행한다. 공통 모듈이 약 10개정도 나온다.
- 새로운 컴포넌트가 필요할 경우 INTEKPLUS가 설계파일을 제공하여 VTI가 새롭게 개발해야 한다.

설계파일 제공시 현재 설계파일이 너무 디테일하여 단순화 시켜야 한다. BS와 논의가 필요하다.
VTI에서 단순화 시켜서 개발에 사용하면 되지 않을까?
모듈에 대한 설명을 제공하여 이해한다음 VTI측에서 단순화작업을 진행하는것은 어떤가? 에셋을 단순화 시키는것?
캐드를 다룰 줄 알아야 하는데 VTI에 가능한 인력이 있는가?
- 확인해보고 답변드리겠다.
캐드 소프트웨어도 가지고 있는가? 크레오?
- 크레오 파일의 Import 경험이 있다.

리스크 & 이슈에서 오차는 어떤것을 의미하는가? 좌표 오차에 대한 얘기인가? 컴포넌트의 모양은 캐드파일에서 추출하기에 다르진 않을것 같다.
- 장비가 동작하는 시간에 차이가 있을 수 있다. 정기적인 데모를 통해 피드백을 받아서 해결해야 한다.
속도에 대한 내용은 어떻게 반영하는가?
- 가속, 감속은 고려하지 않고 등속으로 제공하기로 합의하였다. 장비와 완전하게 동일하진 않다.
그렇게 어렵지 않을것 같은데?
- 1차 개발은 등속으로, 향후 2차 개발에 추가로 들어갈 수 있을것 같다.
- 고려할 만한 내용이다.

온라인 지원 시스템이 별도로 존재하는가?
- 고객지원에 접수하면 대응하겠다.

산출물에 추가로 개발산출물에 대한 사용교육, 코드설명 교육도 제공해줄 수 있는가?
- 기본 프로세스는 매뉴얼제공까지이다. 질의응답을 대응하는 방식으로 제공해왔다.
그동안 잘 해왔다고 한다면 산출물의 퀄리티를 믿고 가겠다. 원칙적으로 운영하지만 탄력적으로 운영하는 방식으로 갔으면 한다.

공유 QnA 시트를 통해 요청사항에 대해 바로바로 대응해줘야 한다.
- QnA문서는 하나로 통합

다른 질문이 있는가?
- 340을 타겟으로 하는데 어느것을 기준으로 하면 되는가?
iPIS-500, iPIS-340HST를 대상으로 해주면 된다.

- 자리 배정에 대한 내용?
개발자 옆에 배정 -> 회의실 B-3에 상주

- 기술적인 질의응답은?
곽영보수석님과 지속적인 협의를 통해 진행하면 된다.

<결정사항>
주간미팅일정
- 목요일 한국시간 오전 11시 (임원회의가 있을시 화요일 오전으로 변경)
- 첫 주간미팅은 다음주 시작(5/22)

INTEKPLUS R&R
PM - 한창진
TL - 곽영보
TM - (기술이관) 이효중, 이동활
(인수테스트) 양창기, 김효승

프로젝트 범위 : 가감속 미반영, 정속 운동을 기본으로 함
- 사용성이나 심미성을 위해 가감속 반영 고려