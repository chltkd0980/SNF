# Zr 합금 산화막 주기 전이(cyclic transition) 연구 주제 탐색 노트

- 작성일: 2026-10-09 (탐색 기간 2026-10-06 ~ 10-09)
- 작성: Claude (Fable 5.1) + 최상일 박사 대화 기록 정리
- 용도: GitHub `SNF/` 폴더에 보관, 클라우드 세션에서 이어서 작업
- 로컬 자료: `Cowork\Zr_oxide_oscillator\` (pptx, 빌드 스크립트, `refs\` 원문 PDF·추출 텍스트). 클라우드 세션에서는 이 노트의 인용문·수치·URL만으로 이어갈 수 있도록 작성함.

---

## 0. 한 줄 요약

Zr 합금 산화막은 약 2 μm마다 보호성을 잃고 다시 시작하는 **주기 전이**를 보인다. 이 현상을 설명하는 정량 모델은 서로 양립하지 않는 세 갈래(맨체스터 Platt, 미시간 Gupta, NPIC Liao)가 있고, 리뷰 논문들은 "이론 틀은 대체로 미검증", "근본적 해석적 기술이 없다"고 명시한다. **주기 전이 모델만을 같은 실측 데이터로 비교한 리뷰·벤치마크는 없다.** 이것이 현재 확인된 빈 자리이며, 다음 단계는 (1) 기존 리뷰 논문을 더 깊이 파고 모델 목록을 닫는 것, (2) 공통 데이터로 모델을 판별하는 것이다. 타 분야 이론(완화 진동자 등)의 이식은 보류.

---

## 1. 배경: 이 주제에 이른 경로

### 1.1 출발점
- 사용자의 처음 발상: "고준위 방사원이 붕괴해도 방사능이 안 나오는 획기적 메커니즘" 수준의 Nature급 주제.
- 물리 진단: α·β 붕괴율의 환경 제어는 길이 없음(α 0.1~1 %, β 10⁻⁵ 수준 불변, 속박상태 β 붕괴는 저장링 한정, NEEC·Hf-178m2 주장은 반박됨). "환경이 핵 과정을 제어"하는 유일한 실증 무대는 Th-229 이성질핵 전이(핵시계)였고, 그 호스트 결정의 자기조사 손상 모델링을 한동안 검토함(별도 노트·pptx 8장 존재).
- 이후 사용자가 역량을 **"실험 현상을 파이썬으로 해석하는 것"**으로 재정의하고, 마이트너식(미해결 실험 현상 + 검증된 기존 이론 → 발표 데이터로 검증) 연역 작업을 요구.

### 1.2 등급에 대한 솔직한 전제
- 계산 단독으로 Nature 본지에 간 조사손상·부식 논문은 사실상 없음(Bai 2010 Science는 새 일반 메커니즘 + 다중척도 모사; Goryaeva 2023 Nat. Commun.이 계산 단독 상한선).
- 따라서 목표 등급은 Corrosion Science·JNM·Acta급 모델 판별/리뷰 논문이고, 실험 협업이 붙으면 상향.

### 1.3 후보 주제 선별 (원자력 재료 미해결 현상 × 외부 이론)
| 후보 | 현상 | 빌려올 이론 | 판정 |
|---|---|---|---|
| SAV → 수소 크립 가속 | 고용 수소가 Zr 크립 가속 | 후카이 초과공공 | **철회**: 사용자 논문(ΔQ_H = E_b·θ, 전위 코어 점유율)의 변주 |
| 유효온도 → RPV 선속 효과·조사 고용도 | 선속 의존 석출 | Martin-Bellon 구동계 | 이미 적용됨 |
| 브라운 래칫 → 조사 크립 | σφ 선형 크립 | 분자모터 | 이론 포화, 새 예측 없음 |
| **A. Zr 산화 주기 전이** | 2 μm 주기 전이, f_H 주기, 수소화물 가속 | 완화 진동자(비선형동역학) | **선택 → 검증 진행** |
| B. FFRD 문턱 | 60~65 GWd/t 미세파편화 | 결정립계 기포 침투 | 부분 선행(위상장 연결성 문턱) |
| C. c-루프/breakaway 문턱 | 40년 미해결 | 수소 안정화 공공 평판 핵생성 | 사용자 형식의 확장, 자명도 중간 |
| D. Th-229 형석 호스트 자가치유 | 2주 어닐링 필요 | 초이온 음이온 부격자 | 별도 줄기 |

### 1.4 사용자 지시로 확정된 우선순위 (2026-10-08)
> "주기성을 반영한 기존 산화막 모델을 리뷰하는 게 가장 큰 이슈고, 다른 이론을 가지고 와서 붙여 넣는 것은 추후에 다시 논의."

즉 **현 단계 = 기존 모델·리뷰의 정밀 조사**. 완화 진동자 정식화는 보류.

---

## 2. 핵심 아이디어 (현재 형태)

1. 주기 전이는 확립된 사실이지만 **기구는 미결**이고, 정량 모델은 세 갈래가 서로 양립하지 않는다.
2. 세 모델 + 공학 경험식 + 침투 모델을 **같은 실측 데이터 7종**으로 판별하는 리뷰·벤치마크가 없다.
3. 수소화물 가속 부식(고연소 phase III의 유력 가설)과 수소흡수율 f_H의 주기성은 판별의 결정적 지표가 된다(어느 모델도 아직 수소화물 항이 없음).
4. 산출물: ① 모델 판별표 ② 수소화물 가속의 기구(문턱 저하 vs 주기 내 가속) ③ 산화-수소흡수 결합 모델. 1차 결과는 새 실험 없이 발표 데이터 재해석으로 가능.

---

## 3. 확립된 사실 (1차 출처에서 직접 확인, 체크리스트 C1~C8)

검증 원칙: 결론을 내가 말하는 대신 주장을 쪼개 1차 출처(저자 공개 PDF, 오픈액세스, 기관 리포지토리)로 확인. Sci-Hub는 사용하지 않음. ScienceDirect는 사용자 크롬에도 기관 인증이 없어 저자 공개판으로 대체.

### C1. 주기성 — 확인 (Yilmazbayhan et al., JNM 324 (2004) 6–22; Motta et al., JASTMI 2005)
- "후전이 영역은 전전이 운동학을 흉내 내는 여러 주기의 부식으로 구성되며, 개별 시편에서 주기적 성격은 여러 반복을 통해 쉽게 구별된다."
- 360 °C 순수 784일: Zircaloy-4 산화막 31 μm에 층 17개, 평균 층 두께 1.82 μm. 층 두께는 후전이 부식 속도에 반비례.
- Table 2 (1차 전이 일/μm, 평균 층 두께): Zircaloy-4 28일/1.50, 1.82 μm · ZIRLO 84일/2.32, 2.01 μm · Zr-2.5Nb 112일/2.41, 2.54 μm · Zr-2.5Nb-0.5Cu 112일/2.43, 2.87 μm. 후전이 속도: 0.58/0.33/0.21/0.14 mg/dm²/d.
- 정방정 분율이 "층 두께와 비슷한 주기로 주기적으로 증감하며 산화막 붕괴·재구축의 반복과 일치". 계면 근처 고정방정 영역 두께 1.8~2.87 μm.
- **단서**: "전이의 원인은 아직 규명되지 않았으며, 산화막 응력 축적과 그에 따른 대규모 균열·기공 발달과 관련된 것으로 생각되지만 다른 견해도 존재한다."
- **경계 조건 (Motta 2005, Table 3)**: 순수에서는 세 합금 모두 주기적(층 주기 XRD/광학/TEM 일치: Zry-4 1.85, ZIRLO 2.2~2.3, Zr-2.5Nb 2.9~3.1 μm). **리튬수(70 ppm Li)에서는 ZIRLO만 주기적, Zircaloy-4와 Zr-2.5Nb는 주기성 없음 + 계면 평행 균열 + 가속(후전이 속도 2.02, 84.6 mg/dm²/d).** → 모델은 "진동 영역 / 폭주 영역" 분기를 재현해야 함.
- Couet 2014 Table 4 (1차/2차 전이 두께): Zircaloy-4 sheet 2.1/4.5, tube 2.6/4.9, ZIRLO sheet 2.9/5.7, tube 3.1/–, Zr-2.5Nb 3.5/–, Zr-2.5Nb-0.5Cu 3.2/– μm. 2차 ≈ 1차의 2배.
- Liao 2024: "2차 전이 시간은 예외 없이 1차의 거의 2배".

### C2. 응력 문턱·t→m 변태·균열 — 가설 수준으로 확인
- 2004 시점에 가설("다른 견해도 존재"). Platt 2015는 균열·거칠기로 구체화. Motta 2015 리뷰는 두 기구(응력 축적→붕괴 / 기공 침투)를 나란히 둠.

### C3. 기판 금속 크립의 응력 완화 기여 — 원문 확인 (Platt et al., JNM 456 (2015) 415–425; Platt EngD thesis, Manchester, Proposed Paper 1·7장)
- 관측: Zircaloy-4 360 °C 오토클레이브, 산화막 평균 면내 응력 **−1.76 → −1.01 GPa (220일, 3.3 μm)**. 정방정 분율도 감소. 문헌 범위 단사정 1~2 GPa, 정방정 2~3 GPa.
- FE Set 1(관측 완화에 맞도록 금속 크립 피팅): 재현되나 "문헌의 산화 유발 변형보다 크립 변형률 속도가 한 자릿수 큼".
- FE Set 2(문헌 크립·수소 변형): −1.76 → −1.6 GPa로만 완화. "벌크 완화 기구(산화물 크립, 금속 크립, 수소 격자변형)는 관측 완화를 설명하기에 충분하지 않다 → 계면 거칠기 발달과 가로 균열".
- 학위논문 종합 가설(7장): 거칠기 발달과 국소 응력은 근표면 금속의 소성 변형에 의존, 기판 경화↑·산화막 파괴강도↓ → 계면 가로 균열층 → 응력 해방 → t→m 변태 → 나노균열 방사.
- 사용자 모델과의 접점: 계면 아래 고수소 금속의 크립이 문헌 벌크값보다 빠르면 Set 1 쪽으로 이동 가능(사용자 모델 ΔQ_H ≈ 0.06 eV@310 wppm → 360 °C에서 약 3배; 10배에는 부족). 금속은 "벌크 크립 완화"가 아니라 "계면 소성·경화"로 들어감.

### C4. 수소흡수율 f_H의 주기성 — 원문 확인 (Couet, Motta, Comstock, JNM 451 (2014) 1–13; PSU 공개 PDF)
- 360 °C 순수 18.7 MPa, ASTM G2. Zircaloy-4, ZIRLO, Zr-2.5Nb, Zr-2.5Nb-0.5Cu, 순Zr, 모델 합금.
- 총 흡수율: "전이 중간쯤부터 f_H가 꾸준히 증가해 전이까지 오르고, 전이 직전에 감소하는 듯 보인다. 이 변화가 다음 전이 구간에서 반복되어 수소흡수 운동학이 산화 운동학의 주기성을 따른다." "f_H는 한 전이 구간에서 다음 구간으로 갈수록 커진다."
- 순간 흡수율: "부식 속도가 높을 때 f_H는 낮고, 속도가 느려지면 f_H가 크게 증가. 모든 합금에서 관찰. 전이까지 계속 오르다 전이 직전 급락. 1차 전이 후 부식 속도가 다시 오르고 f_H는 초기 낮은 값으로 돌아간다."
- **저자 단서**: "전이 직전의 급락이 실제 물리 현상인지 피팅 함수의 오차인지 분명하지 않다." → 시험 항목에서는 "전이까지 상승·전이 후 재설정·주기마다 기준선 상승"만 사용.
- 메커니즘(초록): 전하 균형, 산화막 전자전도도가 핵심. 전전이 지수 n(Table 3): 순Zr 0.20, Zr-2.5Nb 0.37, ZIRLO 0.37~0.41, Zircaloy-4 0.29~0.32.

### C5. 수소화물에 의한 부식 가속 — 확인, 메커니즘 미결 (Ensor et al., JNM 496 (2017) 301–312; Bisor-Melloul, Tupin et al., RGN 2011; Tupin et al., Corros. Sci. 98 (2015) 478–493)
- Ensor: 사전 수소충전 없이 두께만 다른 Zircaloy-4 쿠폰(360 °C, 최대 2,800일)으로 수소량 차이 유도. "TSS를 넘은 수소 농도(수소화물 형성)가 가속 부식과 연관… TSS를 넘어갈수록 주기적 산화 전이가 더 일찍… 후전이 속도도 증가." 산화막 입자가 주상→등축, 진행된 산화 위치가 수소화물 위치와 상관.
- Ensor가 정리한 제안 기구 3개: ① 수소화물이 Zr 기지보다 빨리 산화 ② 수소 존재로 덜 보호적인 산화막 미세조직 ③ 수소화물이 계면 국소 응력을 바꿔 **주기 전이 빈도 증가**. 저자 가설: 국소 경화 → 응력 수용 불가 → 조기 전이 → 계면 요철·면적 증가.
- Kido 인용: "전전이 영역에서는 가속 없음".
- Bisor-Melloul·Tupin: 음극 충전 수소화물 림 시편, **전이 두께 약 1.5 μm (기준 2 μm)**, 운동학 k·n 상승(0.54, 0.38), 미세균열 밀도↑, 정방정 분율은 모든 깊이에서 기준보다 낮음, 계면에 Zr₃O 아산화물·ε-ZrH₂, 수소화물의 수소는 산화막으로 가지 않음. 고연소 phase III(>40 GWd/tU) 가속의 3가설(Sn, Zr(Fe,Cr)₂ 용해, 수소화물 림)은 "여전히 논쟁 중".
- 2026 Comm. Mater. 리뷰(Liu & Han): 사전 수소화 Zircaloy-4는 초기 수소량이 높을수록 산화 속도 증가, 기지-지르코니아 결맞음 상실로 해석(Kido).

### C6. 전이 두께의 온도 의존 — 확인 (Liao et al., Heliyon 10 (2024) e33266, 오픈액세스)
- 과열증기 390/416/427/455 °C, 10.3 MPa. N36·N2·N3(Zr-Sn-Nb)와 Zr-4.
- 전이 시간이 Arrhenius(처음 보고). Qt/R: N36 −13,681 K, N2 −13,553, N3 −13,054, Zr-4 −10,406 K. 전전이 Qa/R: Zr-4 13,700 K(Kass 13,640과 일치).
- 전이 무게증가 ΔW_T = 15·(A·t0)^(1/n)·exp(−(Qa+Qt)/nRT) → 온도와 함께 완만히 증가. **Zr-4 3.3 → 4.2 μm, N36 2.8 → 3.1 μm (390 → 455 °C).**
- 모델: 핵심 특징(t-ZrO₂ 입자 크기) Σ^α − Σ₀^α = ν·t가 임계값 Σc에 닿으면 전이. α = 2(포물선) 가정. Qν 86~114 kJ/mol ≈ t-ZrO₂ 내 산소 확산(81~110) → "입자 성장이 산소 확산 지배". 900~1000 °C breakaway까지 외삽해 대체로 일치.
- 저자 진술: "계면 미세균열의 원인, 곧 전이의 근본 기구는 여전히 논쟁 중."

### C7. Nb 합금 — 부분 확인
- Couet 2014: Zr-2.5Nb는 1차 전이만 추출됨(2차 미도달). Motta 2005: 리튬수에서 Zr-2.5Nb 주기 없음·가속. 2026 리뷰: 과량 Nb는 t/m 비와 압축응력을 줄임.

### C8. 완화 진동자/limit cycle 선행 부재 — 용어로는 부재, 비선형동역학 선행은 **존재**
- Google Scholar(사용자 크롬에서 직접 실행): `"zirconium" oxidation "relaxation oscillator"` → 전부 강유전체 HfZrO₂ 회로. `zirconium corrosion "limit cycle" oxide transition` → Gupta·Barber·Thouless·Lu PRE 2020 1건. `"nonlinear dynamics" OR "self-oscillation"` → 촉매·강유전체.
- **Gupta, Barber, Thouless, Lu, Phys. Rev. E 102, 012802 (2020)** 초록: 이동경계 Turing 계에서 "주기적·비주기적 성장률 영역이 얻어지고, 주기적 경우의 경향은 실험의 순환 경계 운동학과 놀라울 만큼 유사. 이동 전면 뒤에 정지한 주기 구조가 남는다."
- **Gupta 2021 미시간 박사논문** (deepblue hdl 2027.42/169636) 초록: ① 산화물 응력 모델 → 900 K 이하 산화물은 전위 활주로 변형, 기판 크립은 고온에서만 유의, "전이는 산화막의 거시적 파괴로 설명될 수 없다" ② t→m 변태 자유에너지 모델 → 응력은 변태 장벽에 거의 무영향, 결맞음 상실이 구동 ③ Turing 이동경계 모델 + 응력 의존 정방정상-기공 상호작용 모델로 주기 재현. "산화막 균열 가정 없이 제안된 최초의 수학 모델".
- **Gupta, Tripathi, Gorr, High Temp. Corros. Mater. 103:75 (2026)** (KITopen OA): "Hopf형 화학 불안정성과 Turing형 확산 불안정성이 탐색되었으나(참고 89~91) 이론적 화학·확산 불안정성 틀은 대체로 미검증." "주기적 층상 조직은 응력만으로 설명 불가하나, 얇은 기판에서 주기성 부재는 응력이 관련됨을 시사." t→m 주기성에 대해 지지 보고와 부재 보고 공존.

---

## 4. 세 경쟁 모델 (서로 양립 불가) — pptx 6장으로 도식화 완료

| | Platt (맨체스터, 2015) | Gupta (미시간, 2019~2021) | Liao (NPIC, 2024) |
|---|---|---|---|
| 느린 변수 | 계면 거칠기·미세균열 (근표면 금속 소성) | 반응-확산 종 농도 (정방정상·기공) | 계면 t-ZrO₂ 입자 크기 Σ |
| 문턱 | 가로 균열망 형성 (기판 경화↑, 파괴강도↓) | 없음 — Turing 패턴이 전면 속도 진동 | Σ = Σc |
| 응력의 역할 | 핵심: 균열·거칠기가 응력 해방 → t→m | 변태 장벽에 무시(상충) | 다루지 않음 |
| 균열 | 원인 | 불필요 | 결과 |
| 온도 의존 | 미정 | 미정 | 예측·실측 일치 |
| 리튬수 분기 | 미정(기공→파괴강도↓로 해석 가능) | 비주기 영역 존재 → 가능 | 다루지 않음 |
| 수소화물 | 경화 → 조기 균열(Ensor 가설과 일치) | 없음 | 없음(Σc 또는 ν의 수소 의존 필요) |
| f_H | 균열 = 전자 통로 | 기공 연결 | 미세균열 |

공통 초기 상태: 주상 m-ZrO₂, 계면 근처 준안정 t-ZrO₂, PBR 1.56 → 면내 압축 1~2 GPa, 두께 ∝ t^n (n≈0.3~0.4). 공통 결과: 균열·기공 띠가 남고 새 보호층 시작(층 두께 = 전이 두께).

### 4.1 문헌조사로 바뀐 견해 (중요)
1. 느린 변수는 "응력 축적"이 아니라 **"보호성의 소멸"**(응력은 주기 안에서 계속 풀림: −1.76 → −1.01 GPa). 진동자 구조는 남되 변수의 부호가 바뀜.
2. 금속은 벌크 크립 완화가 아니라 **계면 소성·경화**로 들어옴(Platt 7장, Ensor 가설).
3. 진동은 보편이 아니라 **한 영역의 해**(리튬수에서 폭주) → 분기 재현이 필수 시험.
4. 새로움의 크기를 낮춰 잡아야 함: 주기적 붕괴·재구축 서술(2004), 거칠기→균열→변태 연쇄(Platt), Turing 이동경계(Gupta)가 이미 있음. 남는 것은 **공통 데이터로의 판별**.

---

## 5. 리뷰·보고서 지형 (2026-10-08 조사) — "주기 전이 모델 리뷰"의 부재 확인

| 문헌 | 접근 | 전이·주기 모델 서술 | 파일 |
|---|---|---|---|
| Motta, Couet, Comstock, *Annu. Rev. Mater. Res.* 45 (2015) 311–343 | 저자 공개 PDF | 4.2절 전이: (a) 응력 축적→임계값에서 붕괴, 가로 균열이 기공 연결 (b) 기공 침투. "합금별 응력 축적률 차이의 원인 미규명". 6장 정량 모델 = C4(전전이 운동학+f_H; δ ∝ t^0.5 재현)만. 요약 5항: "주기적 산화막 성장이 깨지는 이유는 진행 중인 연구" | refs/Motta_Couet_Comstock_2015_…pdf |
| Tang, Liao, Yun, *Front. Mater.* 2024 (OA) | 전문 | t-m vs 기공, Parise 1998·Platt 2014 FE, C4, Qin 2006 임계 입자 크기(30 vs 90 nm 논쟁). "통일 기구 여부 추가 연구 필요" | URL: frontiersin.org/…/fmats.2024.1381818 |
| *JNST* 2022/2023 overview "Phenomenological aspects" | 크롬으로 본문 확인 | 주기 성장 도식 1개(보호층 형성·파괴의 교대). "수많은 연구에도 Zr 부식은 근본적 해석적 기술이 없다", "현대 수치 모델의 가능성·한계 평가의 예비 작업", 기계학습 제안 | URL: tandfonline.com/doi/full/10.1080/00223131.2022.2127954 |
| Gupta, Tripathi, Gorr, *HTCM* 103:75 (2026) | KITopen OA | Ti·Zr·Nb·Ta·W 공통: "직접 선형 breakaway / 주기 전이 후 선형 / 약한 과도 후 선형" 세 유형. 불안정성 틀 미검증 | refs/Gupta_Tripathi_Gorr_2026_…pdf |
| PENG Danmin 등, *Materials Reports* 40(2) (2026), DOI 10.11896/cldb.24120206 | 초록만 | "경험 모델 vs 기구 모델" 분류의 **모델 전용 리뷰**(중국어). PDF는 JS 링크라 미확보 | **사용자 브라우저로 PDF 확보 필요** |
| IAEA TECDOC-996 (1998), 316쪽 | OSTI PDF(스캔본) | 7장 노내 부식 모델링: 7.2 계면온도, 7.3 반경험 모델(PWR), 7.4 기구 모델, 7.5 요약. 텍스트 추출 불가 → 수동 열람 | refs/IAEA_TECDOC-996_…pdf |
| ANT ZIRAT12 STR 2007 "Corrosion Mechanisms" | 1장 샘플만 | 미해결 질문: "왜 고압수·증기에서는 부식이 주기적인가(장벽을 통한 음이온 확산 지배?)" | refs/ANT_ZIRAT12_…SAMPLE_ch1.pdf |
| BISON 피복관 부식 모델 문서(INL) | 크롬으로 확인 | 입방 → 선형, **전이 두께 2 μm 고정**(Ritchie 1998, EPRI-KWU-CE). 주기 미표현 | URL: mooseframework.inl.gov/bison/theory/cladding_corrosion_model.html |
| EPRI PFCC TR-105387 (1995) | 미확보 | 공학 경험식 | – |
| Yardley 2017 옥스퍼드 DPhil | ORA OA, 확보 | 문헌절: 응력 완화(기판 크립)와 기공 기반 전이. 실험: 두께가 전이의 예측변수, 전이 후 기존 산화막 전체 다공화, 전이 후 압축응력 급락 | refs/Yardley_2017_…pdf |
| Ensor 2016 PSU PhD "The nature of unstable oxide growth" | 미확보 | – | PSU etda |
| Platt EngD thesis (맨체스터) | Pure 포털로 확보(319쪽) | Proposed Paper 1~5, 7장 종합 가설 | refs/Platt_EngD_thesis_…pdf |
| Gupta 2021 미시간 PhD | 초록만(PDF 봇 차단) | 위 C8 | deepblue hdl 2027.42/169636 |

### 5.1 개별 모델 목록 (리뷰·벤치마크 대상)
1. Garzarolli 1991 ASTM STP: 장벽층 개념, 임계 두께에서 다공화.
2. Bryner 1979 JNM: "The cyclic nature of corrosion of Zircaloy-4 in 633 K water" (주기 현상 최초 명명).
3. Motta 2004~2015: 응력 축적·붕괴 + 기공 연결(정성).
4. Couet 2014~2015: C4(coupled current charge compensation) 모델 — 전전이 운동학·f_H; 전이는 외생.
5. Parise 1998, Platt 2014~2015: FE 응력·완화 → 균열·거칠기(한 주기).
6. Gupta 2019 *J. Thermal Stresses*, 2020 PRE, 2021 PhD: 응력 모델 + Turing/상-기공(주기 내장).
7. Aryanfar, Goddard, Marian, *Corros. Sci.* 2019 (arXiv 1904.03344, 확보): 침투(cellular automata, Dijkstra 확장) + 압축 항복 기준으로 전이 두께 범위(항복 1.2~5.2 GPa, K 72~212 GPa).
8. Liao 2024 Heliyon: t-ZrO₂ 임계 크기 문턱, Arrhenius 전이 시간.
9. Qin 2006: t→m 임계 입자 크기 열역학.
10. 위상장: npj Mater. Degrad. 2020(응력-산화 결합), 2024 Zr-2.5Sn(입방 법칙 재현) — 주기 미취급.
11. 공학 경험식: EPRI PFCC, MATPRO, BISON(Ritchie 1998).

---

## 6. 판별에 쓸 공통 데이터 (숫자 정리)

| 관측 | 값 | 출처 |
|---|---|---|
| 1차 전이 두께 (360 °C 순수) | Zry-4 1.5~2.6, ZIRLO 2.3~3.1, Zr-2.5Nb 2.4~3.5 μm | Yilmazbayhan 2004 T2, Couet 2014 T4, Motta 2005 T3 |
| 층 주기 | Zry-4 1.82~1.87, ZIRLO 2.0~2.3, Zr-2.5Nb 2.5~3.1 μm | 동일 |
| 후전이 속도 | 0.58 / 0.33 / 0.21 / 0.14 mg/dm²/d | Yilmazbayhan 2004 T2 |
| 2차/1차 전이 두께 | 4.5/2.1, 4.9/2.6, 5.7/2.9 | Couet 2014 T4 |
| 전전이 지수 n | 0.20(순Zr) ~ 0.41(ZIRLO) | Couet 2014 T3 |
| 전이 두께 온도 의존 (증기 10.3 MPa) | Zr-4 3.3→4.2, N36 2.8→3.1 μm (390→455 °C) | Liao 2024 |
| 전이 시간 Arrhenius Qt/R | −10,406 K (Zr-4) ~ −13,681 K (N36) | Liao 2024 T3 |
| 산화막 응력 | −1.76 → −1.01 GPa (220일, 3.3 μm) | Platt 2015 |
| 리튬수(70 ppm Li) | Zry-4·Zr-2.5Nb 주기 소멸, 후전이 2.02 / 84.6 mg/dm²/d | Motta 2005 T3 |
| 수소화물 림 | 전이 두께 2 → 1.5 μm, k 0.54, n 0.38 | Bisor-Melloul 2011 |
| 수소 TSS 초과 | 2차 전이부터 조기화, 후전이 속도↑ | Ensor 2017 Fig. 9–10 |
| f_H | 전이까지 상승, 전이 후 재설정, 주기마다 기준선↑ | Couet 2014 Fig. 8, 11 |

---

## 7. 한계·주의 사항

- 전이 두께 값이 측정법(무게증가 외삽 vs 단면 관찰)과 연구실에 따라 ±0.5 μm 흩어짐. 벤치마크는 동일 조건 데이터 묶음 단위로 해야 함.
- Platt의 "기판 크립 기여 작음"은 **문헌 벌크 크립률 기준**의 조건부 결론. 계면 근처 고수소 금속은 다를 수 있음(사용자 모델 접점).
- Couet의 f_H 전이 직전 급락은 저자도 피팅 오차 가능성 명시 → 시험 항목에서 제외.
- Gupta 모델은 "균열 불필요"를 주장하지만 리튬수·수소화물·f_H에 대한 명시적 예측이 아직 없음. Gupta 학위논문 PDF 미확보.
- IAEA TECDOC-996은 스캔본이라 모델 장(7.3~7.5)을 수동으로 읽어야 함.
- 완화 진동자 정식화는 "새 물리"가 아니라 정식화 수준이며, 사용자 지시로 보류 중.

---

## 8. 다음 단계

### 8.1 즉시 (리뷰 논문 정밀 조사 — 사용자가 다음 세션에서 파고들 부분)
1. **Motta 2015 리뷰 4.2절·6장 정독**: 전이 기구 (a)(b)의 근거 문헌(67–77, 111–113)을 추적해 각 기구가 어떤 측정에 기대는지 표로 정리. C4 모델의 가정(산소 공공 전하 상태, 전기장)과 전이와의 분리 방식 확인.
2. **Materials Reports 2026(PENG 등) PDF 확보 후 정독**: 경험 모델/기구 모델 분류와 "개선 방향"에 주기 모델이 포함되는지. 중국어 → 번역 필요.
3. **Gupta 2026 HTCM 리뷰 전문 정독**(확보됨): 참고 89~91(Salazar·Lallemant 1994 비선형성, Lallemant 1987 Ti-Zr 화학 쌍안정, Gupta 2020)과 "Proposed Unifying Breakaway Factors" 절. Zr 전용 주장과 범금속 주장을 분리.
4. **IAEA TECDOC-996 7장 수동 열람**: 1998년의 반경험·기구 모델 목록을 5.1 목록과 대조해 누락 보완(ABB Atom 모델, 초기 EPRI 모델 등).
5. **Yardley 2017 문헌절(2장)** 정독: 응력 완화·기공 모델의 당시 평가.
6. 미확보 자료 확보: Ensor 2016 PSU PhD, Gupta 2021 PDF(사용자 브라우저로 deepblue 다운로드), Tupin 2015 Corros. Sci. 원문(기관 인증), Cox 2005 JNM, Bryner 1979 JNM, Garzarolli 1991 ASTM.

### 8.2 중기 (판별 벤치마크)
7. 6절 공통 데이터를 CSV로 정리(조건·합금·측정법 태그 포함).
8. 모델별 파이썬 구현: Liao 문턱 모델(해석적), Aryanfar 침투·항복 기준(식 재현), Platt FE의 축약판(거칠기 성장률 + 파괴 기준), Gupta 1차원 이동경계 Turing 모델(논문 방정식 재현). 각 모델이 전이 두께 1.5~2.9 μm와 온도 의존 3.3→4.2 μm를 동시에 내놓는지 확인.
9. 판별표(pptx 6장)의 노랑 칸(미정)을 계산 결과로 채움. 리튬수 분기·수소화물·f_H까지 확장.

### 8.3 장기 (보류 중, 재논의 필요)
10. 완화 진동자/limit cycle 정식화 및 사용자 수소크립 모델의 계면 경화 항 결합(수소화물 가속의 기구 판별).

---

## 9. 산출물·파일 목록

- `Cowork\Zr_oxide_oscillator\(2026.10.08) - Zr 산화막 주기 전이 세 모델 도식.pptx` (6장: 연구 목표 / 공통 초기상태·분기·전이 직후 / Platt / Gupta / Liao / 판별표). 빌드 `build_zr_oxide_deck.py`, 렌더 검증 `render_pptx.py`(PowerPoint COM).
- `refs\` (22개): Yilmazbayhan 2004, Motta 2005, Bisor-Melloul·Tupin 2011, Couet 2014, Ensor 2017 (PSU 저자 공개), Platt EngD thesis (Manchester Pure), Yardley 2017 (Oxford ORA), Gupta·Tripathi·Gorr 2026 (KITopen), Motta·Couet·Comstock 2015 (PSU), IAEA TECDOC-996 (OSTI), ANT ZIRAT12 1장 샘플, Aryanfar 2019 (arXiv), Chalmers BWR PIE 보고서. 각 PDF 옆 `_text.txt`는 PyMuPDF 추출본.
- Th-229 줄기(별도): `Cowork\Th229_nuclear_clock\(2026.10.06) - Th-229 핵시계 모식도.pptx` (8장) 및 원자배열 그림.

## 10. 오픈액세스 URL (클라우드 세션용)
- Motta 2015 리뷰: https://www.nuce.psu.edu/Motta/Publications/124_Motta_ARoMR_2015.pdf
- Couet 2014: https://www.nuce.psu.edu/motta/Publications/112_Couet_JNM_2014.pdf
- Yilmazbayhan 2004: https://www.nuce.psu.edu/motta/Publications/2004_Yilmazbayhan_JNM.pdf
- Motta 2005 JASTMI: https://www.nuce.psu.edu/motta/Publications/2005_Motta_JASTMI.pdf
- Ensor 2017: https://www.nuce.psu.edu/motta/Publications/148_Ensor_JNM_2017.pdf
- Bisor-Melloul 2011: https://www.nuce.psu.edu/Motta/Publications/2011_Bisor-Melloul_RGN.pdf
- Platt thesis: https://pure.manchester.ac.uk/ws/portalfiles/portal/54552151/FULL_TEXT.PDF (research.manchester.ac.uk 쪽은 Cloudflare 차단)
- Yardley thesis: https://ora.ox.ac.uk/objects/uuid:bb4776ae-60f7-49f1-b93f-9d1542e79431
- Gupta 2021 thesis: https://deepblue.lib.umich.edu/items/460712d6-0602-4ba5-bde4-6ebf758a2203 (PDF는 브라우저로)
- Gupta 2020 PRE: https://doi.org/10.1103/PhysRevE.102.012802 (초록 공개)
- Gupta 2026 리뷰: https://publikationen.bibliothek.kit.edu/1000195894/186542640
- Liao 2024 Heliyon: https://www.cell.com/heliyon/fulltext/S2405-8440(24)09297-1
- Liu & Han 2026 Comm. Mater.: https://www.nature.com/articles/s43246-026-01201-1
- Tang·Liao·Yun 2024 Front. Mater.: https://www.frontiersin.org/journals/materials/articles/10.3389/fmats.2024.1381818/full
- Aryanfar 2019: https://arxiv.org/abs/1904.03344
- IAEA TECDOC-996: https://www.osti.gov/etdeweb/servlets/purl/20010506
- BISON 부식 모델: https://mooseframework.inl.gov/bison/theory/cladding_corrosion_model.html
- Materials Reports 2026: https://www.mater-rep.com/EN/Y2026/V40/I2/24120206
