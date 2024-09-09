- [교차검증](https://velog.io/@ohxhxs/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D-%EA%B5%90%EC%B0%A8%EA%B2%80%EC%A6%9D-KFold-StratifiedKFold-crossvalscoreGridSearchCV) - cross_val_score > cross_val_score(sgd_clf, X_train, y_train_5, cv=3, scoring="accuracy") - StratifiedKFold - 교차검증 과정을 더 많이 제어해야 할때 사용

  ````
  from sklearn.model_selection import StratifiedKFold
  from sklearn.base import clone

          skfolds = StratifiedKFold(n_splits=3)  # 데이터셋이 미리 섞여 있지 않다면
                                              # shuffle=True를 추가하세요.
          for train_index, test_index in skfolds.split(X_train, y_train_5):
              clone_clf = clone(sgd_clf)
              X_train_folds = X_train[train_index]
              y_train_folds = y_train_5[train_index]
              X_test_fold = X_train[test_index]
              y_test_fold = y_train_5[test_index]

              clone_clf.fit(X_train_folds, y_train_folds)
              y_pred = clone_clf.predict(X_test_fold)
              n_correct = sum(y_pred == y_test_fold)
              print(n_correct / len(y_pred))
          ```

  ````

- 오차행렬

* 정밀도, 재현율

  - [임계값](https://support.minitab.com/ko-kr/minitab/help-and-how-to/statistics/basic-statistics/supporting-topics/basics/what-is-a-critical-value/)

  - 정밀도/ 재현율에 대한 그래프를 그리기 보다는 f1-score을 통해 확인하면 됨

* ROC, AUC
