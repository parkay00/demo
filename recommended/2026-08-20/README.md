# 2026-08-20 논문 추천

## 검색 정보
- 연구 기준일: 2026-08-20 (`REQUESTED_DATE` 미설정, Asia/Seoul 기준 어제)
- 실제 검색 창: 당일(2026-08-20) → 7일(2026-08-14~2026-08-20) → 30일(2026-07-22~2026-08-20) 순으로 확대, 30일 창에서 조건 충족
- 검색 쿼리: `chest radiograph deep learning diagnosis`

## 코호트 요약 (집계만, 환자 단위 값 없음)
- 총 영상 272건, 고유 환자 153명
- 성별: 남 136 / 여 136, 평균 연령 남 48.7세 / 여 54.3세
- 촬영 자세: PA 184건, AP 88건
- 소견 분포: No Finding 145건(과반), 이어서 Infiltration 21, Atelectasis 16, Nodule 7, Fibrosis 6, Effusion 6, Cardiomegaly 5, Pneumothorax 5 등. 다수 사례가 Effusion|Infiltration, Atelectasis|Infiltration 등 복합 라벨로 기록됨
- 데이터는 흉부 X선 단일 모달리티, 단일(가상) 기관 구성

## 선정 축 (axes)
- **판독문 기반 학습**: 판독 리포트/소견 텍스트를 영상 모델 학습에 직접 결합하는 접근
- **기관 간 일반화**: 외부·다기관 데이터에서의 성능 검증
- **소규모 코호트 데이터 증강**: 표본이 적은 병리에 대한 합성/증강 활용

## 논문별 코멘트

### CLEAR: an auditable foundation model for radiology grounded in clinical concepts
(Nature Biomedical Engineering, 2026) — 축: 판독문 기반 학습, 기관 간 일반화
- 87만 건 이상의 영상-리포트 쌍으로 학습한 개념 기반 흉부 X선 모델로, 예측을 개별 소견 기여도로 분해해 감사 가능성을 확보하고 4개 대륙 외부 데이터셋에서 최고 수준 성능을 보임.
- 우리 데이터와의 연결점: 코호트의 절반(145/272)이 No Finding이고 나머지는 다양한 복합 소견으로 구성돼, 예측 근거를 소견 단위로 제시하는 방식이 판독 검증에 도움이 될 수 있음.
- 한계: 본 코호트(153명, 단일 기관)는 CLEAR의 검증 규모에 비해 훨씬 작아 일반화 성능 자체를 재현할 수 없음.
- 링크: https://doi.org/10.1038/s41551-026-01741-4

### Grounding Radiology Report Findings into Medical Image Segmentation (CF2Seg)
(npj Digital Medicine, 2026) — 축: 판독문 기반 학습, 기관 간 일반화
- 판독 소견 텍스트를 직접 활용해 흉부 X선 병변을 분할하는 프레임워크로, 5.3만 건 규모 다기관 벤치마크에서 분포 변화와 주석 부족 상황에서도 안정적 성능을 보임.
- 우리 데이터와의 연결점: 복합 라벨 사례(Effusion|Infiltration 5건, Atelectasis|Infiltration 4건 등)가 다수 존재해, 판독문과 영상 위치를 연결하는 접근이 복합 병변 재검토에 참고될 수 있음.
- 한계: 본 코호트에는 픽셀 단위 전문가 분할 주석이 없어 분할 정확도나 병변 부담 일치도를 직접 검증할 수 없음.
- 링크: https://doi.org/10.1038/s41746-026-03051-0

### UniMedDiff: a knowledge-enhanced diffusion model for medical image generation from clinical reports
(npj Digital Medicine, 2026) — 축: 소규모 코호트 데이터 증강, 판독문 기반 학습
- 판독 리포트 기반 확산 모델로 실제 데이터 1%만 증강해도 전체 데이터 수준에 근접하는 분류 성능을 달성.
- 우리 데이터와의 연결점: 환자 153명, 영상 272건의 소규모 코호트이며 Nodule(7), Fibrosis(6), Pneumothorax(5) 등 희귀 소견의 표본이 매우 적어, 증강을 통한 학습 보완이 실질적으로 유용할 수 있음.
- 한계: 합성 영상의 임상적 타당성을 검증할 방사선과 전문의 리뷰 체계가 본 프로젝트에는 없어 생성 품질 주장을 그대로 확인할 수 없음.
- 링크: https://doi.org/10.1038/s41746-026-03135-x

## 검토 안내
이 추천은 자동 파이프라인이 생성한 초안이며, 임상 적용 전 반드시 담당 의료진의 검토와 판단이 필요합니다.
