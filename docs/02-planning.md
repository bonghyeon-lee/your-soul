# 02. Planning: Functional Specification

## 1. 개요 (Introduction)

본 문서는 "Your Soul" 프로젝트의 구체적인 기능 명세와 기술적 구현 계획을 다룹니다.
사용자와 AI의 상호작용 데이터를 분석하여 페르소나를 추출하고, 이를 지속적으로 업데이트하는 시스템을 구축하는 것이 목표입니다.

## 2. 주요 기능 (Key Features)

### 2.1. 실시간 성향 분석 (Real-time Analysis)

* **Data Source**: 사용자의 프롬프트(질문, 요청), 작성한 코드/문서, AI의 응답에 대한 반응.
* **Analysis Metrics**:
  * **Communication**: 어조(Tone), 예의, 명확성, 감정 표현 빈도.
  * **Work Style**: 논리적 구조, 창의성, 디테일, 실행력.
* **Interest**: 주로 다루는 주제, 깊이, 확장성.
* **Blind Spot**: 자주 사용하는 부정적 단어, 논리적 비약, 반복되는 사고 패턴 감지.
* **Soul DNA**: 성향을 추상적인 아트나 그래프(Soul DNA Visualization)로 시각화.

### 2.2. 살아있는 문서화 (Living Documentation)

* `your-soul.md` 파일을 통해 분석 결과를 지속적으로 업데이트합니다.
* **Version Control**: Git 등을 통해 나의 변화 과정을 히스토리로 관리할 수 있습니다.

### 2.3. 목표 성장 관리 (Growth Management)

* **Target Persona**: 사용자가 정의한 이상적인 모습 (예: "따뜻한 리더", "냉철한 분석가").
* **Diff Analysis**: 현재 모습과 목표 모습 간의 일치도(Score)와 차이점 분석.
* **Actionable Feedback**: "좀 더 구체적인 예시를 들어 설명해보세요", "감정적인 표현을 줄이고 논리를 강화해보세요" 등 구체적 제안.

### 2.4. 다중 페르소나 워크스페이스 (Multi-Persona Workspace)

* **Context Scoping**: 상황에 따라 다른 자아를 관리합니다.
* **Examples**:
  * `Work/Manager`: 팀을 이끄는 리더로서의 자아.
  * `Personal/Writer`: 자유로운 창작자로서의 자아.
  * `Study/Student`: 호기심 많은 학습자로서의 자아.

### 2.5. 시장 분석 (Market & Competitive Analysis)

| 프로젝트/서비스 | 주요 특징 | 'Your Soul'의 차별점 |
| :--- | :--- | :--- |
| **Rewind.ai** | 모든 화면/오디오 기록 (Recall 중심) | 단순 기록이 아닌 **'성찰과 피드백'**에 초점. |
| **Mindos.com** | AI 페르소나 생성 (Creation 중심) | 내가 만드는 것이 아니라, **AI가 나를 정의**함. |
| **Personal AI** | 지식 복제 (Digital Twin) | 지식보다는 **성향과 성장**에 집중. |
| **Spotify Wrapped** | 청취 습관 데이터 시각화 | **'나'라는 콘텐츠**를 매일/실시간으로 확인 가능. |

## 3. 데이터 구조 (Data Structure)

### 3.1. Soul File Schema (`your-soul.md`)

```markdown
# My Soul Profile

## Core Identity
*   **Keywords**: #Analytical #Curious #Fast-paced
*   **One-liner**: "빠르지만 깊이 있는 탐구를 즐기는 탐험가"

## Communication Style
*   직설적이고 명확한 요구를 선호함.
*   감정적 교류보다는 정보 교환 중심.

## Work/Creation Style
*   큰 그림을 먼저 그리고 세부 사항을 채워나가는 Top-down 방식.
*   새로운 도구 사용에 주저함이 없음.

## Growth Journey (Diff Log)
*   [2026-02-06] Target: "친절한 사수" (Score: 65/100) -> Action: "피드백 시 칭찬 먼저 하기"
```

## 4. 기술적 아키텍처 (Technical Architecture)

### 4.1. 구현 방식 (Implementation Strategy)

1. **Phase 1: Agent Skill Registration (에이전트 스킬 등록)**
    * AI Agent(Claude, GPT, OpenClaw 등)에게 `analyze_soul` 및 `update_soul` 스킬을 등록합니다.
    * 대화 중 또는 종료 시점에 Agent가 스스로 `your-soul.md` 파일을 읽고 업데이트합니다.

2. **Phase 2: IDE/Browser Plugin Extension**
    * VS Code Extension 또는 Chrome Plugin 개발.
    * API를 통해 백그라운드에서 분석 및 파일 자동 업데이트.

3. **Phase 3: Privacy First Architecture**
    * 모든 분석은 로컬 환경(Local LLM)에서 수행하거나, 개인 식별 정보를 제거(Anonymization) 후 처리합니다.
    * `your-soul.md` 및 분석 데이터는 사용자 로컬 저장소에만 보관됩니다.

### 4.2. Workflow

1. **Input**: User Interaction (Chat, Coding, Writing).
2. **Process**: Background Agent analyzes the interaction against current `your-soul.md` and `target-soul.md`.
3. **Output**: Update `your-soul.md` with new insights and Diff Score.

## 5. 향후 계획 (Roadmap)

* **Visual Soul**: 텍스트 분석 결과를 바탕으로 DALL-E/Midjourney 프롬프트 생성 -> 나만의 아바타 생성.
* **Soul Timeline**: 시간 흐름에 따른 성향 변화를 그래프나 타임라인 UI로 시각화.
