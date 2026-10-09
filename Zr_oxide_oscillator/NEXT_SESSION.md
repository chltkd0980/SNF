# 다음 세션 인수인계 (2026-10-09 작성)

새 클라우드 세션에서 이 파일을 먼저 읽고 시작한다. 이 폴더의 문서 3개가 전체 맥락이다.

| 파일 | 내용 | 상태 |
|---|---|---|
| `SNF_Zr_oxide_transition_research_notes.md` | rev.1. 주제 탐색 경로, 1차 출처로 확인한 사실 C1~C8, 세 모델(Platt/Gupta/Liao) 비교, 리뷰 지형, 판별 데이터, URL | 완료 (로컬 세션, 원문 기반) |
| `review_02_cyclic_transition_models_deep_dive.md` | rev.2. 모델 목록 8계열 ~25항목, 신규 경계조건 N1~N10, 4열 판별표, 자료 확보 경로 | 완료 (클라우드 세션, **검색 요약 기반** — 전문 미확인 항목 다수) |
| `NEXT_SESSION.md` | 이 파일 | — |

## 1. 지금까지의 결정 사항 (변경 금지)

1. 1순위 과제 = **주기성을 반영한 기존 산화막 모델 리뷰**. 타 분야 이론(완화 진동자 등) 이식은 보류 (사용자 지시 2026-10-08).
2. 목표 등급 = Corrosion Science·JNM·Acta급 **모델 판별 리뷰 + 공통 데이터 벤치마크**. 새 실험 없이 발표 데이터 재해석으로 1차 결과.
3. 리뷰의 분류 축 = **내생 진동(Gupta Turing)** vs **문턱 재설정(Bradhurst·Heuer 1970 → Platt / Liao / El Kadiri / Aryanfar)**. 판별 1번 축 = **t→m 변태의 인과 방향**(네 모델이 전부 다름).
4. 불안정 산화 성장(nodular, Ensor 2022)은 주기 전이와 **분리**해서 다룬다.

## 2. 직전 세션에서 막힌 것

- 클라우드 컨테이너 네트워크 정책이 외부 PDF 호스트를 전부 차단해 **전문을 한 편도 못 읽었다.** rev.2는 전부 WebSearch 초록·요약 수준이며 각 항목에 [원문]/[초록]/[요약] 등급을 붙여 두었다.
- 사용자가 환경 설정에서 도메인을 허용했으나 기존 세션에는 반영되지 않아 새 세션을 열기로 함. **새 세션에서 첫 번째로 할 일: 아래 다운로드 스크립트로 접근 가능 여부 확인.**

## 3. 새 세션 첫 작업: 오픈액세스 PDF 일괄 확보

