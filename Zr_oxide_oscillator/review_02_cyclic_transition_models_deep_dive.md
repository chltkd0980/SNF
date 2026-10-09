# Zr 합금 산화막 주기 전이 모델 리뷰 — 심화 조사 (rev.2)

- 작성일: 2026-10-09
- 선행 문서: `SNF_Zr_oxide_transition_research_notes.md` (rev.1, 2026-10-09). 이 문서는 rev.1의 5절(리뷰 지형)·5.1절(모델 목록)·6절(판별 데이터)을 확장한다. rev.1과 겹치는 내용은 반복하지 않는다.
- 목적: 사용자 지시(2026-10-08) "주기성을 반영한 기존 산화막 모델 리뷰"를 더 깊게. 세 모델(맨체스터 Platt / 미시간 Gupta / NPIC Liao) 외의 일반 산화막 모델과 주기 전이 모델, 리뷰·보고서를 넓게 훑어 **모델 목록을 닫는 것**이 1차 목표.

---

## 0. 이번 세션의 조건과 근거 등급

클라우드 세션의 네트워크 정책 때문에 외부 PDF·웹페이지 전문을 받을 수 없었다(psu.edu, kit.edu, arxiv.org 등 전부 차단). 가능한 것은 웹 검색(초록·색인 수준)뿐이었다. 따라서 이 문서의 모든 항목에 근거 등급을 붙인다.

| 등급 | 뜻 |
|---|---|
| **[원문]** | 이전 세션(로컬)에서 1차 출처 PDF로 직접 확인한 내용 (rev.1 C1~C8) |
| **[초록]** | 출판사·리포지토리의 초록 또는 하이라이트 문구로 확인 |
| **[요약]** | 검색 엔진이 합성한 요약. 인용 가능 수준이 아님. 원문 확인 필요 |

전문 확보 경로는 9절에 정리했다. **이 문서의 결론은 [초록]·[요약] 수준의 신규 항목이 많으므로, 원문 확보 후 수정될 수 있다.**

---

## 1. 한 줄 요약

모델 목록이 rev.1의 11개에서 **8개 계열·약 25개 항목**으로 확장되었다. 특히 (i) 1970년 Bradhurst·Heuer의 **주기 입방근(cyclic cube-root) 모델**이 "주기 전이 정량 모델"의 시초이고, (ii) El Kadiri 2013(Acta Mater.)의 **응력 부호 반전 모델**은 Platt와 정반대 부호(t→m 변태가 전이를 지연시킨다)를 주장하는 **네 번째 경쟁 모델**이며, (iii) Harada·Wakamatsu 2008/2009는 **Ar/O₂ 가스 분위기에서도 주기 전이와 f_H 주기성이 나타난다**고 보고하여, 전이 기구가 물·전기화학에 특이적이지 않다는 강한 경계 조건을 준다. 전이 기구 전용 리뷰(Li 외, JNM 2026)가 하나 더 존재하지만 ML 응용에 비중을 두고 있고, **주기 전이 모델을 공통 데이터로 비교한 문헌은 여전히 없다.**

---

## 2. 리뷰·개관 지형 업데이트

rev.1 5절의 표에 아래를 추가·수정한다.

| 문헌 | 근거 | 전이·주기 모델 서술 | 비고 |
|---|---|---|---|
| **Li Weiyang, Li Weicai, Hu Jing, Liu Pengliang, Shi Haoyu, Yu Jiyang, *J. Nucl. Mater.* 619 (2026) 156217** (온라인 2025), doi 10.1016/j.jnucmat.2025.156217 | [초록] | 제목이 "corrosion transition mechanisms"인 **전이 기구 전용 리뷰**. 범위: 전이의 운동학·열역학 구동력, t→m 변태, 산화막 응력 축적, ML(회귀·딥러닝·PINN) 적용, 기술적 난제. 전이 임계 두께 약 2~3 μm로 서술. "전이를 지배하는 기본 기구는 여전히 완전히 이해되지 않음" | **rev.1 지형에 빠져 있던 가장 가까운 리뷰.** 주기(2차 이후 전이)를 다루는지는 초록으로 알 수 없음. ScienceDirect 유료 → 기관 인증 필요 |
| Stoll U., Slavinskaya N., *J. Nucl. Sci. Technol.* 60(5) (2023) 573–602, doi 10.1080/00223131.2022.2127954 | [초록]+이전 세션 본문 열람 | rev.1의 "JNST 2022/2023 overview". 저자 확정. Zr1Nb는 전이 1회(396일, Zry-4는 183일), 수직 균열 없이 더 얇은 산화막 | 저자명 확정으로 인용 가능 |
| **PENG Danmin(彭丹珉), SUN Zhipeng(孙志鹏) 외, 中国核动力研究设计院, 《锆合金均匀腐蚀模型研究进展》 *Materials Reports* 40(2) (2026) 24120206**, 영문 제목 "The Research Progress of Zirconium Alloy Uniform Corrosion Mechanism Models" | [초록] | 경험 모델(데이터 피팅) vs 기구 모델(미시 기구) 분류, 장단점 비교, 개선 방향 제안. 키워드: 包壳材料, 腐蚀模型, 氧化动力学 | 제목·저자 확정. NPIC(Liao와 같은 기관) 소속 → Liao 2024 모델이 어떻게 자리매김되는지 볼 수 있음. 중국어 PDF는 사용자 브라우저로 확보 필요 |
| Allen T.R., Konings R.J.M., Motta A.T., "5.03 Corrosion of Zirconium Alloys", *Comprehensive Nuclear Materials* vol. 5 (2012) 49–68; 2020년 2판 재수록 | [초록] | 균일 산화 기구 절 포함. 전이 서술 내용은 미확인 | PSU 저자 공개 PDF(`2012_Allen_CNM.pdf`) 존재 |
| Motta A.T., *JOM* 63 (2011) "Waterside corrosion in zirconium alloys" | [초록] | 전전이·전이·breakaway 단계 구분 | PSU 공개 PDF |
| ASM Handbook vol. 13B "Corrosion of Zirconium and Zirconium Alloys" | 미확인 | 공학 개관 | 참고용 |
| INIS "Review of theoretical conceptions on regimes of oxidation and hydrogen pickup in Zr-alloys" | 미확인 | 제목상 이론 모델 리뷰(러시아권으로 추정) | **확인 필요**: 주기 모델 리뷰일 가능성 |
| Zhang 외, *Nucl. Eng. Technol.* (2025) neural ODE 피복관 부식 모델 | [초록] | 반경험 모델로 사전학습 후 실측으로 미세조정. "기존 반경험 모델이 실측과 눈에 띄게 어긋남" | ML 계열 |

