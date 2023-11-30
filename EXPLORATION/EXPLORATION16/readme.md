# AIFFEL Campus Online 7th Code Peer Review Templete

- 코더 : 김윤서
- 리뷰어 : 강다은



🔑 **PRT(Peer Review Template)**

- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
    퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 부분의 코드 및 결과물을 근거로 첨부
          
        <br/>
        
        > 프로젝트에서 요구사항에 따라 챗봇을 구현하고 직접 대사를 입력하여 성능을 확인하였습니다
        
        <img width="690" alt="image" src="https://github.com/DiANA-KANG/AIFFEL_-YK/assets/149550222/26122a5d-6007-4177-8ec1-9f1c3a456cb2">

        <br/>

    
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 잘 작성되었다고 생각되는 부분을 근거로 첨부합니다.

        <br/>

        > 꼼꼼한 주석을 통해 코드 수행 내용과 흐름을 직관적으로 파악할 수 있었습니다

        ```
        #예측(inference)으로 챗봇 테스트하기
        def decoder_inference(sentence):
            sentence = preprocess_sentence(sentence)
        
            # 입력된 문장을 정수 인코딩 후, 시작 토큰과 종료 토큰을 앞뒤로 추가.
            # ex) Where have you been? → [[8331   86   30    5 1059    7 8332]]
            sentence = tf.expand_dims(
                START_TOKEN + tokenizer.encode(sentence) + END_TOKEN, axis=0)
        
            # 디코더의 현재까지의 예측한 출력 시퀀스가 지속적으로 저장되는 변수.
            # 처음에는 예측한 내용이 없음으로 시작 토큰만 별도 저장. ex) 8331
            output_sequence = tf.expand_dims(START_TOKEN, 0)
        
            # 디코더의 인퍼런스 단계
            for i in range(MAX_LENGTH):
                # 디코더는 최대 MAX_LENGTH의 길이만큼 다음 단어 예측을 반복합니다.
                predictions = model(inputs=[sentence, output_sequence], training=False)
                predictions = predictions[:, -1:, :]
        
                # 현재 예측한 단어의 정수
                predicted_id = tf.cast(tf.argmax(predictions, axis=-1), tf.int32)
        
                # 만약 현재 예측한 단어가 종료 토큰이라면 for문을 종료
                if tf.equal(predicted_id, END_TOKEN[0]):
                    break
        
                # 예측한 단어들은 지속적으로 output_sequence에 추가됩니다.
                # 이 output_sequence는 다시 디코더의 입력이 됩니다.
                output_sequence = tf.concat([output_sequence, predicted_id], axis=-1)
        
            return tf.squeeze(output_sequence, axis=0)
        ```
        ```
        #임의의 입력 문장에 대해서 decoder_inference() 함수를 호출하여 챗봇의 대답을 얻는 sentence_generation() 함수를 만듭니다.
        def sentence_generation(sentence):
            # 입력 문장에 대해서 디코더를 동작 시켜 예측된 정수 시퀀스를 리턴받습니다.
            prediction = decoder_inference(sentence)
        
            # 정수 시퀀스를 다시 텍스트 시퀀스로 변환합니다.
            predicted_sentence = tokenizer.decode(
                [i for i in prediction if i < tokenizer.vocab_size])
        
            print('입력 : {}'.format(sentence))
            print('출력 : {}'.format(predicted_sentence))
        
            return predicted_sentence
        ```

        <br/>

- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인 또는
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 근거로 첨부합니다.
     
          <br/>

          > custom learning rate 의 동작을 실험하고 프로젝트에 적용하여 최적의 학습 성능을 도모하였습니다
          
          <img width="405" alt="image" src="https://github.com/DiANA-KANG/AIFFEL_-YK/assets/149550222/56162ec9-3fb8-477f-b766-970b93065087">
          
          > 동일한 주제에 관한 반복적인 실험을 수행하습니다 (실험 결과는 썩 좋지 않았으니 의의가 있는 시도였습니다)
          <img width="619" alt="image" src="https://github.com/DiANA-KANG/AIFFEL_-YK/assets/149550222/6c56c430-eae3-4b5d-af4d-c800d268dba4">

          <br/>
        
