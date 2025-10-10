---
layout: single
title: "FitChecker 요구사항 분석"
categories: [Unity]
tags: [Unity]   
toc: true
classes: wide
---

목표 : 내 치수와 옷에 나와있는 치수 비교하여 최상의 핏을 뽑아내자! -> 2D 이미지로 착샷 제공까지

범위 : 상의(어깨,가슴,총장) 하의(허리,골반,엉덩이,허벅지,밑단)

입력 : 내 프로필 수동입력 

출력 : tight, ok, roomy + 몇cm 차이인지 ( 추후 허리핏인지 골반핏인지 선택으로 확장 )

임계값 : 흠

확장 : 물리엔진 및 3D겟지 / 신발도 있으면 좋을듯

좋은거 : 

* 뭔가 내가 제일 아름답다고 생각한 옷의 스펙을 저장해놓으면 존나 좋을거같음
* inch -> cm 도 좋을듯





0924

내 치수를 정확하게 잰다. cm 기준

**측정 가이드**를 텍스트 파일로 정리해둔다.

- 어깨단면: 어깨뼈 끝~끝 직선
- 가슴둘레: 유두 기준 둘레
- 허리둘레: 배꼽 위 2cm 둘레 …
- 인심: 사타구니 시작점~발목뼈

→ 이게 나중에 앱 온보딩 튜토리얼의 “치수 재는 법” 그대로 쓸 수 있음.

내 프로필 입력

- `UserProfile.json` or Unity ScriptableObject에 기록
- 단위(cm) 고정, 나중에 변환 가능
- 최소 필드만: `height, shoulderBreadth, chestCirc, waistCirc, hipCirc, thighCirc, inseam`

**Golden Fit 1벌 등록**: 가장 지리는 옷 치수 측정 → `GoldenFit.json` 저장

**CSV 샘플 1개 작성**: `tops.csv`/`bottoms.csv` 파일에 그 옷 치수 1줄 기입
 → 나중에 임포트 테스트하기 편해짐.