```bash
mkdir -p refs && cd refs
while read name url; do curl -sSL -m 120 -A "Mozilla/5.0" -o "$name" -w "$name %{http_code} %{size_download}\n" "$url"; done << 'EOF'
motta2015_ARMR.pdf https://www.nuce.psu.edu/Motta/Publications/124_Motta_ARoMR_2015.pdf
couet2014_JNM.pdf https://www.nuce.psu.edu/motta/Publications/112_Couet_JNM_2014.pdf
yilmazbayhan2004_JNM.pdf https://www.nuce.psu.edu/motta/Publications/2004_Yilmazbayhan_JNM.pdf
motta2005_JASTMI.pdf https://www.nuce.psu.edu/motta/Publications/2005_Motta_JASTMI.pdf
ensor2017_JNM.pdf https://www.nuce.psu.edu/motta/Publications/148_Ensor_JNM_2017.pdf
bisor2011_RGN.pdf https://www.nuce.psu.edu/Motta/Publications/2011_Bisor-Melloul_RGN.pdf
couet2015_CS_C4.pdf https://www.nuce.psu.edu/Motta/Publications/131_Couet_CS_2015.pdf
couet2017_CS_EIS.pdf https://www.nuce.psu.edu/Motta/Publications/137_Couet_CS_2017.pdf
ensor2019_JNM.pdf https://www.nuce.psu.edu/Motta/Publications/166_Ensor_JNM_2019.pdf
ensor2021_STP.pdf https://www.nuce.psu.edu/Motta/Publications/177_Ensor_STP_2021.pdf
ensor2022_JNM.pdf https://www.nuce.psu.edu/Motta/Publications/181_Ensor_JNM_2022.pdf
spengler2015_JNM.pdf https://www.nuce.psu.edu/Motta/Publications/122_Spengler_JNM_2015.pdf
allen2012_CNM.pdf https://www.nuce.psu.edu/Motta/Publications/2012_Allen_CNM.pdf
motta2011_JOM.pdf https://www.nuce.psu.edu/Motta/Publications/2011_Motta_JoM.pdf
motta2008_JASTMI.pdf https://www.nuce.psu.edu/Motta/Publications/2008_Motta_JASTMI.pdf
wang2025_JNM.pdf https://www.nuce.psu.edu/Motta/Publications/192_Wang_JNM_2025.pdf
yilmazbayhan2006_JNM.pdf https://www.nuce.psu.edu/Motta/Publications/2006_Yilmazbayhan_JNM.pdf
gupta2026_HTCM.pdf https://publikationen.bibliothek.kit.edu/1000195894/186542640
aryanfar2019_arxiv.pdf https://arxiv.org/pdf/1904.03344
oscill_review_arxiv2107.pdf https://arxiv.org/pdf/2107.05867
platt_thesis.pdf https://pure.manchester.ac.uk/ws/portalfiles/portal/54552151/FULL_TEXT.PDF
iaea_tecdoc996.pdf https://www.osti.gov/etdeweb/servlets/purl/20010506
tang2024_frontiers.pdf https://www.frontiersin.org/journals/materials/articles/10.3389/fmats.2024.1381818/pdf
elkadiri2013_acta.pdf https://scholarsmine.mst.edu/cgi/viewcontent.cgi?article=2505&context=matsci_eng_facwork
tejland2012_JNM.pdf https://research.chalmers.se/publication/161446/file/161446_Fulltext.pdf
EOF
file *.pdf
```

- 텍스트 추출: `pdftotext -layout x.pdf x.txt` (컨테이너에 설치됨). pymupdf는 없고 pypdf는 있음.
- IAEA TECDOC-996은 스캔본이라 OCR 필요(tesseract 미설치 → `pip install ocrmypdf` 시도 또는 수동).
- El Kadiri·Tejland URL은 추정 경로이므로 404면 리포지토리 페이지에서 PDF 링크를 다시 찾을 것.
- 여전히 403이면 환경의 Allowed domains에 rev.2 9.4절 도메인이 들어갔는지 사용자에게 확인 요청.

## 4. 정독 순서와 각 문헌에서 뽑을 것 (rev.2 8.1절 구체화)

| 순서 | 문헌 | 뽑을 것 | 반영 위치 |
|---|---|---|---|
| 1 | Motta 2015 ARMR 4.2절·6장 | 전이 기구 (a)(b)의 근거 참고문헌 번호와 서지, 각 기구가 기대는 측정. C4 모델 가정과 전이 분리 방식 | rev.1 5절 표, rev.2 2절 |
| 2 | Gupta 2026 HTCM | ref. 89~91 서지(Lallemant), "Proposed Unifying Breakaway Factors" 절, 3유형 분류 원문 | rev.2 3-F, 6절 |
| 3 | El Kadiri 2013 Acta | 응력 측정 위치·방법(Raman 표면?), 임계 두께 식, t→m 지연 논리, 산화 조건 | rev.2 3-C, 5절 판별표 N6 |
| 4 | Ensor 2019 JNM | 정방정 입자 임계 크기·온도 의존, Liao Σc와 비교 가능한 수치 | rev.2 3-D |
| 5 | Ensor 2022 JNM + 2021 STP | 불안정 성장 vs 주기 전이의 구분 기준 | rev.2 3-I |
| 6 | Couet 2015 C4 I, 2017 EIS | 전이를 어떻게 외생 처리하는지, EIS에서 전이 시점 표식 | rev.2 3-G |
| 7 | Tejland 2012 | SPP 개시 균열의 정량(균열 수/SPP 수), 응력장 깊이 | rev.2 N7 |
| 8 | Platt thesis 7장, Yardley 2장 | 이미 rev.1에 반영. 응력 수치 재확인만 | — |
| 9 | Motta 2008 JASTMI, Yilmazbayhan 2006 | 층상 산화막 서술, 층 두께 데이터 추가 | rev.1 6절 표 |
| 10 | IAEA TECDOC-996 7.3~7.5 | 1990년대 모델 목록(ABB Atom, Siemens, EPRI 초기) → 모델 목록 누락 보완 | rev.2 3-A, 6절 |
| 11 | arXiv 2107.05867 | ref. [17] Lallemant 정확한 서지 | rev.2 3-F 27번 |

