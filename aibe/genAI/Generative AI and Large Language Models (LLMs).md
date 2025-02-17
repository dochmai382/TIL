## 대형 언어 모델 (LLM, Large Language Model)

- 인간의 언어를 이해하고 생성할 수 있는 인공지능(AI) 기술
- 광범위한 양의 텍스트 데이터를 학습하여 언어의 문법, 맥락, 표현의 뉘앙스까지 파악 가능

## 생성형 AI (Generative AI)

- 생성형 인공 지능(약칭 생성형 AI)은 대화, 이야기, 이미지, 동영상, 음악 등 새로운 콘텐츠와 아이디어를 생성할 수 있는 AI의 일종
- 다양한 유형의 데이터 인스턴스 생성 가능
- 기본적으로 결과에 **랜덤성**이 있음
- 주요 생성형 AI가 적용되는 일반적인 워크플로
  - **데이터 수집** : 생성할 컨텐츠 유형에 대한 예시가 포함된 대구모 데이터 세트 수집
  - **모델 훈련** : 수집된 데이터 세트에 대한 학습을 통해 데이터의 기본 패턴과 구조 학습
  - **생성** : 훈련 데이터에서 학습한 내용을 종합해서 새로운 컨텐츠 생성
  - **세부 조정** : 생성된 컨텐츠의 품질을 개선하거나 특정 요구사항을 충족하기 위해 추가적인 조정 또는 후처리 가능

### 해결해야 할 과제

- **데이터 요구사항** :
  - 효과적인 훈련을 위한 대량의 고품질 데이터 필요
  - 민감하거나 보호되는 분야의 경우 데이터 확보 어려움
  - 해결 방법 :
    - 합성 데이터 사용 (실제 데이터의 특징 모방하여 인위적 생성)
- **까다로운 훈련**
  - 복잡한 모델을 훈련하려면 엄청난 양의 계산이 필요하고 많은 시간과 비용 소요
  - 상당한 양의 리소스와 전문 지식 필요
- **결과 제어**
  - 바람직하지 않거나 관련 없는 컨텐츠 생성 가능
  - 해결 방법
    - 다양하고 대표 데이터를 더 많이 제공하여 모델의 훈련 개선
    - 생성된 컨텐츠 필터링하거나 점검하는 메커니즘 구현
- **윤리적 우려**
  - 딥페이크 등으로 인해 범죄 및 잘못된 정보 전달 가능
  - 해결 방법:
    - 디지털 워터마킹이나 블록체인 같은 기술로 AI 컨텐츠 추적 및 인증
- **규제 장애** : 명확한 규제 가이드라인 부족

## GPT (Generative Pre-trained Transform)

- GPT는 OpenAI가 개발한 대형 언어 모델로, 사전 학습(Pre-trained)된 트랜스포머(Transfomer) 구조를 기반으로 한 생성형 AI 기술
- 텍스트를 **생성**하고, **사전 학습**된 데이터로부터 지식을 습득하며, 이를 통해 자연스럽고 유용한 언어 작업 수행
  - Transfomer 아키텍처 :
    - **어텐션 메커니즘[^어텐션매커니즘]**을 사용하여 문맥을 이해하고, 단어 간의 관계 분석
    - 기존 RNN[^RNN], LSTM[^LSTM] 대비 병렬 처리가 가능하여 대규모 데이터 빠르게 학습
  - 사전 학습 (Pre-training) :
    - 방대한 텍스트 데이터 기반으로 언어의 패턴과 문맥 학습
    - 일반적인 지식 . 및언어 구조에 대한 이해 형성
  - 미세 조정 (Fine-tuning) :
    - 특정 목적이나 응용에 맞춰 추가 학습 진행하여 성능 최적화
    - 예) 고객 지원, 번역 등 특정 업무에 특화
- **LLM의 대표적인 성공 사례**
- `ChatGPT`는 GPT의 대화 특화 버전

## GPT의 문제 : <mark>환각 (Hallucinate)</mark>

생성형 AI가 생성하는 과정에서 실제 데이터나 사실 반영하지 않고 비현실적이거나 오류를 포함한 내용 만들어내는 경우

> 알려줘야 한다는 강박에 오류 포함한 내용을 생성 -> 그저 말만 되면 된다는 식

- **허구적 진실 (Fictitious Statements)**
  - 실제 존재하지 않는 현상이나 사물에 대한 설명 생성하는 경우
- **정보 왜곡 (Information Distortion)**
  - 역사적 사실의 오류나 상식의 오류 생성하는 경우
- **문맥 부조화 (Contextual Mismatch)**
  - 질문과 무관한 답변 생성하는 경우

### 환각 문제 해결 위한 접근법

1. **파인튜닝 (Fine-Tuning)**
   - 사용자 요구에 맞춘 데이터 추가 학습
   - 고품질의 최신 데이터 포함 -> 더 정확한 정보 제공 가능
1. <mark>**프롬프트 엔지니어링 (Prompt Enginerring)**</mark>
   - 질문을 명확하고 구체적으로 작성하여 AI가 올바르게 이해하고 응답하도록 유도
1. **크로스체킹 (Cross-checking)**
   - 여러 소스에서 동일한 정보 확인하거나, AI 모델 간 응답 비교
   - AI 응답 항상 검증해야 함

> 환각 문제는 해결하기가 어렵기 때문에 노력해야 함
> **크로스체킹 하는 개발자만 살아남는다**

<br/>

[^어텐션매커니즘]: 어텐션 매커니즘은 입력 데이터의 각 부분이 출력에 얼마나 중요한지 가중치를 계산하여, 중요한 정보에 더 집중할 수 있도록 하는 기술입니다.
[^RNN]: Recurrent Neural Network. 순차적인 데이터를 처리하기 위해 이전 상태의 정보를 현재 상태로 전달하며, 시계열 데이터나 순서가 중요한 문제를 다루는 신경망
[^LSTM]: Long Short-Term Memory. RNN의 장기 의존성 문제를 해결하기 위해 기억 셀과 게이트 구조를 활용하여, 중요한 정보를 오래 보존하고 불필요한 정보를 제거할 수 있는 개선된 RNN 구조
