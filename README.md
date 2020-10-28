# kaggle_study
| date | 주제 | 분석 내용 | 느낀점 |
| :---: |:---:|:---:|:---:|
| 2018.10.01 ~ 2018.10.28 | [Doodle Recognition](https://www.kaggle.com/c/quickdraw-doodle-recognition) | [낙서 분류하기](https://github.com/jeeyeonLIM/Graduate_Course/tree/master/Financial%20engineering/Kaggle_Doodle_Recognition_Challenge) | CNN 학습 | 
| 2020.09.05 ~ 2020.09.09 | [Car Noise](https://www.kaggle.com/murtio/car-noise-specification) | - 1차분석 : [Data Handling](https://github.com/jeeyeonLIM/kaggle_study/blob/master/1_handling.Rmd), [EDA](https://github.com/jeeyeonLIM/kaggle_study/blob/master/2_EDA.Rmd)  |  |
| 2020.09.15 ~ 2020.09.24 | [Car Noise](https://www.kaggle.com/murtio/car-noise-specification) | - 최종분석 : [Data Handling](https://github.com/jeeyeonLIM/kaggle_study/blob/master/NEW2_1.Rmd), [Small](https://github.com/jeeyeonLIM/kaggle_study/blob/master/NEW2_small.Rmd), [Medium](https://github.com/jeeyeonLIM/kaggle_study/blob/master/NEW2_medium.Rmd), [Large](https://github.com/jeeyeonLIM/kaggle_study/blob/master/NEW2_large.Rmd)  |  |

### Car Noise 

- [최종 분석 결과 자료](https://github.com/jeeyeonLIM/kaggle_study/blob/master/car_noise_%EC%B5%9C%EC%A2%85%EB%B6%84%EC%84%9D%20%EA%B2%B0%EA%B3%BC%20%EC%A0%95%EB%A6%AC.pdf)

#### [2020/09/10]

- 차량 부품 및 기술 공부에서 모든 시간을 변수의 의미 찾고 정리하는 데 소요했다. 
- 문제 정의와, 모델링을 위한 Y 기준 정의, NA값이 너무 많아서 처리하는 데 어려움을 겪었다.
- Q. 이렇게 결측치가 너무 많은 경우 대체방법을 사용하기 애매한 부분이 있었다. 
  - 거르고 거른 데이터의 row가 약 1,000개였는데 이 중 5% 만이 모든 값이 존재했고 이외의 값은 하나 이상 결측이 존재했다.
  - 칼럼별로 보면 대부분의 칼럼값이 결측이 많아서 60% 이상의 결측치를 갖는 변수는 일단 제거했다. 
  - 보통 30% ?? 이하일 때 대체 방법을 사용하는걸로 알고있다.
- 이럴 때는 어떻게 분석을 진행해야하는 지 답답하다.

#### [2020/09/16]
- [중간분석 결과](https://github.com/jeeyeonLIM/kaggle_study/blob/master/NEW.html)
- 피드백 : `자동차 소음 허용 기준` 내에 속한다면 소음이 크면 안좋은걸까? 아래와 같은 큰 흐름 가이드라인을 제시해주심.
    - 1. 자동차 소음 허용 기준 내에 속하는 차와 속하지 않는 차 구분 → 두 그룹의 차이 비교 및 원인 분석
    - 2. 모두 허용 기준 내에 속하는 경우 → 물리적 기준(차종 등)으로 군집화 후 동일 그룹 내에 소음에 영향을 미치는 요인 분석

#### [2020/09/18]
- 자동차 출시년도와 종류에 따라서 소음 항목을 구분해 놓은 법령을 찾았고 살펴보니 가속주행소음, 배기소음, 경적소음에 대한 기준은 있으나, 모두 실외에서 측정되는 소음이고, 실내 내부에 대한 제한 법률은 없음. 외부 소음 기준을 실내에 적용하기에 어려움이 있다고 판단. 
- [[별표 18의2] 제작차 소음(가속주행소음) 측정방법(제6조 관련)](http://www.law.go.kr/%ED%96%89%EC%A0%95%EA%B7%9C%EC%B9%99/%EC%A0%9C%EC%9E%91%EC%9E%90%EB%8F%99%EC%B0%A8%EC%8B%9C%ED%97%98%EA%B2%80%EC%82%AC%EB%B0%8F%EC%A0%88%EC%B0%A8%EC%97%90%EA%B4%80%ED%95%9C%EA%B7%9C%EC%A0%95) - 
- 최종 목표 정해짐. :point_right: " 물리적 기준(차종 등)으로 군집화 후 동일 그룹 내에 소음에 영향을 미치는 요인 분석"
- 결측치 처리방법에 대해서 가장 합리적으로 정리해 놓은 블로그 발견 
  - https://nittaku.tistory.com/451

- S/M/L 분류-> 조건에 해당하지 않는 차는 예측 
- 그룹 비교 EDA, Modeling 진행 

#### [2020/09/19]
- S/M/L 분류한 것 각각 단변량 EDA
- 이상치 Handling, Modeling 할때 고려해볼 만한 것 정리. 
- optim, optimx 찾아봄.
- 언제 다하죠 ?..ㅠ_ㅠ

#### [2020/09/20]
- 전체 데이터에서 categorical 변수 처리- 재범주화 
- 소형차 전처리, 모델링

#### [2020/09/21]
- 최적화된 Noise를 위한 x값 조합 찾기.
    -> 최적값 찾기에 있어서 어려웠던 점은 R에서 제공하는 optim/optimx 를 이용하는 방법이 있는데 이렇게되면 각각의 x값마다 제한조건을 주는 데 어려움이 있었다. 또 수렴하지 않는 경우도 있었다.
    -> 따라서 직접 변수값을 조정해가며 for문을 돌려서 찾거나 해야 하는데 ( 15개 ~ 20개 변수에 대해서), 과연 이게 맞는 방법일지를 고민했다. 
    -> 결국 lsolve 이용하여 y(noise) 최소로 하는 x값 조합 찾는 방법 완료(각각의 변수에 대한 제한조건을 넣어줄 수 있고, 시간도 매우 짧게 소요되었다)
- Middle, Large도 진행해서 내일 피드백 한번 더 받을 예정이다. 

#### [2020/09/22 ~ 9/24]
- 끝!!!! 
- 결국 최종적으로 분석 완료함. 

#### [마지막 피드백]
- 결측치 처리방식에 있어서 train에 적용하고 test에는 NA 처리하지 않은 상태로 예측해야 하는 것이 아닌지.
- Best Car 선정은 이미 Noise값이 데이터에 있는데? 왜 했는지 -> 


### Doodle Recognition
- 금융공학 수업시간에 이미 끝난 competition 가지고 pilot으로 분석했다. 
- 캐글에 업로드되어있는 데이터를 분석하고 test할 때는 우리가 직접 낙서한 이미지가 어떤 범주에 해당되는지 예측하도록 해서 재밌었다.






