# GPT Model Guide — 모델 선택과 메타 프롬프팅 스킬

짧은 업무 요청을 **어떤 GPT 모델로 처리할지** 판단하고, **바로 실행할 수 있는 지시문**으로 바꾸는 한국어 스킬 모음입니다. 강의 제작뿐 아니라 문서 작성, 조사·분석, 코딩, 디자인, 고객 업무와 자동화에 사용할 수 있습니다.

## 제공 파일

| 파일 | 용도 |
|---|---|
| [gpt-model-selector](skills/gpt-model-selector/SKILL.md) | 업무별 모델·추론 강도 추천 |
| [gpt-meta-prompt](skills/gpt-meta-prompt/SKILL.md) | 짧은 요청 → 모델 추천 + 복사용 실행 지시문 |
| [일반 채팅창용 프롬프트](prompts/chat-meta-prompt.md) | 스킬 설치 없이 붙여 넣어 사용 |
| [헤르메스 초보자 강의 예시](examples/hermes-beginner-course.md) | 실제 요청에 적용한 지시문 예시 |
| [일반 업무 예시](examples/general-cases.md) | 단순 작업·복합 작업의 선택 차이 |

## 모델을 고르는 기본 원칙

| 상황 | 출발점 |
|---|---|
| 모호한 목표, 깊은 판단, 중요한 내용 검토 | GPT-6 Astra / Medium~High |
| 보통의 복합 제작·코딩·조사 정리·자동화 | GPT-6.1 Sol / Medium |
| 정해진 추출·분류·반복 가공 | GPT-6 Luna / Low~Medium |

이는 공식 문서를 일반 업무에 적용한 운영 권장안입니다. 가장 어려운 문제에는 Astra를 쓰고, 품질을 충족하는 범위에서 Sol·Luna를 비교합니다. Astra가 항상 긴 추론을 필요로 하는 것은 아닙니다. 짧은 문장의 사실·뉘앙스를 보존하는 수정에는 Astra Low도 선택할 수 있습니다.

GPT는 작업을 설계·작성·운영합니다. 음성은 TTS, 화면 녹화는 녹화 도구, 영상 합성은 편집 도구가 실제 처리합니다. 모델을 바꿨다는 이유만으로 음성 잡음이나 화면 오류가 해결되었다고 판단하지 않습니다.

## 설치와 사용

저장소를 가져옵니다.

```bash
git clone https://github.com/charlychoi/gpt_model_guide.git
cd gpt_model_guide
```

### Codex

두 스킬 폴더를 개인 스킬 경로에 복사합니다. 같은 이름의 기존 스킬이 있으면 내용을 확인하고 합치세요.

```bash
mkdir -p "$HOME/.codex/skills"
cp -R skills/gpt-model-selector "$HOME/.codex/skills/"
cp -R skills/gpt-meta-prompt "$HOME/.codex/skills/"
```

새 세션에서 사용합니다.

```text
$gpt-model-selector 고객 설문 2천 건의 분류와 개선 보고서 작성에 어떤 모델을 쓸지 추천해줘.
$gpt-meta-prompt AI agent 헤르메스 관련해서 초보자 대상 강의 교안 원고와 실습 시연 영상을 만들 실행 지시문을 만들어줘.
```

### Claude Code

동일한 SKILL.md 기반 폴더를 개인 스킬 경로 `~/.claude/skills/` 또는 해당 프로젝트의 `.claude/skills/`에 복사합니다. 설치한 버전의 스킬 지원 여부를 확인하세요. 아래 호출은 GPT로 실행하라는 추천 지시문을 **Claude가 작성**하는 것이며, Claude의 내부 모델을 GPT로 바꾸는 기능이 아닙니다.

```text
/gpt-meta-prompt 매달 고객 문의를 분석하고 개선 보고서를 만들 실행 지시문을 작성해줘.
```

### 일반 ChatGPT·Claude·Gemini 질문창

[일반 채팅창용 프롬프트](prompts/chat-meta-prompt.md)를 열어 내용을 복사하고 `[내 요청]`에 자신의 업무를 적어 전송하세요. 그 답변으로 받은 실행 지시문을 추천 모델의 새 대화에 붙여 넣습니다. 단순 작업은 같은 대화에서 이어서 실행할 수도 있습니다.

GitHub 링크만 입력한다고 스킬이 자동 설치되지는 않습니다. 서비스가 파일 읽기나 프로젝트 지침을 지원하면 스킬 파일을 제공할 수 있습니다. 지원하지 않으면 통합 프롬프트를 직접 붙여 넣으세요. 자동 모델 전환·병렬 실행을 제공하는 코드가 아니라 모델 선택 및 지시문 작성용 스킬입니다.

## 검수와 운영

확정 사실·사용자 조건을 유지하고, 미정 사항은 가정으로 표시합니다. 복잡한 프로젝트만 필요한 단계로 나누며 간단한 요청에는 짧은 지시문 하나를 제공합니다. 최신 가격·도구 지원은 공식 문서에서 확인하고 API 가격을 구독 사용량과 동일하게 해석하지 않습니다.

모델 비교는 같은 대표 입력으로 정확성·요구사항 충족·재작업·시간을 측정합니다. 서로 다른 모델의 동의만으로 사실 검증을 끝내지 않습니다.

기준일: **2026-10-08**.
- [공식 Model selection](https://developers.openai.com/api/docs/guides/model-selection)
- [공식 GPT-6 guide](https://developers.openai.com/api/docs/guides/latest-model)
- [공식 모델 목록](https://developers.openai.com/api/docs/models)

사용자 제공 GPT-6 AX 컨설팅 가이드의 역할 분담을 참고했으며, 가격표를 고정해서 복제하지 않았습니다.
