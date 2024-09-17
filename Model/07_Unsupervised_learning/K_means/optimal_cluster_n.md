- 엘보 그래프: for 문을 통해 kmeans의 n_cluster옵션을 변경해가며 시각화.

- 코드 예시
    ```
    # 추가 코드 - 이 셀은 그림 9-8을 생성하고 저장합니다.

    kmeans_per_k = [KMeans(n_clusters=k, n_init=10, random_state=42).fit(X)
                    for k in range(1, 10)]
    inertias = [model.inertia_ for model in kmeans_per_k]

    plt.figure(figsize=(8, 3.5))
    plt.plot(range(1, 10), inertias, "bo-")
    plt.xlabel("$k$")
    plt.ylabel("이너셔")
    plt.annotate("", xy=(4, inertias[3]), xytext=(4.45, 650),
                arrowprops=dict(facecolor='black', shrink=0.1))
    plt.text(4.5, 650, "엘보", horizontalalignment="center")
    plt.axis([1, 8.5, 0, 1300])
    plt.grid()
    save_fig("inertia_vs_k_plot")
    plt.show()
    ```

- 실루엣 점수  
    - 실루엣 다이어그램
    - 한 클러스터의 샘플이 낮은 계수를 가지면 다른 클러스터랑 너무 가깝다는 것을 의미