**판정 유지**: 전이 기구 리뷰(Motta 2015, Tang 2024, Stoll 2023, Li 2026, Gupta 2026)와 모델 리뷰(PENG 2026)는 있으나, **주기 전이를 내장한 모델들만 골라 같은 실측으로 비교한 리뷰는 없다.** Li 2026이 ML에 비중을 두는 점, PENG 2026이 "균일 부식 모델" 일반을 다루는 점이 그 증거이며, 두 문헌의 원문으로 최종 확인해야 한다.

---

## 3. 모델 목록 확장 — 8개 계열

rev.1 5.1절의 11개 항목을 계열별로 재배치하고 신규 항목을 추가했다. ★는 이번 세션 신규.

### A. 장벽층·주기 경험 모델 (현상론)
1. ★ **Bradhurst D.H., Heuer P.M., *J. Nucl. Mater.* 37 (1970) "The influence of oxide stress on the breakaway oxidation of Zircaloy-2"** [요약]: **주기 입방근 모델**. 계면에서 새 보호층이 임계 두께까지 성장 → 보호성 상실 → 반복. 후전이 속도 = f(입방근 속도상수, 평균 산화막 밀도, 임계 두께). 응력 지배 기구를 제안. → **"주기 전이 정량 모델"의 출발점**. Kass·Hillner의 입방→선형 모델과 함께 공학 경험식의 뿌리.
2. Bryner J.S., *J. Nucl. Mater.* 82 (1979) "The cyclic nature of corrosion of Zircaloy-4 in 633 K water" [요약]: 각 주기에 장벽 산화물 층이 교대로 형성, 전이 횟수 = 층 수.
3. Garzarolli F., Seidel H., Tricot R., Gros J.P., ASTM STP 1132 (1991) 395 "Oxide growth mechanism in zirconium alloys" [색인]: 장벽층 개념.
4. ★ **Beie H.-J., Mitwalsky A., Garzarolli F., Ruhmann H., Sell H.-J., ASTM STP 1245 (1994) 615–643 "Examinations of the corrosion mechanism of zirconium alloys"** [초록]: 온도 변동 장기 시험에서 **장벽층의 주기적 형성에 의한 기억 효과(memory effect)** 관측. "Zr 합금 부식은 장벽층 지배 과정". 계면에 치밀·무공극층, 리튬수에서는 입계 미세기공 망과 Li 농축, 산화막 압축응력이 기존 보고보다 훨씬 큼.
5. ★ Hillner E., Franklin D.G., Smee J.D., *J. Nucl. Mater.* 278 (2000) 334 "Long-term corrosion of Zircaloy before and after irradiation" [색인]: 초장기 오토클레이브 데이터(다중 전이 포함 추정). 벤치마크 데이터 후보.
6. 공학 경험식: EPRI PFCC TR-105387, MATPRO, BISON(Ritchie 1998; 전이 두께 2 μm 고정) [원문: BISON 문서].

