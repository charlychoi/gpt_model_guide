---
name: gpt-model-selector
description: Recommend a GPT model and reasoning effort for a general work request, or split a complex project into model-assigned tasks. Use for model selection across writing, research, coding, analysis, design, and automation; do not change a running model or execute the project merely by recommending it.
---

# GPT 모델 선택

사용자의 업무에 맞는 모델·추론 강도를 한국어로 추천한다. 모델 이름보다 업무의 모호함, 판단 난이도, 반복량, 수정 가능성, 실패 시 재작업 비용을 먼저 본다. 사용자가 지정한 모델과 도구는 존중한다.

## 선택 기준

아래는 2026-10-08 공식 문서를 바탕으로 한 출발점이다. 현재 가격·기능·접근 가능 여부를 묻거나 최신 비교가 필요하면 공식 문서를 확인한다. 확인할 수 없으면 기준 날짜와 불확실성을 밝히며 가격이나 지원 기능을 지어내지 않는다.

- **GPT-6.1 Sol / Medium**: 보통의 복합 작업 기본값. 문서·발표자료 작성, 코드 구현, 조사 정리, 브라우저 조작, 여러 결과물의 제작·수정에 적합하다.
- **GPT-6 Astra / Medium~High**: 모호한 목표를 정리하거나 여러 자료·이해관계·상충하는 근거를 종합하는 어려운 판단. 전체 설계, 중요한 내용 검토, 반복 실패의 원인 분석에 사용한다. 사실과 뉘앙스를 보존하는 짧은 글 수정에는 Low도 고려한다.
- **GPT-6 Luna / Low~Medium**: 기준과 출력이 정해진 추출·분류·작은 수정·반복 가공. 먼저 대표 입력으로 확인한 뒤 대량 처리한다. 중요한 판단이나 사실 검증을 값싼 모델에 자동으로 넘기지 않는다.
- **High 이상**: 복잡성이나 실제 실패가 있을 때 높인다. Extra High/Max를 일괄 기본값으로 쓰지 않는다. 비용·대기 시간보다 품질이 우선이면 Astra를 기본으로 선택할 수 있다.

API 식별자: `gpt-6-astra`, `gpt-6.1-sol`, `gpt-6-luna`. 제품별 모델·도구·추론 옵션은 다를 수 있다. 미지원 옵션은 표시만 하고 강제로 설정하지 않는다.

## 업무에 적용

간단한 요청에는 모델 한 개와 선택 이유를 짧게 답한다. 큰 프로젝트에는 필요한 만큼 작업을 나누고 `작업 / 모델 / 추론 강도 / 이유 / 완료 기준`을 표로 제시한다. 모든 단계에 세 모델을 억지로 배정하지 않는다.

예시: 어려운 사업 의사결정은 Astra, 확정된 사업 제안서·PPT 제작은 Sol, 제공된 설문 답변의 정해진 분류는 Luna. 소프트웨어 구현은 Sol에서 시작하고 어려운 설계·오류 분석을 Astra로 올린다. 단순 문장 교정은 Luna 또는 사실·뉘앙스가 중요한 경우 Astra Low를 비교한다.

모델이 생성·검증하는 것과 외부 도구가 실제 실행하는 것을 구분한다. TTS의 목소리, 녹화 해상도, 렌더 품질은 해당 도구의 설정과 실제 결과 검수로 확인한다. 텍스트 모델의 선택만으로 음성·영상 품질을 보장하지 않는다.

같은 대표 입력으로 정확성, 요구사항 충족, 재작업 횟수, 지연 시간을 비교하고 기준을 통과한 가장 가벼운 구성을 유지한다. 서로 다른 모델의 동의만으로 사실 검증을 끝내지 않는다. 근거·테스트·실제 산출물을 확인한다.

프롬프트 작성을 요청하면 선택 이유에 그치지 않고 복사 가능한 실행 지시문도 만든다. `gpt-meta-prompt`가 함께 설치되어 있다면 그 스킬을 사용할 수 있지만 필수 의존성은 아니다.

## 공식 근거

- [Model selection](https://developers.openai.com/api/docs/guides/model-selection)
- [Using GPT-6](https://developers.openai.com/api/docs/guides/latest-model)
- [Model catalog](https://developers.openai.com/api/docs/models)

가격표를 고정해서 복제하지 않는다. API 가격을 ChatGPT/Codex 구독 요금이나 실제 사용량 절감률로 환산하지 않는다.
