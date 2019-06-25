# [PCoE Datasets](https://ti.arc.nasa.gov/tech/dash/groups/pcoe/prognostic-data-repository/) 번역

### PHM08 Prognostics Data Challenge Dataset

#### 설명
이 데이터 세트는 International Conference on Prognostics and Health Management(PHM08)에서 사전예지 분석 Competition에 사용되었습니다. 챌린지는 연구자가 2008 년에 챌린지 승자와 비교하여 자신의 노력을 개발하고 비교할 수 있도록 개방되어 있습니다. 3가지 수상 논문에 대한 문헌은 아래에 나와 있습니다.

 - [1] Heimes, F.O., "Recurrent neural networks for remaining useful life estimation", in the Proceedings of the 1st International Conference on Prognostics and Health Management (PHM08), Denver CO, Oct 2008.
 - [2] Tianyi Wang, Jianbo Yu,  Siegel, D.,  Lee, J., "A similarity-based prognostics approach for Remaining Useful Life estimation of engineered systems", in the Proceedings of the 1st International Conference on Prognostics and Health Management (PHM08), Denver CO, Oct 2008.
 - [3] Peel, L., "Recurrent neural networks for remaining useful life estimation", in the Proceedings of the 1st International Conference on Prognostics and Health Management (PHM08), Denver CO, Oct 2008.

#### Experimental Scenario
데이터셋은 여러 다변수 시계열로 구성됩니다. 각 데이터셋은 학습 및 테스트 하위 집합으로 더 나뉩니다. 시계열 데이터는 각각 다른 엔진에서 나왔습니다. 즉, 데이터는 동일한 유형의 엔진으로 구성된 것으로 간주 할 수 있습니다. 각 엔진은 사용자에게 알려지지 않은 다양한 초기 마모 및 제조 편차로 시작합니다. 이 마모 및 변동은 정상적인 것으로 간주되며, 즉 결함 조건으로 간주되지 않습니다. 엔진 성능에 상당한 영향을주는 세 가지 작동 설정이 있습니다. 이러한 설정은 데이터에도 포함됩니다. 데이터가 센서 노이즈로 오염되었습니다.


엔진은 각 시계열데이터의 시작부분에서는 정상적으로 작동하고 시계열데이터 중 일부 지점에서 성능이 저하되기 시작합니다. 트레이닝 세트에서 엔진을 작동시키는 것이 적절하지 않은 미리 정의 된 임계값에 도달 할 때까지 성능 저하가 커집니다. 테스트셋에서 시계열데이터는 직동이 완료되기 전에 종료됩니다. Competition의 목적은 테스트셋 이전의 잔여 작동 사이클의 수, 즉 엔진이 적절하게 계속 작동 할 마지막 사이클 이후의 작동 사이클의 수를 예측하는 것입니다.

#### Usage
데이터는 공백으로 구분 된 26 열의 숫자로 이루어진 압축 된 텍스트 파일로 제공됩니다. 각 행은 단일 작업주기 동안 수집 된 데이터의 스냅샷입니다. 각 열은 다른 변수입니다. 열은 다음에 해당합니다:

| column | contents               |
| ------ | ---------------------- |
| 1      | unit number            |
| 2      | time, in cycles        |
| 3      | operational setting 1  |
| 4      | operational setting 2  |
| 5      | operational setting 3  |
| 6      | sensor measurement  1  |
| 7      | sensor measurement  2  |
| ...    | ...                    |
| 26     | sensor measurement  26 |

사용자는 `train.txt` 파일의 데이터를 사용하여 알고리즘을 학습해야합니다. 그 후 파일 `test.txt`에 제공된 데이터에서 RUL 예측 성능을 평가해야합니다. 관련 진정한 RUL 값은 Competition에서와 마찬가지로 공개되지 않습니다. 곧 사용자는 웹 응용 프로그램을 사용하여 결과를 업로드하고 총점 피드백을 얻을 수 있습니다. 자동 채점을위한 웹 응용 프로그램에 대한 자세한 내용을 보려면 2010년 6월에 다시 확인하십시오. 그때까지는 간단한 텍스트 파일을 통해 결과를 아래 제공된 이메일 주소로 메일로 보내 피드백을 얻을 수 있습니다. 대회 기간 동안 얻은 대표적인 20대 점수 세트가 여기에 포함되어 모든 사람들에게 참조 정보를 제공합니다.

| No. | Score    |
| --- | -------- |
| 1   | 436.841  |
| 2   | 512.426  |
| 3   | 737.769  |
| 4   | 809.757  |
| 5   | 908.588  |
| 6   | 975.586  |
| 7   | 1,049.57 |
| 8   | 1,051.88 |
| 9   | 1,075.16 |
| 10  | 1,083.91 |
| 11  | 1,127.95 |
| 12  | 1,139.83 |
| 13  | 1,219.61 |
| 14  | 1,263.02 |
| 15  | 1,557.61 |
| 16  | 1,808.75 |
| 17  | 1,966.38 |
| 18  | 2,065.47 |
| 19  | 2,399.88 |
| 20  | 2,430.42 |

#### Evaluation
최종 점수는 RUL 오류의 가중치 합계입니다. 채점 함수는 초기 예측보다 늦은 예측에 패널티를 주는 비대칭 함수입니다. (자세한 내용은 첨부 문서 참조)

알고리즘이 만족스럽게 학습이 되면 사용자는 `final_test.txt` 파일에 포함 된 최종 테스트 데이터 세트에 적용 할 수 있습니다. 사용자는 평가를 위해 최종 시험 세트에 대한 RUL 벡터를 PHM 학회에 보내야합니다. 점수가 곧 우편으로 발송됩니다. 연구원은 자신의 알고리즘에 새로운 것이 있다고 믿는다면 절대적인 성과에 상관없이 결과를 발표 할 것을 권장합니다. 이 자료 배포의 의도는 사전예지를 위한 혁신적인 접근법을 개발하는 것이기 때문입니다.
참고 : 팀 또는 개인은 누구든지 최종 테스트 세트에서 단 한번만 결과를 제출할 수 있습니다.

| Data Set                | `train.txt`, `test.txt` |
| ----------------------- | ----------------------- |
| Train trjectories       | `218`                   |
| Test trajectories       | `218`                   |
| final_test trajectories | `435`                   |


#### Contacts
 - Abhinav Saxena : abhinav.saxena@nasa.gov, 650-604-3208
 - Kai Goebel : kai.goebel@nasa.gov 

#### References
A. Saxena, K. Goebel, D. Simon, and N. Eklund, "Damage Propagation Modeling for Aircraft Engine Run-to-Failure Simulation"ㅍ, in the Proceedings of the 1st International Conference on Prognostics and Health Management (PHM08), Denver CO, Oct 2008.
