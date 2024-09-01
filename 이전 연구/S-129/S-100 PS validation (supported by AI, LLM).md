input : S-100 PS docs 
output : validation result document

<'issues'>
- 현재 validation이라고 하면 XML 문법체크 정도가 이루어지고 있음
  → 제대로된 validation check가 필요함

<'approach'>
- validation 대상은 무엇인가? feature data(GML)? FC(XML)? PC(XML)?
  1. Feature data를 대상으로 적용한다면 input이 FC가 될 수 있으며 두 문서사이의 sync를 찾을 수 있을 것이다.
  2. FC가 대상이라면?
	- XSD에 대하여 태깅 등 문법에 맞는지 검사
	- 다른 것은 없는가?
  3. PC가 대상이라면?
	- PC가 대상인 경우는 XML끼리 변경하는 것과는 접근법이 다르다. 자체 Rule, 그리고 FC와 마찬가지로 XSD의 문법에 맞는지 비교하는 접근이 될 것이다.
- validation과 verification의 차이
- LLM을 사용한다면 어떤 모델을 사용할 것인가?
- validation의 기준은 있는가?
  Feature data를 대상으로 validation check를 수행한다면 FC는 Feature data를 만들기 위한 구조이기 때문에 validation의 기준문서로 적합하다고 볼 수 있다.

