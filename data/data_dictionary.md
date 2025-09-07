## Data Dictionary

### 데이터 구성

- **원천 데이터**: 유저 속성, 학교 속성, 네트워크 관계(친구 관계, 투표), 앱 로그
- **집계 기간**: 전체(2023-03-29 ~ 2024-05-09), 앱 로그(2023-07-18 ~ 2023-08-04)

### 분석 대상

- **유저** 676,987명 / **학교** 5,267개

### 분석 단위

- **유저 단위**: 활동일수, 결제, 이벤트 로그, 네트워크 지표
- **학교 단위**: 소속 유저의 평균 지표, 기타 네트워크 지표

### 변수 생성

- **활동일 테이블 재구성**:
    - **배경**: 원본 데이터에서 출석일은 ‘출석체크 버튼 클릭’만 포함되어 있었으나, 이는 실제 앱 이용일수를 정확히 반영하지 않음
    - **방법**: 유저 활동기록에서 특정 날짜에 이벤트가 1건 이상 발생하면 출석일로 인정하는 별도 테이블을 생성하여 분석에 활용
- **종속변수 이진화**:
    - **배경**: 분석 절차를 단순화하고 해석을 명확히 하기 위해
        - 유저/학교별 특징이 활동일수·결제에 미치는 영향 분석에서는 종속변수를 이진화하여 사용함
        - 핵심 세그먼트(고 활동·고 결제 집단) 특징 분석에서는 동일한 기준을 활용해 세그먼트를 정의함.
    - **유저 단위**: 활동일수 7일 이상 여부, 결제 여부
    - **학교 단위**: 평균 활동일수 7일 이상 여부, 결제율 0.1% 이상 여부
- **네트워크 지표 산출**:
    - **유저 단위:** 친구 수, clustering coefficient
    - **학교 단위**: 평균 친구 수, 평균 clustering coefficient, density, modularity
- **이벤트 파생 변수**: 결제 직전 행동 시퀀스, 이벤트별 체류 시간, 전환률

### 분석 변수 목록

- 유저 단위

| is_high_attendance | 평균활동일수 7일 이상 여부
(KPI) | pay_or_not | 결제 여부
(KPI) |
| --- | --- | --- | --- |
| attendance_count | 활동 일수 | ques_count | 참여한 질문 세트 수 |
| vote_count | 투표 참여 횟수 | chosen_count | 투표를 선택받은 횟수 |
| view_count | 질문 조각에 등장한 횟수 | total_paid_points | 총 재화 사용 금액  |
| school_id | 학교 id | question_skip_ratio | 스킵 비율 |
| group_id | 학급 id | vote_open_count | 투표 열어본 횟수 |
| school_type | 학교 형태(중 / 고) | is_push_on | 알림 ON 여부 |
| student_count | 학교 학생 수 | block_count | 차단 횟수 |
| gender_encoded | 성별 | blocked_count | 차단 받은 횟수 |
| friend_count | 친구 수 | report_count | 신고 받은 횟수 |
| is_question_skip | 스킵 여부 |  |  |
- 학교 단위

| is_high_attendance | 평균활동일수 7일 이상 여부
(KPI) | is_high_pay_ratio | 결제율 0.1 이상 여부
(KPI) |
| --- | --- | --- | --- |
| school_id | 학교 id | modularity | 분절도 |
| school_type | 학교 형태(중 / 고) | density | 밀도 |
| user_count | 학교 유저 수 | mean_attendance_count | 평균 활동 일수 |
| gender_ratio | 남성 비율 | mean_lifecycle | 평균 생명주기 |
| mean_friend_count | 평균 친구 수 | total_pay_amount | 총 충전 포인트 |
| avg_clustering | 평균 clustering coef | total_pay_count | 총 결제횟수 |
| mean_ques_count | 평균 참여한 질문 세트 수 | pay_user_count | 총결제자수 |
| mean_chosen_count | 평균 선택받은 횟수 | pay_ratio | 결제율 |
| mean_vote_open_count | 평균 투표 열어본 횟수 | mean_vote_count | 평균 투표 참여 횟수 |
| mean_block_count/
mean_blocked_count | 평균 차단(차단 받은) 횟수 | mean_question_skip_ratio | 평균 스킵 비율 |
| mean_report_count | 평균 신고 받은 횟수 | mean_is_push_on | 평균 알림 ON 비율 |

### 전처리 요약

- 사용자·세션 ID 불일치 처리 → 앱 로그 데이터 0.12% 감소
- 문자열 user_id 제거 → 앱 로그 데이터 0.35% 감소
- 앱 로그 정제 (`$session_start`/`$session_end` 제거) → 앱 로그 데이터 14.7% 감소
- 결제 기록 교차 검증 (`accounts_paymenthistory` vs `hackle_event`) 후 불일치 제거 → 제거율 미미(0.00%)
- 공통 처리: 모든 날짜 KST 통일