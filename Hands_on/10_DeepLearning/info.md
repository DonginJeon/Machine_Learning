- 기본 모델 설계
    ```
    tf.random.set_seed(42)
    model = tf.keras.Sequential()
    model.add(tf.keras.layers.Input(shape=(28,28)))
    model.add(tf.keras.layers.Flatten()) # 1D 배열로 변환
    model.add(tf.keras.layers.Dense(300, activation="relu"))
    model.add(tf.keras.layers.Dense(100, activation="relu"))
    model.add(tf.keras.layers.Dense(10, activation="softmax"))
    ```

- 모델 컴파일
    ```
    model.compile(loss = "sparse_categorical_crossentropy",
                optimizer = "sgd",
                metrics = ["accuracy"])
    ```

    - 클래스가 배타적이면 ```sparse_categorical_crossentropy```
    - 클래스 별 타깃 확률을 가지면 ```categorical_crossentropy```
    - 이진분류나 다중 레이블 이진 분류이면 softmax대신 sigmoid를 쓰고 ```binary_crossentropy```

- 텐서보드를 통한 시각화