### B. 응력 축적 → 균열·거칠기 모델
7. ★ Roy C., Burgess B., *Oxid. Met.* 2 (1970) "A study of the stresses generated in zirconia films during the oxidation of zirconium alloys" [요약]: 얇은 막에서 5~7×10⁵ psi(약 3.4~4.8 GPa) → **약 3.5 μm에서 1×10⁵ psi로 급락, 이 두께가 전이 두께와 일치.** 응력-전이 상관의 최초 실측 중 하나. 단, 다른 1970년대 측정(500 °C 건조 산소)은 "응력 측정만으로 인과를 말할 수 없다"고 명시.
8. ★ **Parise M., Foerch R., Cailletaud G., *J. Phys. IV* 9 (1999) Pr9-311** (+ Parise 1998 *J. Nucl. Mater.* 256 FE 모델) [초록]: 300~450 °C. 국소 응력장과 균열을 설명하려면 계면 요철 기하가 필요. **요철의 기원을 지르코니아 입계 확산의 불균일성에 의한 자기조직화(self-organization)로 모델링** → Platt의 "거칠기" 변수에 발생 기구를 제공하는 선행. 
9. Platt P. 외, *J. Nucl. Mater.* 456 (2015) 415; Platt EngD thesis (Manchester) [원문]: rev.1 C3.
10. ★ Polatidis E. 외(Preuss 그룹), *J. Nucl. Mater.* 432 (2013) 102–112 [초록]: 에너지분산 싱크로트론 XRD, Zircaloy-4 360 °C. 후전이(220일) 시편에서 단사정 응력이 두께 방향으로 크게 변하고 계면 근처에서 최대 압축. **응력 불연속이 전자현미경으로 본 두 산화층 경계와 일치.** 전이 전·중에 정방정 총량 변화.
11. ★ Garner A. 외, *J. Nucl. Mater.* 479 (2016) "The measurement of stress and phase fraction distributions in pre and post-transition Zircaloy oxides using nano-beam synchrotron X-ray diffraction" [색인]: 나노빔. 내용 미확인(검색 요약이 Gupta 논문과 섞여 있어 폐기).
12. ★ Tejland P., Andrén H.-O., *J. Nucl. Mater.* 430 (2012) 64–71 "Origin and effect of lateral cracks in oxide scales formed on zirconium alloys" [초록]: Zircaloy-2 증기 오토클레이브. **계면 근처 산화막의 국소 인장응력이 구동력, 미산화 제2상 입자(SPP)가 균열 개시점.** 균열 수 ∝ SPP 수. → 가로 균열의 "씨앗"을 SPP로 특정. 같은 그룹: 산화 중 금속의 국소 크립 변형 보고.
13. ★ IRSN, "Modelling of corrosion induced stresses during Zircaloy-4 oxidation in air" [초록]: 공기 산화에서 물결 계면과 **두께 방향으로 주기적으로 분포한 짧은 원주 균열**을 FE로 모델링.

### C. ★ 응력 부호 반전 모델 (네 번째 경쟁 모델)
14. ★ **El Kadiri H. 외(Mississippi State·INL·Missouri S&T·Georgia Tech), *Acta Mater.* 61(11) (2013) 3923–3935, doi 10.1016/j.actamat.2013.02.052, "Transformations and cracks in zirconia films leading to breakaway oxidation of Zircaloy"** [초록]: Raman·AFM·광학현미경. **breakaway는 산화막 원주 응력이 압축→인장으로 부호가 바뀔 때 발생**, 균열이 표면→계면 방향으로 성장. 부호 반전은 임계 두께에서 일어나며 그 두께는 계면 원주 응력에 의존. **t→m 변태는 격자 팽창으로 계면 압축을 보태므로 부호 반전을 지연 → 전이를 늦추는 유익한 역할**(Platt·Motta의 "t→m가 전이의 결과/원인"과 부호가 반대). Scholars Mine(Missouri S&T)에 OA 사본 있음.
    - 동반 논문: Mamivand M., Asle Zaeem M., El Kadiri H., TMS 2013 "Phase field modeling of tetragonal to monoclinic phase transformation at zirconium oxide" [초록]: 변태가 계면 근처 응력 상태를 바꾸고 그 진폭이 산화 운동학을 크게 바꾼다 → 계열 D의 위상장 모델로 연결.

### D. t→m 변태·입자 크기 문턱 모델
15. Qin W. 외 2006: t→m 임계 입자 크기 열역학(30 vs 90 nm 논쟁) [rev.1].
16. ★ Mamivand M., Asle Zaeem M., El Kadiri H., *Acta Mater.* 61 (2013) 5223–5235; *Acta Mater.* 64 (2014) 208–219; Mamivand PhD (MSU 2014) [초록]: 지르코니아 t→m 마르텐사이트 변태의 위상장 모델. 쌍정 "V"형, 표면 "gable roof" 융기, 응력 유도 변태, 변태 강화. **Zr 산화막에 적용 가능한 유일한 t→m 위상장 틀**이나 산화 성장·주기와 직접 결합은 안 됨.
17. ★ Ensor B. 외, *J. Nucl. Mater.* 2019 (PSU 166) [초록]: 274~427 °C 산화막의 정방정 분율–응력 관계. **계면에서 멀어지며 임계 크기를 넘은 정방정 입자가 단사정으로 변태.** → Liao 2024의 "계면 t-ZrO₂ 입자 크기 Σ" 변수에 PSU 측 실측 근거.
18. ★ NPIC 계열 선행, *J. Nucl. Mater.* (2020) "Critical behavior of interfacial t-ZrO₂ and other oxide features of zirconium alloy reaching critical transition condition" (Zr-0.5Sn-0.15Nb-0.5Fe-0.2V, 400 °C 증기) [요약]: 전이 직전 정방정 평균 응력이 갑자기 떨어지며 "원인 미설명". 응력 축적과 t→m를 후보 트리거로 제시. → Liao 2024 모델의 실험적 모태.
19. Liao Y. 외, *Heliyon* 10 (2024) e33266 [원문]: rev.1 C6.
20. Gupta I. PhD(2021) 2부 [초록]: 응력이 변태 장벽에 거의 무영향, **결맞음 상실(loss of coherency)**이 구동.

