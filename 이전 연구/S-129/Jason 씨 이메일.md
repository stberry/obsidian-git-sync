"1"에 대해서는 말씀해주신대로 rule파일인 areaHatchfillTemplate.xsl파일 또는 areaSimpleColorFillTemplate.xsl을 호출하며 그 룰 파일에서 각각 ANA.xml과 NNA.xml을 호출하게 됩니다.  ANA.xml, NNA.xml에서 색깔 및 투명도의 parameter 값을 조정하면 됩니다.

**_[Jason Rhee]_** **_그럼_** **_곧_** **_ANA.xml_****_과_** **_NNA.xml_****_에서_** **_설정된_** **_투명도가_** **_적용된다는_** **_뜻인지요_****_?  
ANA.xml_****_가_** **_NNA.xml_****_가_** **_“main” XML_** **_파일에서_** **_호출되는_** **_것_** **_이에_**  **_PC_****_내에서_** **_AreaFills_****_와_** **_Rules_** **_사이의_** **_연결부분을_** **_제가_** **_찾거나_** **_이해하지_** **_못하여_** **_재차_** **_두_** **_분께_** **_여쭙는_** **_점_** **_양해_** **_부탁드립니다_****_._**  
  
"2"에 대해서는 표출은 대표님께서 잘 도와주셔서 저도 많은 도움이 되었습니다. 감사합니다.

새롭게 UnderKeelClearancePlan 피처를 표시하는 과정에 몇가지 질문드릴게 있습니다.  
  
현재 UKCM에서 기본적으로 표출하는 NonNavigableArea이나 AlmostNonNavigableArea와 ControlPoint는 좌표 데이터를 받아 영역 및 심볼을 표출하고 있습니다.  
  
이번에 추가된 UnderKeelClearancePlan의 경우 좌표를 이어 하나의 영역으로 구성해야 하는데 이 좌표는 NonNavigableArea이나 AlmostNonNavigableArea와 ControlPoint의 피처데이터와 같이 전송이 되는것인지요?

**_[Jason Rhee]_** **_네_** **_맞습니다_****_._**

  
또한 UnderKeelClearancePlan는 배가 진행함에 따라 새롭게 갱신되어야 할것인데 이에 대한 갱신은 어떻게 진행되어야 하는지요?

**_[Jason Rhee]_** **_갱신은_** **_새로운_** **_dataset_****_의_** **_전송을_** **_통한_** **_cancellation_****_으로_** **_진행하는_** **_것이_** **_현재_** **_PT_****_의_** **_의견입니다_****_._**

**_참고를_** **_위해_** **_지난_** **_S-129 PT_** **_회의_** **_내용을_** **_스크린샷으로_** **_아래와_** **_같이_** **_포함했습니다_****_._**![A close-up of a document
Description automatically generated](https://mail.google.com/mail/u/0?ui=2&ik=89c70d472e&attid=0.0.10&permmsgid=msg-f:1792036885696478805&th=18de980d8c55fe55&view=fimg&fur=ip&sz=s0-l75-ft&attbid=ANGjdJ9KHPBVHH9BZvy5sRQhE7s40qge_mZFnKOaNFzXtEK-0qDcipdsp6jeQK_zx_VyXbpnsMByYwC1sI1bIjmyEB6vek8FhLEwTTeGr28-Jvo2-PMnPVDEYs9mct0&disp=emb)

현재 데이터 구조에는  UnderKeelClearancePlan의 좌표를 위한 속성값이 없는것 같아 질문드립니다.

**_[Jason Rhee]_** **_현재_** **_S-129 PS_****_를_** **_따르면_** **_UnderKeelClearancePlan, UnderKeelClearanceNonNavigableArea,_** **_그리고_** **_UnderKeelClearanceAlmostNonNavigableArea_** **_전부_** **_GM_OrientableSurface_****_에_** **_기반한_** **_surface_****_로_** **_구현하게_** **_됩니다_****_._**

**_조경민_** **_대표님께서_** **_제작해_** **_주신_** **_sample dataset_****_에_** **_UnderKeelClearancePlan feature_** **_가_** **_포함되어_** **_있는데_****_,_** **_참고를_** **_위해_**  **_다시_** **_첨부해드립니다_****_._**

UKC analysis area의 명확한 정의와 필요 Feature data에 대한 정의가 필요해 보입니다.

**_[Jason Rhee]_** **_네_****_,_** **_맞습니다_****_._** **_현재_**  **_PS_****_에서_** **_수정해야_** **_하는_** **_부분_** **_중_** **_하나가_** **_“UnderKeelClearancePlan” feature_****_의_** **_spatialAttribute_****_에_** **_대한_** **_설명을_** **_추가하는_** **_것입니다_****_._**