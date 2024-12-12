- Vision Inspection item
        - 조합이 많기에 기본 항목 위주로 작성하고 향후 Scenario 테스트에서 recipe를 작성

- MED#6 Test planning
	- iPIS-500 목표 test
		- [ ] Static test
		- [ ] Confirmation test
		- [ ] SW System test
		- [ ] Scenario test (CS, operator)
	- 현장 결함 파악 - 결함 메커니즘 파악 목적 : FARM 작성([개발자 이메일 분석 (iPIS-500I)](https://do-intekplus.atlassian.net/wiki/spaces/TMS/pages/601686018))
	    - TC 장비 verification test
	    - Testing 중 결함 Jira issue로 등록 ([Training Fault | Jira issue list](https://do-intekplus.atlassian.net/jira/software/c/projects/TFP/list))
	    - 안되는것을 모두 기록하며 해결 및 조치사항은 하단의 댓글에 상세히 기록
            
    - Test environment
        
        - 테스트 버전 기록 (Host / Vision)
            
        - 테스트 시료 확보 (레시피 포함)
            
            - SKXXCC 패키지 4구 3트레이, 12ea, SKXXCC_56X76.job 
                
            - 74SPR-XCC package 패키지 5구 81트레이, 405ea, 74SPR-XCC-1007-77.5X56.5.job
                
            - KBLG 쿠폰 3X4 12트레이+1개, KBLG_31X58.5.job (with coupon handling option)
                
            - Picker필요 - Normal, Vortex
                
    - User Requirement Analysis : MED#6 → PRD 완성 Intel에 전달 - 지속적 follow up
        
        - PRD 분석 - 개발자 세미나 (Handler/Vision)
            
            - PRD 구성, 작성 이유, 문제 파악, 개선 전반적인 내용
                
            - Confluence 페이지([https://do-intekplus.atlassian.net/wiki/x/FQASIg](https://do-intekplus.atlassian.net/wiki/x/FQASIg))를 기준으로 설명 <- 최신 논의 내용 반영
                
        - PRD 업데이트 - 개발자 세미나 진행(Handler/Vision)
            
            - Update 내용 구체적 질문
                
            - PRD기반 Confirmation TC 업데이트 진행