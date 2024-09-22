- 그라디언트 손실이나 폭주를 방지하기 위해선 활성화함수가 중요
- 시그모이드와 가중치 초기화 방식(평균이 0, 표편이 1) 조합이 문제를 야기
- 글로럿 초기화
    - 각 층의 연결 가중치를 랜덤으로 초기화
    - kernel_intializer = "he_normal"옵션을 통해 초기화
- 고급 활성화 함수
    - Relu
    - LeakyRelu
    - RRelu
    - PRelu
    - Elu
    - SElu
    - Gelu
    - Swish
    - Mish

    - 예시코드
    ```
    leaky_relu = tf.keras.layers.LeakyReLU(alpha=0.2)  # 기본값 alpha=0.3
    dense = tf.keras.layers.Dense(50, activation=leaky_relu,
                                kernel_initializer="he_normal")
    ```

- 배치정규화
    - tf.keras.layers.BatchNormalization(),를 은닉층 활성화 함수 전이나 후에 추가

- 그래디언트 클리핑
- 사전훈련층 재사용
- 고속옵티마이져
- 학습 스케쥴러