### E. 기공 발달·침투 모델
21. ★ Preuss M., Frankel P., Lozano-Perez S., Grovenor C., Ni N. 외, *J. ASTM Int.* 8(9) (2011) [초록]: ZIRLO, Fresnel 대비 TEM으로 주상 입계 나노기공 확인, **전이 통과 후 연결망 형성**, in situ EIS로 전이 중 기공 발달 확인. 3DAP로 ZrO 아산화물 3차원 형상.
22. ★ Hu J. 외(Oxford), *Acta Mater.* (2019) [초록]: Fresnel 영상으로 세 시편의 기공 연결성 비교. 후전이 급속 산화 합금에서 입자 구조가 무질서하고 나노기공망이 더 발달(Zr-1Nb·Zr-2.5Nb 중수소 시험). "연결 기공이 수소종 수송의 지배 경로".
23. Aryanfar A., Goddard W., Marian J., *Corros. Sci.* 158 (2019) [원문]: 침투 CA + 압축 항복.
24. Yardley S. 2017 DPhil (Oxford) [원문]: 두께가 전이 예측변수, 전이 후 전체 다공화.
25. Beie 1994 [초록]: 리튬수 입계 기공망(계열 A와 겹침).

### F. 반응-확산·비선형동역학 모델
26. Gupta I., Barber J.R., Thouless M.D., Lu W., *Phys. Rev. E* 102 (2020) 012802 [초록]; Gupta 2021 PhD 3부 [초록]: Turing 이동경계. ("*J. Thermal Stresses* 2019" 논문은 이번 검색으로 확인 못 함 → rev.1 5.1의 해당 항목은 **미확인**으로 강등.)
27. ★ Lallemant M. 외(Dijon), 1980년대: **Ti-Zr 합금 고온 산화에서 진동(oscillation) 관측**. arXiv 2107.05867(2021 리뷰, ref. [17]) 요약 [요약]: 적정 온도창에서 표면 온도가 진동하고 2상 층상 생성물이 성장. 제안 기구 두 가지 — (a) 흡열 산화 단계가 계면 조성을 바꿔 반응을 늦추는 **열 피드백**, (b) 계면 응력 축적이 금속 수송을 막는 **역학적 차단**. "기구는 아직 완전히 이해되지 않음". Gupta 2026 리뷰의 ref. 89~91이 이 계열. → 사용자가 보류한 "완화 진동자" 발상의 직접 선행이므로, 추후 재논의 시 1차 출처 확보 필수(정확한 서지 미확정).
28. Parise 1999의 입계 확산 자기조직화(계열 B 8번) — 계면 요철의 주기성을 만드는 Mullins–Sekerka형 불안정으로 읽을 수 있음.

### G. 전기화학·전하 모델
29. Couet A., Motta A.T., Ambard A., *Corros. Sci.* 100 (2015) 73–84 (C4 Part I, 포물선 산화; PSU 131) [초록]; Couet 2017 *Corros. Sci.* (in situ EIS, PSU 137) [색인]. 전이는 외생.
30. ★ Vermoyal J.J., Frichet A., Dessemond L., Hammou A., *Electrochim. Acta* 45 (1999) 1039; *J. Nucl. Mater.* 288 (2001) 297 (Zircaloy-4 500 °C 건조 공기 in situ); *Electrochim. Acta* 47 (2002) 2679 (Zr-1Nb-O 수중 산화막) [색인]; Barberis P., Frichet A., *J. Nucl. Mater.* 273 (1999) 182 [색인]: 임피던스로 본 산화막 전기 특성. 전이 모델 포함 여부 미확인.
31. ★ Harada M., Wakamatsu R.(Kobe Special Tube·Zirco Products), *J. ASTM Int.* 5(3) (2008) / ASTM STP 1505 (2009) STP48146S "The effect of hydrogen on the transition behavior of the corrosion rate of zirconium alloys" [초록]: 모델 논문은 아니지만 **f_H 주기성 + 가스 분위기 주기성**의 독립 보고(4절 참조).

