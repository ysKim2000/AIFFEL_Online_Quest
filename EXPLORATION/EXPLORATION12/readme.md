# AIFFEL Campus Online 7th Code Peer Review Templete

- 코더 : 김윤서
- 리뷰어 : 박준



🔑 **PRT(Peer Review Template)**

- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
    퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 부분의 코드 및 결과물을 근거로 첨부
     
텍스트전 처리를 잘 실행했습니다.
![텍스트처리부분](https://github.com/currybab/first-repository/assets/7679722/8bb3ef24-88a5-42cf-ab51-8760d10a507a)

모델 학습이 진행되면서 train loss와 validation loss가 감소하는 경향을 그래프를 통해 확인했으며, 실제 요약문에 있는 핵심 단어들이 요약 문장 안에 포함되었다.

![lossgraph](https://github.com/currybab/first-repository/assets/7679722/3e8a6333-63e0-47af-a2ed-d98bd62e04c2) 

두 요약 결과를 문법완성도 측면과 핵심단어 포함 측면으로 나누어 비교하고 분석 결과를 표로 정리하여 제시하였다.

![seq2seqresult](https://github.com/currybab/first-repository/assets/7679722/48396d5e-a94e-459f-a3f6-aaf61c7eb8ed)

![summaresult](https://github.com/currybab/first-repository/assets/7679722/6f3a2f3b-a48c-4ce5-aacc-02ddb8e72523)

    
- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 잘 작성되었다고 생각되는 부분을 근거로 첨부합니다.

![](https://github.com/currybab/first-repository/assets/7679722/6e45223f-b347-44e2-8da2-9e736f7fc1b7)

위와 같이 전처리 함수에서 과정 과정에 대해 자세한 설명이 있습니다.


- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인 또는
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 근거로 첨부합니다.
     
![recurrent dropout](https://github.com/currybab/first-repository/assets/7679722/6fd6e9fb-fcd6-42a8-bb2b-0d41fed061b2)

recurrent dropout을 활용하여 성능을 개선하였습니다.

        
- [X]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 상세히 기록되어 있는지 확인
        - 딥러닝 모델의 경우,
        인풋이 들어가 최종적으로 아웃풋이 나오기까지의 전체 흐름을 도식화하여 
        모델 아키텍쳐에 대한 이해를 돕고 있는지 확인

결과 관찰 및 아쉬운점 후 개선점을 작성해 주셨습니다.
![회고](https://github.com/currybab/first-repository/assets/7679722/f774aad9-76e1-48a6-9d4c-5a9c9d7bbcee)


- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 모듈화(함수화) 했는지
        - 잘 작성되었다고 생각되는 부분을 근거로 첨부합니다.


![recurrent dropout](https://github.com/currybab/first-repository/assets/7679722/6fd6e9fb-fcd6-42a8-bb2b-0d41fed061b2)

전체적으로 코드가 간결하게 작성이 되어있습니다. 필요한부분에 모듈화도 되어있고 블록별로 실행하기 좋게 잘 블록화 되어있습니다.
