# kaggle_study
| date | 주제 | 분석 내용 | 느낀점 |
| :---: |:---:|:---:|:---:|
| 2018.10.01 ~ 2018.10.28 | [Doodle Recognition](https://www.kaggle.com/c/quickdraw-doodle-recognition) | [낙서 분류하기](https://github.com/jeeyeonLIM/Graduate_Course/tree/master/Financial%20engineering/Kaggle_Doodle_Recognition_Challenge) | CNN 학습 | 
| 2020.09.05 ~ 2020.09.09 | [Car Noise](https://www.kaggle.com/murtio/car-noise-specification) | [실내 소음에 영향 미치는 요인 탐색](https://github.com/jeeyeonLIM/kaggle_study/blob/master/1_handling.Rmd) |  |

### Doodle Recognition
- 금융공학 수업시간에 이미 끝난 competition 가지고 pilot으로 분석했다. 
- 캐글에 업로드되어있는 데이터를 분석하고 test할 때는 우리가 직접 낙서한 이미지가 어떤 범주에 해당되는지 예측하도록 해서 재밌었다.

### Car Noise 
#### [2020/09/10]
- [1_handling](https://github.com/jeeyeonLIM/kaggle_study/blob/master/1_handling.Rmd)
- [2_EDA](https://github.com/jeeyeonLIM/kaggle_study/blob/master/2_EDA.Rmd)
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


