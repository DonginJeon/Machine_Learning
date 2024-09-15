# 머신러닝 기초

## 데이터 호출

- ### 샘플링
  - 무조건 split을 하는게 아닌 계층적 샘플링이 필요할 수 있음. 샘플 내에서 비율이 다르면 그 비율을 유지하면서 뽑기
  - 계층적 샘플링 : train_test_split(stratify 옵션을 이용하면 가능)

## 탐색과 시각화

- ### 시각화
- ### 탐색
  - 상관계수 : 피어슨으로 보고 시각화(scatter_matrix)도 시켜보자
  - 위도 경도 정보가 있으면 실제 지도에도 그려보자(02_end)

## 전처리

- ### 대체

  - 수치형
    - 해당 구역제거
    - 전체 특성 제거
    - 대체(평균, 중간값)
      - sklearn.impute > SimpleImputer로도 가능
  - 범주형
    - 원핫인코딩 : 0,1로 구분

- ### 스케일링
  > 회귀에서 스케일이 다르면 경사하강법을 적용하기 어렵고 (시간이 오래 걸려서)


  - minmax
  - standard
  - 로그
  - 가우스 랭크변환
  - 스케일을 하고 inverse_transform 으로 원래 값으로 돌린다

- ### 파이프라인

  - 전처리를 파이프 라인을 통하여 동시에 처리하고 한번에 모델이 넣는다
  - simpleimputer : 대체할때 사용.fillna() 도 있지만 데이터셋이 많은 경우 사용하면 좋다

- ### 모델설계

  - 돌리고 성능평가

    - gridsearch나 랜덤search로 최적의 파라미터 결정
    - param_grid에 하이퍼파라미터를 넣고(list안에 적당한 범위의 수를 넣음. 이것에 대한 학습이 필요)

      ```
      grid_search = GridSearchCV(knn_clf, param_grid, cv=5)
      grid_search.fit(X_train[:10_000], y_train[:10_000])
      ```

      위의 과정을 거쳐 파라미터를 찾는다.

      > grid*search.best_params* : 최적의 파라미터 확인

      > grid*search.best_score* : 점수확인

  - cv

- ### 성능평가