### H. 새 수치 틀 (주기 미취급이나 확장 후보)
32. npj Mater. Degrad. 4 (2020) "Mechanical–chemical coupling phase-field modeling for inhomogeneous oxidation of zirconium induced by stress–oxidation interaction" [초록]: 계면 거칠기 발달·거칠기 의존 성장률·조기 균열 핵생성 위치.
33. 위상장 Zr-2.5Sn 고온 부식(2024) [초록]: 입방 법칙 재현.
34. ★ **Lea S.L.M., Haynes T.A., Wenman M.R., *Nuclear Future* 20(3) (2024) 57–62 "Peridynamic modelling of zirconium oxidation to gain mechanistic understanding"** (MIDAS 프로그램, Imperial 배경) [초록]: **peridynamics**(비국소, 균열 경로 사전 지정 불필요)로 산화+균열 모델. 입력: 산소 확산계수, 산화막 파괴 변형률, 상별 산소 농도·팽창. 산화막 두께·계면 거칠기·균열 패턴을 실험과 비교. → Platt형 "거칠기→균열" 연쇄를 균열 가정 없이 자연 발생시킬 수 있는 틀. 주기 재현 여부 미확인.
35. ★ ML 계열: Li 2026 JNM(회귀·DL·PINN 제안), Zhang 2025 NET(neural ODE), 中国原子能科学技术 2023(XGBoost, R²=0.996). 주기 모델은 아니며 벤치마크의 "기준선"으로만 사용.

### I. 불안정 산화 성장(nodular·입계 침투) — 주기와 구별해야 할 현상
36. ★ Ensor B., Motta A.T. 외, *J. Nucl. Mater.* 558 (2022) (PSU 181) [초록]: 결정봉 Zr·스펀지 Zr·모델 합금(Sn, Fe, Cr 소량) 360 °C 70일. **합금 원소의 불균일 분포가 불안정 산화 성장(nodule형, 입계 침투, 입자별 차등 성장)을 일으켜 breakaway**. "예비적, 추가 연구 필요".
37. ★ Ensor B. 외, ASTM STP (2021) "Investigation of breakaway corrosion observed during oxide growth" (PSU 177) [색인].
    - 판별 의미: 순Zr·저합금의 "breakaway"는 **주기 전이와 다른 현상**(불균일 성장)이다. 리뷰에서 두 현상을 분리해야 하며, Gupta 2026의 "직접 선형 breakaway / 주기 전이 후 선형 / 약한 과도 후 선형" 세 유형 분류와 대응시킬 수 있다.

---

## 4. 새로 확인된 경계 조건·판별 데이터

rev.1 6절 표에 추가할 관측. 모델이 재현해야 할 "시험 문항"이 늘어났다.

