# 2026-08-21 논문 추천

## 검색 정보
- 연구 기준일: 2026-08-21 (`REQUESTED_DATE` 미설정, Asia/Seoul 기준 어제)
- 실제 검색 창: 당일(2026-08-21) → 7일(2026-08-15~2026-08-21) 모두 결과 없음 → 30일(2026-07-22~2026-08-21) 창에서 조건 충족
- 검색 쿼리: `chest radiograph deep learning multicenter validation`

## 코호트 요약 (집계만, 환자 단위 값 없음)
- 총 영상 272건, 고유 환자 153명
- 성별: 남 136 / 여 136, 연령 범위 9~87세(평균 약 51.5세)
- 촬영 자세: PA 184건, AP 88건
- 기관 코드 5개(INST01~05)에 걸쳐 48~62건씩 분포
- 소견 분포: No Finding 145건(과반), 이어서 Infiltration 21, Atelectasis 16, Nodule 7, Fibrosis 6, Effusion 6, Cardiomegaly 5, Pneumothorax 5 등. 다수 사례가 Effusion|Infiltration, Atelectasis|Infiltration 등 복합 라벨로 기록됨
- 데이터는 흉부 X선 단일 모달리티 구성

## 선정 축 (axes)
- **기관 간 일반화**: 다기관·외부 데이터에서의 성능 재현성
- **저빈도 소견 성능 저하**: 표본이 적은 병리·질환에서 나타나는 정밀도 하락
- **연령·성별 편향**: 인구학적 하위집단 간 성능 격차
- **구조화 판독 소견 결합**: 텍스트 소견을 영상 모델과 결합하는 접근

## 논문별 코멘트

### Advancing human-centric AI for robust X-ray analysis through holistic self-supervised learning (RayDINO)
(Nature Communications, 2026) — 축: 연령·성별 편향, 기관 간 일반화
- 84만 장으로 학습하고 12개 공개 데이터셋 8.2만 장으로 외부 검증한 자기지도학습 흉부 X선 인코더로, 9개 과제에서 최고 수준 성능과 함께 인구·연령·성별 편향 완화를 보고.
- 우리 데이터와의 연결점: 남 136/여 136으로 성비가 균형 잡혀 있고 연령이 9~87세로 넓게 분포해, 논문이 강조한 연령·성별 편향 분석 프레임이 우리 하위집단 성능 점검에 참고될 수 있음.
- 한계: 본 코호트(272건, 153명)는 RayDINO 검증 규모와 차원이 달라 편향 완화 효과를 직접 재현할 수 없음.
- 링크: https://doi.org/10.1038/s41467-026-76076-4

### Multicenter evaluation of four large language models for automated spine imaging diagnosis
(npj Digital Medicine, 2026) — 축: 기관 간 일반화, 저빈도 소견 성능 저하
- 3개 기관 2만여 건 판독 리포트로 4개 LLM을 비교, 전반적 특이도·음성예측도는 높았으나 저빈도 질환에서 정밀도가 19~42%p 하락하는 장꼬리 문제를 확인.
- 우리 데이터와의 연결점: No Finding이 145/272건으로 과반을 차지하고 Nodule 7, Fibrosis 6, Pneumothorax 5건 등 저빈도 소견 표본이 매우 적어, 이 논문이 지적한 저빈도 병리 정밀도 저하가 우리 데이터에서도 우려됨.
- 한계: 이 논문은 텍스트 리포트 기반 LLM 진단이 대상이라 영상 자체의 분류 성능에 대한 직접 근거는 아님.
- 링크: https://doi.org/10.1038/s41746-026-03133-z

### Multimodal deep learning for preoperative invasiveness stratification of lung adenocarcinoma spectrum nodules
(npj Digital Medicine, 2026) — 축: 기관 간 일반화, 구조화 판독 소견 결합
- 3개 기관 2700여 명 코호트에서 CT 영상과 구조화 판독 소견을 결합한 다중모달 모델이 영상 단독·소견 단독보다 침습도 예측 AUC를 유의하게 개선(내부 0.914, 외부 0.879~0.895).
- 우리 데이터와의 연결점: Nodule 소견 7건이 존재하고 다수 사례가 Atelectasis|Infiltration, Effusion|Infiltration 등 복합 라벨로 기록돼, 영상-텍스트 소견 결합 접근이 복합 소견 해석에 참고될 수 있음.
- 한계: 이 논문은 흉부 CT 결절 검체이고 본 코호트는 단순 흉부 X선 자료라 모달리티가 달라 AUC 향상폭을 직접 확인할 수 없음.
- 링크: https://doi.org/10.1038/s41746-026-03062-x

## 검토 안내
이 추천은 자동 파이프라인이 생성한 초안이며, 임상 적용 전 반드시 담당 의료진의 검토와 판단이 필요합니다.