- [x]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 상세히 기록되어 있는지 확인
        - 딥러닝 모델의 경우,
        인풋이 들어가 최종적으로 아웃풋이 나오기까지의 전체 흐름을 도식화하여 
        모델 아키텍쳐에 대한 이해를 돕고 있는지 확인

        <br/>
        
        > 회고록을 통해 프로젝트 수행 내용을 요약하고 실험 결과를 간략히 분석하였습니다
        
        ```
        노드에 따라 프로젝트를 수행하니 수월하게 진행할 수 있었다. 노드 실습과 달리 프로젝트에서 영어와 한국어의 전처리 차이만 조금 수정하여 프로그래밍했다. 챗봇 테스트 질문으로 여행, 여행지에 관련되어 물어보았는데 모두 똑같은 답변이 나와 아쉬웠다. 그리고, 입력되는 문장에 간소할 경우, 이상한 답변을 주는 경우도 있었다.
        ```
        <br/>

- [x]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 모듈화(함수화) 했는지
        - 잘 작성되었다고 생각되는 부분을 근거로 첨부합니다.

        <br/>
     
        > PEP8 을 준수하여 적절한 함수명, 클래스명, 변수명을 선언하였습니다. 또한 직관적인 단어의 조합으로 해당 함수/클래스/변수의 목적을 알기 쉽게 코드를 작성하였습니다
        
        ```
        class MultiHeadAttention(tf.keras.layers.Layer):

        def __init__(self, d_model, num_heads, name="multi_head_attention"):
            super(MultiHeadAttention, self).__init__(name=name)
            self.num_heads = num_heads
            self.d_model = d_model
    
            assert d_model % self.num_heads == 0
    
            self.depth = d_model // self.num_heads
    
            self.query_dense = tf.keras.layers.Dense(units=d_model)
            self.key_dense = tf.keras.layers.Dense(units=d_model)
            self.value_dense = tf.keras.layers.Dense(units=d_model)
    
            self.dense = tf.keras.layers.Dense(units=d_model)
    
        def split_heads(self, inputs, batch_size):
            inputs = tf.reshape(
                inputs, shape=(batch_size, -1, self.num_heads, self.depth))
            return tf.transpose(inputs, perm=[0, 2, 1, 3])
    
        def call(self, inputs):
            query, key, value, mask = inputs['query'], inputs['key'], inputs[
                'value'], inputs['mask']
            batch_size = tf.shape(query)[0]
    
            # Q, K, V에 각각 Dense를 적용합니다
            query = self.query_dense(query)
            key = self.key_dense(key)
            value = self.value_dense(value)
    
            # 병렬 연산을 위한 머리를 여러 개 만듭니다
            query = self.split_heads(query, batch_size)
            key = self.split_heads(key, batch_size)
            value = self.split_heads(value, batch_size)
    
            # 스케일드 닷 프로덕트 어텐션 함수
            scaled_attention = scaled_dot_product_attention(query, key, value, mask)
    
            scaled_attention = tf.transpose(scaled_attention, perm=[0, 2, 1, 3])
    
            # 어텐션 연산 후에 각 결과를 다시 연결(concatenate)합니다
            concat_attention = tf.reshape(scaled_attention,
                                          (batch_size, -1, self.d_model))
    
            # 최종 결과에도 Dense를 한 번 더 적용합니다
            outputs = self.dense(concat_attention)
    
            return outputs
        
        ```
        <br/>

<br/>

🍂🍄 **친절하고 온화하신 윤서님께** 🦔🐾  
단 시간에 이렇게까지 코드를 정리하시고 실험평가까지 완벽하게 마무리 지으시다니 놀랍습니다 🫢  
흔쾌히 좋은 코드 리뷰할 기회를 주셔서 감사합니다 ✨  
또 유사한 주제에 대해서 문장을 다르게 하여 실험을 시도해보신 것도 재미있게 잘 보았습니다 ㅎㅎ  
실험을 보니 여행에 관심이 있으신 것 같은데, 어디가 되었든 재미있고 마음을 채울 수 있는 귀한 시간 되시기 바랍니다 😍🍜