| # | 관측 | 값·내용 | 출처 | 근거 | 판별 의미 |
|---|---|---|---|---|---|
| N1 | **가스 분위기 주기성** | Zry-4·Zry-2·NDA, 633 K, 순수와 Ar+O₂ 혼합가스 **양쪽에서 부식 속도가 주기적으로 변동**. 전이 시간·무게증가는 합금 내식성에 따라 변화 | Harada & Wakamatsu 2008 JAI / STP 1505 | [초록] | 주기 전이는 수용액·전기화학(수소 발생, Li) 특이 현상이 아님. **순수 산소 수송·역학으로 설명되어야 함.** C4(전하 균형) 단독으로는 부족 |
| N2 | **f_H 주기성 독립 확인** | 순수 600 h 주기 × 12회(7200 h). 주기별 수소흡수율이 일정하지 않고 **주기적으로 변동** | 동일 | [초록] | rev.1 C4(Couet 2014)의 f_H 주기성이 다른 그룹·다른 방법으로 재현됨. 시험 항목 신뢰도 상승 |
| N3 | **노내 주기성** | >70 GWd/MTU 고내식 합금 피복관: 계면의 무특징 치밀 하층 위에 **미세 원주 균열을 가진 부층(sub-layer)들이 쌓여 있고 이는 주기 부식 전이와 연관**. 부층 수는 중간 내식성 합금에서 많고 고내식성에서 적음. **이 층상 구조는 오토클레이브에서는 보이지 않음.** 부분 박리(OSP)는 펠릿 접촉 인장 응력의 방사 균열과 연관 | Westinghouse(Pan 외), ASTM STP 1543 (2013) STP154320130005 | [초록] | 주기성이 노내에서도 존재. 부층 수 ∝ 1/내식성은 "층 두께 ∝ 1/후전이 속도"(C1)와 정합. "오토클레이브에서 안 보임"은 노내 산화막 구조가 다름을 뜻하므로 모델 외삽의 한계 조건 |
| N4 | **초기 응력 급락** | 얇은 막 5~7×10⁵ psi → 약 3.5 μm에서 1×10⁵ psi, 이 두께가 전이 두께 | Roy & Burgess 1970 | [요약] | Platt 2015의 −1.76→−1.01 GPa 완화와 같은 방향. 1970년대부터 알려진 사실 |
| N5 | **층 경계의 응력 불연속** | 후전이 Zircaloy-4(220일): 단사정 응력의 두께 방향 불연속이 두 산화층 경계와 일치. 전이 전·중 정방정 총량 변화 | Polatidis 2013 JNM 432 | [초록] | 각 층이 독립된 응력 이력을 가짐 → "주기마다 재설정"의 응력 측 증거 |
| N6 | **원주 응력 부호 반전** | breakaway 시 원주 응력 압축→인장(Raman). 임계 두께는 계면 원주 응력 의존 | El Kadiri 2013 | [초록] | "산화막은 항상 압축"이라는 공통 초기 상태 가정과 충돌. 측정 위치(표면 vs 계면)와 산화 조건 확인 필요 |
| N7 | **가로 균열 개시점** | 계면 근처 국소 인장응력 + 미산화 SPP가 개시점, 균열 수 ∝ SPP 수 (Zircaloy-2) | Tejland & Andrén 2012 | [초록] | Nb 합금(SPP 종류·분율 다름)의 전이 두께 차이를 설명할 변수 후보. 순Zr(SPP 없음)에서의 주기 유무와 대조 필요 |
| N8 | **Zr1Nb 전이 1회** | Zr1Nb 전이 1회(396일) vs Zry-4(183일), 수직 균열 없음, 산화막 더 얇음 | Stoll & Slavinskaya 2023 | [초록] | rev.1 C7(Nb 합금 2차 전이 미도달) 보강 |
| N9 | **고연소 가속의 합금 의존** | 저Sn Zry-4 ~90 μm + 계면 수소화물 림; M5 <20 μm, H <100 ppm. 응력 없는 조사 관에서도 Zry-4 ~60 μm(93 GWd/tU) vs M5 ~7.5 μm(79 GWd/tU), 속도 8배 | Bossis 2005 STP / 2006 JAI; CEA | [초록] | rev.1 C5 보강. Sn이 가속 개시, 수소화물이 추가 가속 |
| N10 | **노내 산화막 나노구조** | BWR 고연소(Oskarshamn 3) APT: 조사 유발 FeCrNi 클러스터가 기지 산소 확산을 약간 가속, c-루프가 산화물 핵생성 자리 제공 가능. 기공이 수소흡수 가속 경로 | Mayweg 외, *Acta Mater.* 292 (2025) | [초록] | 주기성 데이터는 아님(rev.1 refs의 Chalmers 보고서 정정: 보고서가 아니라 Acta 논문) |

---

## 5. 판별표 재구성 (pptx 6장 → 4열 + 신규 시험)

rev.1 4절의 3열 표에 El Kadiri 열과 신규 시험 행을 더한다. ○ 설명 가능 / △ 조건부 / × 상충 / – 미취급.

| 시험 항목 | Platt (거칠기·균열) | Gupta (Turing·결맞음) | Liao (t-ZrO₂ 크기 문턱) | El Kadiri (응력 부호 반전) |
|---|---|---|---|---|
| 전이 두께 1.5~2.9 μm (합금별) | △ 피팅 | △ | ○ (Arrhenius) | △ 계면 응력 피팅 |
| 2차 ≈ 2×1차 전이 (Couet, Liao) | – | – | △ | – |
| 온도 의존 3.3→4.2 μm | – | – | ○ | – |
| 리튬수 분기(주기 소멸·폭주) | △ 기공→파괴강도↓ | △ 비주기 영역 | – | – |
| 수소화물 조기 전이(2→1.5 μm) | ○ 경화→균열 | – | – (Σc의 H 의존 필요) | △ 계면 응력 변화 |
| f_H 주기(C4, N2) | △ 균열=전자통로 | △ 기공 연결 | – | – |
| **N1 가스 분위기 주기성** | ○ (역학만으로 가능) | ○ | ○ | ○ |
| **N3 노내 부층 수 ∝ 1/내식성** | △ | △ | △ | – |
| **N5 층 경계 응력 불연속** | ○ | △ | – | ○ |
| **N6 응력 부호 반전** | × (압축 완화만) | × | – | ○ (정의상) |
| **N7 SPP 개시 균열** | △ 거칠기에 흡수 가능 | × 균열 불필요 | – | △ |
| 응력 완화 −1.76→−1.01 GPa (C3) | ○ | △ (산화물 전위 활주) | – | △ |
| t→m의 역할 | 결과(응력 해방 후) | 결맞음 상실 구동 | 입자 성장이 트리거 | **지연 요인(유익)** |

핵심 상충: **t→m 변태의 인과 방향이 네 모델 모두 다르다.** (Platt: 결과 / Gupta: 결맞음 상실의 결과이며 기공 형성 원인 / Liao: 입자 성장 → 변태 → 균열 / El Kadiri: 변태가 전이를 늦춤). 이것이 판별 벤치마크의 1번 축이 되어야 한다. 실험적으로는 전이 직전 정방정 분율·응력의 시간 분해 측정(Polatidis 2013, Ensor 2019, NPIC 2020)이 결정 데이터다.