산출물: **rev.3** = rev.2의 [초록]/[요약] 항목을 [원문]으로 승격하고 수정된 내용 반영. 파일명 `review_03_...md` 또는 rev.2 파일을 직접 갱신(갱신 시 변경 이력은 git에 남으므로 직접 갱신 권장).

## 5. 사용자 브라우저가 필요한 자료 (클라우드에서 못 받음)

- Li 외 JNM 619 (2026) 156217 — 전이 기구 전용 리뷰. **최우선**. 기관 인증.
- PENG 외 Materials Reports 40(2) (2026) 24120206 — 중국어 모델 리뷰. https://www.mater-rep.com/CN/Y2026/V40/I2/24120206 의 "Full Text (PDF)".
- Harada & Wakamatsu 2008 JAI 5(3) / STP 1505 — 가스 분위기 주기성. ASTM 유료.
- Westinghouse OSP, ASTM STP 1543 (2013) — 노내 부층. ASTM 유료.
- Gupta 2021 미시간 학위논문 PDF — https://deepblue.lib.umich.edu/items/460712d6-0602-4ba5-bde4-6ebf758a2203 (봇 차단, 브라우저로).
- Ensor 2016 PSU 학위논문 — etda.libraries.psu.edu에서 저자명 검색.
- Bradhurst & Heuer 1970 JNM 37, Bryner 1979 JNM 82, Beie 1994 STP 1245, Polatidis 2013 JNM 432, Cox 2005 JNM 336 — 기관 인증.

받은 PDF는 세션에 업로드하거나 로컬 `Cowork\Zr_oxide_oscillator\refs\`에 저장.

## 6. 벤치마크 준비 (정독 후)

1. rev.1 6절 + rev.2 4절(N1~N10)을 `data/transition_benchmark.csv`로: 열 = 관측량, 값, 단위, 합금, 온도, 매질, 측정법, 출처, 근거등급.
2. 응력 전용 표 `data/oxide_stress.csv`: 측정법(XRD 평균/싱크로트론 두께분해/Raman 표면/곡률)·위상(m/t)·조건을 분리. El Kadiri(부호 반전)와 Platt(압축 완화)의 충돌을 같은 좌표계에서 비교하기 위함.
3. 파이썬 구현 순서: Bradhurst·Heuer 주기 입방근(해석적, 기준선) → Liao 문턱 → Aryanfar CA → Platt 축약 → El Kadiri 임계 두께 → Gupta 1차원 Turing. 폴더 `models/`.

## 7. 새 세션 첫 메시지 예시

```
SNF 저장소 Zr_oxide_oscillator/NEXT_SESSION.md를 읽고 그대로 진행해줘.
3절 스크립트로 PDF를 받고, 4절 순서로 정독해서 rev.2 문서를 rev.3로 갱신한 뒤 커밋·push해줘.
```

## 8. 세션 기록

- 2026-10-06~08 (로컬 Cowork): 주제 탐색, C1~C8 원문 확인, 세 모델 도식 pptx, rev.1 작성.
- 2026-10-09 (클라우드 session_012cDbtkHAJZBChToQuoNf5F): 저장소 초기화, rev.1 업로드, 검색 기반 rev.2 작성. 네트워크 차단으로 전문 정독 못 함. 브랜치 `claude/amazing-feynman-38931d`. 기본 브랜치(main) 미설정 — GitHub 설정에서 지정 필요.
