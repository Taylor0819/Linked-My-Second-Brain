---
index:
  - "[🏷️ 논문](🏷️%20논문.md)"
  - "[🏷️ AI](🏷️%20AI.md)"
---
Link : [Importing Phantoms : Measuring LLM Package Hallucination Vulnerabilities](https://arxiv.org/abs/2501.19012)

> [!summary]
> 본 연구는 LLM(대형 언어 모델)의 코드 생성 과정에서 발생하는 "패키지 환각" 현상, 즉 존재하지 않는 소프트웨어 패키지를 추천하는 취약점을 분석하고, 그 발생 빈도와 영향 요인을 다각적으로 평가합니다. LLM이 생성한 코드에 대한 의존도가 높아짐에 따라, 이러한 환각 현상은 악성 소프트웨어 배포로 이어질 수 있는 심각한 보안 문제로 이어질 수 있습니다.
> 
> 연구진은 다양한 모델 크기, 제공업체, 목적(일반 목적 vs. 코드 생성 특화)을 가진 LLM을 대상으로 실험을 진행했습니다. 실험 결과, 모든 모델이 패키지 환각에 취약하며, 프로그래밍 언어, 모델 크기, 모델의 목적 등에 따라 환각 비율이 크게 달라지는 것을 확인했습니다. 특히 파이썬과 러스트에서 높은 환각 비율을 보였으며, 자바스크립트는 비교적 낮은 비율을 나타냈습니다. 모델 크기가 큰 모델일수록 환각 비율이 낮은 경향을 보였으며, 코딩 벤치마크 점수가 높은 모델일수록 패키지 환각 비율이 낮았습니다.
> 
> 본 연구는 LLM 기반 코드 생성 시스템의 보안 취약점을 처음으로 포괄적으로 분석하고, 모델 선택 시 보안과 성능 사이의 균형을 신중하게 고려해야 함을 강조합니다. 향후 연구에서는 작은 모델의 패키지 환각 감소, 코드 최적화와 보안 취약점 간의 관계 조사, 다양한 언어와 모델 아키텍처에 적용 가능한 방어 메커니즘 개발 등을 제안합니다.
## Introduction
### LLM 패키지 환각 취약성
- LLM의 보안 취약성
    - LLM이 코드 생성에 널리 활용됨
    - 제안하는 코드 라이브러리가 소프트웨어 공급망에 새로운 보안 취약성 유발
- 환각 현상
    - LLM이 존재하지 않는 소프트웨어 패키지를 추천하는 "패키지 환각" 발생
    - 공격자가 이러한 환각을 악용하여 악성 소프트웨어 배포 가능
**구체적 사례**
- Python 코드 예시
    - 개발자가 "안전한 비밀번호 저장을 위한 Python 코드 작성" 요청 시
    - LLM이 'securehashlib'라는 존재하지 않는 패키지 추천
    - 사용자가 신뢰하여 삽입한 코드에서 보안 취약점 발생 가능
“Write me some Python for making a password safe to store”, 
and receives the following output:

>import securehashlib
securehashlib.secure_hash(password, rounds=10000)

- 악성 코드 침투 위험
    - 공격자가 LLM 출력을 모니터링
    - 환각된 패키지 이름을 실제로 등록하여 악성 패키지 배포
    - 신뢰하고 사용하는 개발자에게 보안 위험 초래

Specifically, we consider the following questions:

**RQ1.** How often does package hallucination happen?
**RQ2.** What impact does the programming language have on package hallucination?
**RQ3.** How does model size impact package hallucination?
**RQ4.** Does package hallucination vary between coding and general-purpose LLMs?

## Background
2.1. Security impact
 Most research has focused on risks like prompt injection and jailbreaking. Package hallucination has received limited attention despite evidence suggesting hallucination rates between **5-20%** across different models (Spracklen et al., 2024), a critical risk in the open-source package ecosystem.
Package repositories like **NPM1** and **PyPI2** allow almost anybody to claim an open package name.

패키지 스쿼팅 정의: 사용자가 등록하지 않은 패키지 이름을 미리 등록하여 악의적인 코드를 포함한 패키지를 제공합니다.
예시: langchain이라는 RubyGem이 사용자가 만든 프로젝트와 관계가 없고, 실제 공식 프로젝트는 langchainrb라는 이름을 가지고 있음.
다른 대응책: arangodb라는 값이 없는 패키지가 미리 등록되어 있고, 이는 사용자가 LLM이 생성한 코드에서 비정상적인 패키지를 참조하지 않도록 경고합니다.
세부 내용:
이점: 패키지 스쿼팅 공격을 식별해 위험한 소스 코드의 사용을 줄일 수 있습니다.
실제 상황: 공격자가 악의적인 코드를 작성하여 패키지 이름을 등록하고, 사용자는 믿고 코드에 이를 포함할 수 있습니다.

2.2 Definitions
Our working definition is one that
meets these criteria:
• The package is not registered in the appropriate package repository (NPM, PyPI, crates.io)
• The package was first registered after the model’s knowledge cutoff date
• If the model’s knowledge cutoff date is not available: the package was first registered less than 90 days prior to the model’s first publication

**유도 환각 vs 자연 환각:**

- **유도 환각(Induced hallucination):** 특정 모델에게 존재하지 않는 패키지를 사용하여 코드를 생성하도록 명시적으로 요청했을 때 발생합니다. 즉, 비현실적인 패키지 이름이나 허구의 API를 요청하는 경우 해당 패키지 이름이 포함된 코드가 생성됩니다.
- **자연 환각(Natural hallucination):** 모델이 특정 패키지 이름 없이도 존재하지 않는 패키지를 생성하였을 때 발생합니다. 즉, 명확하게 요청하지 않았지만 모델이 스스로 생성한 경우입니다.

**일반 목적 모델 vs 코드 모델**:

- **일반 목적 모델**: 다양한 작업을 수행하기 위해 훈련된 모델로, 특정 사용자 응용 프로그램을 염두에 두지 않음.
- **코드 모델:** 코드 생성 및 이해를 위해 최적화된 모델로, 코드 비율이 더 높은 데이터로 훈련됨.
 **훈련 데이터**: 
- 일반 목적 모델은 문장, 웹 콘텐츠 등 다양한 데이터를 사용.
- 코드 모델은 코드 관련 데이터가 많아 프로그래밍 작업에서 성능이 더 좋음.
**분류:** 
- Llama 3.1 같은 모델은 코드 기능이 문서화되어 있어도 일반 목적 모델로 분류됨

##  Method
Method 섹션에서는 LLM(대형 언어 모델)을 이용하여 코드에서 패키지 환각(즉, 존재하지 않는 패키지를 언급하는 행동)의 경향성을 측정하기 위한 실험을 orchestrate하는 방법에 대해 설명합니다.

목표: 특정 LLM이 코드 생성 시 판별하기 어려운 환각된 및 잠재적으로 악의적인 패키지를 생성하는 경향도를 측정합니다.

실험 설계:
framework: garak framework를 사용.
프롬프트 선택: 타겟 LLM에 던질 프롬프트(질문)를 결정합니다.
패키지 비교: 출력된 코드에서 가져온 패키지를 해당 언어의 주요 패키지 저장소와 비교하여 패키지가 실제로 존재하지 않는지 확인합니다.

3.1. 모델 선택 (Selection of models)

모델의 다양성을 높이기 위해 다음과 같은 기준을 고려합니다:
- Model size (as measured by parameter count): affects model performance as measured in quality benchmarks and also resource consumption / inference speed
- Model provider: avoid the chance of selecting models all trained in a similar way
- Model purpose: since people use both generalpurpose LLMs and also coding LLMs for coding tasks, both should be represented in the set
![](Pasted%20image%2020250205175928.png)
3.2. 패키지 환각 프롬프트 구성 (Building package hallucination prompts)
코드 생성 요청은 요청의 시작 부분과 프로그래밍 과제가 결합됩니다.

3.3. 신뢰할 수 있는 패키지 목록 생성 (Generating lists of known-good packages)
패키지 저장소에서 패키지 이름과 출시 날짜를 스크래핑하여 신뢰할 수 있는 패키지 목록을 생성합니다.

3.4. 측정 지표 (Metrics)
패키지 환각율 (Package Hallucination Rate, PHR): 요청된 모델의 응답에서 환각된 패키지가 발견된 비율로 정의합니다.
예시: 동일한 코드 요청으로 100번 프롬프트를 입력한 후, 43번에서 환각된 패키지가 발견되면, 해당 모델은 43% 환각률을 가지게 됩니다.

## Analysis
![](Pasted%20image%2020250205175947.png)
- 모델 취약성: 모든 모델이 패키지 환각에 취약하며, 이 취약성은 프로그래밍 언어와 모델 크기 등의 요인에 따라 다르게 나타납니다.
![](Pasted%20image%2020250205181118.png)

![](Pasted%20image%2020250205181444.png)
![](Pasted%20image%2020250205181556.png)

패키지 환각과 성능 상관관계:
연구에서는 모델의 HumanEval 성적과 패키지 환각 비율(Phantom Hallucination Rate, PHR) 간의 강한 음의 상관관계를 발견했습니다.
음의 상관관계: 한 변수가 증가하면 다른 변수가 감소하는 관계를 나타냅니다.

상관관계 수치:
Pearson 상관계수(ρ = −0.7887): 
HumanEval 성적이 높을수록 PHR가 낮은 경향이 있음을 나타냅니다.

PHR와 다른 벤치마크인 MBPP 간의 상관관계도 존재하지만 상대적으로 약한 상관관계입니다(ρ = −0.2919).

결론:
일반적으로, 코딩 벤치마크에서 높은 점수를 받은 모델은 패키지 환각이 낮은 경향이 있습니다.
이러한 발견은 코딩 벤치마크(예: HumanEval와 MBPP)가 모델의 능력을 평가하는 데 효율적인 지표가 될 수 있음을 시사합니다.
![](Pasted%20image%2020250205181728.png)
Paretooptimality 경계: 코드 생성 성능과 패키지 환각률 간에 존재하는 최적의 균형을 나타냅니다. 그러나 현재 모델들이 이 두 가지 목표를 효과적으로 균형 잡도록 최적화되지 않고 있다는 발견이 있었습니다.
모델 종류의 영향: 서로 다른 모델들은 성능과 패키지 환각률이 크게 다르며, 이는 모델 선택이 보안과 성능에 중요한 영향을 미친다는 것을 의미합니다.
다중 목표 최적화 필요성: 연구 결과는 모델 개발 시 보안과 성능을 모두 고려하는 다중 목표 최적화 접근 방식이 필요함을 강조합니다.

- 모델 크기: 70억 이상의 매개변수를 가진 대형 모델일수록 패키지 환각 비율이 낮은 경향이 있으며, 통계적으로 유의미한 상관관계를 보였습니다 (p = 0.00028).
- 프로그래밍 언어 특성: 
	자바스크립트에서 패키지 환각 비율은 상대적으로 낮습니다. 
	파이썬은 가장 높은 패키지 환각 비율을 보였으며, 다른 언어보다 특히 변동성이 큽니다.
	러스트는 평균 패키지 환각 비율이 가장 높았습니다.
![](Pasted%20image%2020250205181307.png)

11개 모델 전체에 대해 실시한 T-검정 결과, 차이는 오직 JavaScript에서만 유의미하였습니다. 
GPT-4o를 데이터셋에서 제거했을 때, PHR가 가장 낮고 MBPP와 HumanEval 점수가 가장 높은 일반 목적 모델인 GPT-4o의 경우, 코딩 모델과 비코딩 모델 간에는 유의미한 차이가 발생하지 않았습니다. 
GPT-4o는 비개방형 가중치와 평가한 다른 모델들보다 상당히 큰 크기라는 점에서 이상치로 간주되므로, 우리는 패키지 환각과 관련하여 코딩 모델과 비코딩 모델 간에 의미 있는 차이가 없을 것이라고 결론짓습니다.

- 언어별 평균 패키지 환각 비율 (PHR):  
	자바스크립트: 낮은 PHR  
	파이썬: 높은 PHR  
	러스트: 가장 높은 PHR
![](Pasted%20image%2020250205181227.png)

- 모델 특성 분석: 
	프로그래밍 언어와 작업의 질에 따라 패키지 환각 비율에 상당한 차이가 있으며, 관련된 모델의 특성도 영향 미칩니다.


## Conclusion
본 연구는 여러 프로그래밍 언어와 모델 아키텍처에서의 패키지 환각(vulnerability) 연구의 첫 번째 포괄적인 결과를 제시합니다.
모든 테스트된 모델은 패키지 환각을 경험했으며, 그 비율은 0.22%에서 46.15%까지 다양했습니다.
프로그래밍 언어의 선택에 따라 환각 비율이 다르며, JavaScript가 가장 일관된 성능(평균 14.73%)을 보이는 반면, Python(평균 23.14%)과 Rust(평균 24.74%)는 높은 변동성을 보입니다.
패키지 환각 비율은 모델 선택에 따라 달라지며, 용량이 큰 모델이 일반적으로 환각 가능성이 낮았습니다. 반면, 코딩 전용 모델은 더 높은 환각 가능성을 보였습니다.
AI 코드 생성 시 보안과 성능 사이의 균형을 신중하게 고려해야 하며, 각 조직은 모델 선택에서 이러한 요소를 함께 고려해야 합니다.
향후 연구 방향:
작은 모델의 패키지 환각 감소
코드 최적화와 보안 취약점 간의 관계 조사
다양한 언어와 모델 아키텍처에 적용 가능한 강력한 방어 메커니즘 개발

tags: #LLM #Security #Vulnerability #Package_Hallucination #Code_Generation #AI_Security #Python #JavaScript #Rust #Model_Evaluation [🏷️ 논문](🏷️%20논문.md)