---

## 6. 모델 목록이 닫혔는가

- **거의 닫힘.** 8개 계열은 1970년(Bradhurst·Heuer) 이후 제안된 주기 전이 관련 정량·반정량 모델을 포괄한다고 판단한다. 남은 확인 사항:
  1. PENG 2026(Materials Reports) 원문의 모델 목록과 대조 → 중국 측 모델(NPIC 내부 모델, 핵동력공정 2018의 "제2상 산화 팽창 → 압축응력 완화 → 보호성 상실") 누락 확인.
  2. IAEA TECDOC-996(1998) 7.3~7.5절 수동 열람 → 1990년대 반경험·기구 모델(ABB Atom, Siemens, EPRI 초기) 보완.
  3. INIS "Review of theoretical conceptions on regimes of oxidation and hydrogen pickup in Zr-alloys" → 러시아권 이론 모델 리뷰일 가능성.
  4. Lallemant 계열의 정확한 서지(Gupta 2026 ref. 89~91).
- **주기성을 "내장"한 모델**(외생 전이 조건 없이 반복을 스스로 만드는 모델)은 여전히 **Gupta(Turing)뿐**이다. Bradhurst·Heuer, Liao, El Kadiri, Platt, Aryanfar는 모두 "임계값 도달 → 재설정"의 외생 규칙으로 주기를 만든다. 이 구분(내생 진동 vs 문턱 재설정)이 리뷰의 분류 축으로 유효하다.

---

## 7. rev.1 대비 바뀐 견해

1. **"응력은 주기 안에서 계속 풀린다"(rev.1 4.1-1)는 El Kadiri의 부호 반전 보고와 긴장 관계.** Raman으로 잰 표면 원주 응력과 XRD로 잰 두께 평균 응력은 다른 양일 수 있으므로, 측정 위치·방법을 명시한 응력 데이터 표를 따로 만들어야 한다.
2. **주기성의 필요조건에서 "물"을 뺄 수 있다**(N1). 전이 기구 리뷰에서 수용액 특이 설명(Li⁺ 침투, 수소 발생 전하 균형)은 **주기의 변조 인자**이지 **주기의 원인**이 아니라고 서술하는 것이 안전하다.
3. **불안정 산화 성장(nodular·입계 침투, Ensor 2022)과 주기 전이는 분리**해야 한다. Gupta 2026의 3유형 분류를 채택.
4. **1970년 Bradhurst·Heuer를 모델 계보의 기점**으로 두면, Platt·Liao·El Kadiri는 모두 "임계 두께의 물리적 정체"를 다르게 채운 후속으로 정리된다. 리뷰 서사가 단순해진다.

---

## 8. 다음 단계 (수정)

### 8.1 원문 정독 (사용자 로컬 또는 PDF 업로드 후 클라우드)
1. **Li 외 2026 JNM 156217** 전문: 주기(2차 이후 전이)와 모델 비교를 다루는지. 다룬다면 이 리뷰의 차별점을 "공통 데이터 벤치마크"로 좁혀야 함.
2. **PENG 외 2026 Materials Reports** 전문(중국어): 모델 목록 대조(6절-1).
3. **El Kadiri 2013 Acta** 전문(Scholars Mine OA): 응력 측정 위치·조건, 임계 두께 식, t→m 지연 논리. Platt·Polatidis 응력 데이터와 같은 좌표계로 환산.
4. **Harada & Wakamatsu 2008 JAI**: 가스 분위기 주기의 층 두께·전이 시간 수치, f_H 주기 그래프. 6절 데이터 표에 추가.
5. **Westinghouse OSP STP 1543**: 부층 두께·수·합금 대응표.
6. Motta 2015 4.2절·6장 참고문헌 추적(rev.1 8.1-1), Gupta 2026 ref. 89~91, IAEA TECDOC-996 7장 — 유지.
7. Bradhurst & Heuer 1970, Bryner 1979 원문: 주기 입방근 모델의 식을 복원해 파이썬 구현 1호로 삼음(가장 단순한 기준 모델).

### 8.2 벤치마크 준비
8. 6절 데이터 표 + 4절 N1~N9를 CSV로(조건·합금·측정법·근거 등급 태그).
9. 구현 순서: Bradhurst·Heuer(해석적) → Liao(해석적) → Aryanfar(CA) → Platt 축약 → El Kadiri 임계 두께 식 → Gupta 1차원 Turing.
10. 응력 데이터 전용 표(측정법: XRD 평균 / 싱크로트론 두께 분해 / Raman 표면 / 곡률법; 위상: m/t; 조건).

### 8.3 보류
11. 완화 진동자 정식화 — Lallemant Ti-Zr 진동의 두 기구(열 피드백 / 응력 차단)가 바로 그 선행이므로, 재논의 시 Gupta 2026 ref. 89~91 원문부터.

---

## 9. 자료 확보 경로

