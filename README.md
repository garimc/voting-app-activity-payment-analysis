# Voting app activity payment analysis - 유저 활동 일수 및 결제율 향상을 위한 핵심 요인 분석

![Image](https://instinctive-milk-d9b.notion.site/image/attachment%3A46b16c1e-ac96-47d5-a7ca-130dc86f1bd5%3A%E1%84%8E%E1%85%A5%E1%86%BC%E1%84%89%E1%85%A9%E1%84%82%E1%85%A7%E1%86%AB_%E1%84%8B%E1%85%B5%E1%86%A8%E1%84%86%E1%85%A7%E1%86%BC_%E1%84%90%E1%85%AE%E1%84%91%E1%85%AD_2.png?table=block&id=2629d974-08e6-8046-b7a1-c6698ba81d96&spaceId=f80357d3-0f5e-4223-be11-6f5365fc1458&width=1380&userId=&cache=v2)

![image](https://instinctive-milk-d9b.notion.site/image/attachment%3A364398ac-efb6-47fd-a227-c35a6a4fa024%3A%E1%84%8E%E1%85%A5%E1%86%BC%E1%84%89%E1%85%A9%E1%84%82%E1%85%A7%E1%86%AB_%E1%84%8B%E1%85%B5%E1%86%A8%E1%84%86%E1%85%A7%E1%86%BC_%E1%84%90%E1%85%AE%E1%84%91%E1%85%AD_3.jpg?table=block&id=2629d974-08e6-80bd-8062-ee1ea131dd71&spaceId=f80357d3-0f5e-4223-be11-6f5365fc1458&width=1380&userId=&cache=v2)

---

## TL;DR

- 10대 청소년 대상 익명 투표 앱의 **리텐션 저조 및 결제율 하락 원인 분석** 프로젝트
- **네트워크 지표, 행동 패턴, 머신러닝 모델링**을 종합하여 활동일수와 결제를 동시에 향상시킬 수 있는 요인 탐색
- 결론: **친구 수와 네트워크 구조**가 핵심 요인임

**TL;DR (English)**

- Project analyzing the **low retention and declining payment rate** of an anonymous voting app for teenagers
- Explored factors that can simultaneously improve **user activity days and payments** through **network metrics, behavioral patterns, and machine learning models**
- Conclusion: **Number of friends and network structure** are key factors

---

## Project Overview

본 프로젝트는 청소년 익명 투표 앱의 **저조한 리텐션과 결제율 문제**를 해결하기 위해 시작되었습니다. 데이터 분석을 통해 **네트워크 구조·행동 패턴·모델링 결과**를 종합적으로 검토하고, 앱의 **활동성과 수익성 동시 개선 전략**을 도출하는 것을 목표로 합니다.

**Project Overview (English)**

This project was initiated to address the issue of **low retention and payment rate** in an anonymous voting app for teenagers. Through data analysis, it comprehensively examined **network structure, behavioral patterns, and modeling results**, with the goal of deriving strategies to improve both **user engagement and monetization**.

---

## Tech Stack

- Python (pandas, numpy, itertools, re)
- Visualization: matplotlib, seaborn
- Statistics: scipy, statsmodels
- Machine Learning: scikit-learn (Logistic Regression, RandomForest), imbalanced-learn (SMOTE)
- Sequential Pattern Mining: PrefixSpan
- Network Analysis: NetworkX, Gephi
- Environment: Jupyter Notebook

---

## What’s inside:

- 분석 통합 파일 (Main Notebook): [`voting-app-activity-payment-analysis`](./voting-app-activity-payment-analysis.ipynb)
- 프로젝트 보고서 파일 (Full Write-up): [`reports/report.pdf`](./reports/report.pdf)
- 데이터 설명 (Data Dictionary): [`data/data_dictionary.md`](./data/data_dictionary.md)

---

## Project Structure

```python
voting-app-activity-payment-analysis/
├─ README.md
├─ voting-app-activity-payment-analysis.ipynb
├─ reports/
│ └─ report.pdf
├─ data/
│ └─ data_dictionary.md 
└─ requirements.txt
```

---

## Reproduce

1. 레포지토리 클론 (Clone this repository)

```
git clone <https://github.com/garimc/voting-app-activity-payment-analysis.git>
cd voting-app-activity-payment-analysis
```

2. 가상환경 생성 및 활성화 (선택) (Create a virtual environment (optional))

```
python -m venv .venv
source .venv/bin/activate
```

3. 필요한 패키지 설치 (Install dependencies)

```
pip install -r requirements.txt
```

4. 주피터 실행 (Run Jupyter Lab / Notebook)

```
jupyter lab
```

5. 노트북 열기 및 실행 (Open and run the notebook)
- [’voting-app-activity-payment-analysis.ipynb`](./voting-app-activity-payment-analysis.ipynb)
- 파일을 열고 위에서부터 차례대로 실행합니다.
- Execute all cells (top → bottom)

### ⚠️ Caution

- 코드와 분석 로직은 동일하게 실행할 수 있지만, 데이터가 없으므로 결과(숫자·그래프)는 재현되지 않습니다.
- Without the dataset, all analysis steps can be executed, but outputs (figures and numbers) cannot be reproduced.

---

## Data & Ethics

- 실제 데이터는 공유 불가 (보안 및 비밀유지 조항).
- 분석 과정, 코드, 변수 정의, 결과물만 공개.

**Data & Ethics (English)**

- The original dataset cannot be shared due to security and confidentiality agreements.
- Only the analysis process, code, variable definitions, and results are publicly available.

---

## Insights/Conclusions

1. 유저 친구 수는 활동성과 결제의 핵심 변수 

2. 결제와 활동은 서로 영향을 주는 선순환 구조 

3. 개인이 속한 네트워크는 개인의 활동성과 결제에 큰 영향을 줌 

4. 네트워크 구조는 학교의 활동성과 결제에 중요한 영향 

5. 개인의 투표 참여도 또한 활동 지속성을 예측하는 중요한 변수 

6. 출석 체크, 푸시 알림, 성별, 학교 종류도 결제에 유의한 영향 

**Insights/Conclusions (English)**

1. Number of friends is a key factor for both activity and payment
2. Payments and activities influence each other in a virtuous cycle
3. A user’s network significantly affects their activity and payment
4. Network structure strongly impacts school-level activity and payment
5. Individual voting participation is an important predictor of sustained activity
6. Attendance checks, push notifications, gender, and school type also have significant effects on payments

---

## License

- Code: MIT
- Reports & Figures: CC BY-NC 4.0