### 9.1 로컬 `refs\`에 이미 있는 22개 → 클라우드 정독용으로 업로드 권장
Yilmazbayhan 2004, Motta 2005, Bisor-Melloul 2011, Couet 2014, Ensor 2017, Platt thesis, Yardley 2017, Gupta·Tripathi·Gorr 2026, Motta·Couet·Comstock 2015, IAEA TECDOC-996, ANT ZIRAT12 1장, Aryanfar 2019, Mayweg 2025(구 "Chalmers 보고서") 및 각 `_text.txt`.

### 9.2 신규 확보 대상 (오픈액세스 또는 저자 공개)
| 문헌 | 경로 | 비고 |
|---|---|---|
| El Kadiri 2013 Acta | https://scholarsmine.mst.edu/matsci_eng_facwork/1506 | OA 사본 |
| Mamivand TMS 2013 / Acta 2013·2014 | https://scholarsmine.mst.edu/matsci_eng_facwork/1527 , /1500 , /1511 | OA |
| Mamivand PhD 2014 | https://scholarsjunction.msstate.edu/td/3522 | OA |
| Tejland & Andrén 2012 | https://research.chalmers.se/publication/161446 | Chalmers OA 가능성 |
| Couet CS 2015 (C4 I) | https://www.nuce.psu.edu/Motta/Publications/131_Couet_CS_2015.pdf | PSU |
| Couet CS 2017 (EIS) | https://www.nuce.psu.edu/Motta/Publications/137_Couet_CS_2017.pdf | PSU |
| Ensor JNM 2019 / STP 2021 / JNM 2022 | https://www.nuce.psu.edu/Motta/Publications/166_Ensor_JNM_2019.pdf , 177_Ensor_STP_2021.pdf , 181_Ensor_JNM_2022.pdf | PSU |
| Spengler JNM 2015 (마이크로빔) | https://www.nuce.psu.edu/Motta/Publications/122_Spengler_JNM_2015.pdf | PSU |
| de Gabory JNM 2015 ×2 | https://www.nuce.psu.edu/Motta/Publications/118_de%20Gabory_JNM_2015.pdf , 121_… | PSU |
| Allen·Konings·Motta CNM 2012 | https://www.nuce.psu.edu/Motta/Publications/2012_Allen_CNM.pdf | PSU(재배포 제한) |
| Motta JOM 2011 | https://www.nuce.psu.edu/Motta/Publications/2011_Motta_JoM.pdf | PSU |
| Motta JASTMI 2008 (층상 산화막) | https://www.nuce.psu.edu/Motta/Publications/2008_Motta_JASTMI.pdf | PSU |
| Wang JNM 2025 (MUZIC-3, 노내 가속 30~40배) | https://www.nuce.psu.edu/Motta/Publications/192_Wang_JNM_2025.pdf | PSU |
| Stoll & Slavinskaya 2023 | https://www.tandfonline.com/doi/full/10.1080/00223131.2022.2127954 | 이전 세션 열람 가능했음 |
| PENG 2026 Materials Reports | https://www.mater-rep.com/CN/Y2026/V40/I2/24120206 | "Full Text (PDF)" 버튼, 브라우저 필요 |
| Lea·Haynes·Wenman 2024 | https://ueaeprints.uea.ac.uk/id/eprint/98773 | 전문 미공개, 저자 요청 |
| arXiv 2107.05867 (Lallemant 인용 리뷰) | https://arxiv.org/pdf/2107.05867 | ref. [17] 서지 확인용 |

### 9.3 유료 (기관 인증 필요)
Li 2026 JNM 156217; Harada & Wakamatsu 2008 JAI / STP 1505; Beie 1994 STP 1245; Bradhurst & Heuer 1970 JNM 37; Bryner 1979 JNM 82; Garzarolli 1991 STP 1132; Hillner 2000 JNM 278; Polatidis 2013 JNM 432; Garner 2016 JNM 479; NPIC 2020 JNM(t-ZrO₂ critical behavior); Westinghouse OSP STP 1543; Bossis 2005 STP / 2006 JAI; Cox 2005 JNM 336; Vermoyal 1999–2002; Roy & Burgess 1970.

### 9.4 클라우드 세션에서 전문을 읽으려면
환경 설정의 Network access에서 아래 도메인을 Allowed domains에 추가하면 이 세션에서 직접 PDF를 받아 정독할 수 있다: `www.nuce.psu.edu`, `publikationen.bibliothek.kit.edu`, `arxiv.org`, `export.arxiv.org`, `www.osti.gov`, `ora.ox.ac.uk`, `pure.manchester.ac.uk`, `deepblue.lib.umich.edu`, `scholarsmine.mst.edu`, `scholarsjunction.msstate.edu`, `research.chalmers.se`, `www.frontiersin.org`, `www.cell.com`, `www.mater-rep.com`, `www.tandfonline.com`, `ueaeprints.uea.ac.uk`. 절차: https://code.claude.com/docs/en/cloud-environments#network-access
