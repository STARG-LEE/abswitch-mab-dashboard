# ABSwitch mAb PK Database — Dashboard

FDA Label / EMA SmPC 기반으로 추출한 단일클론항체(mAb) 약동학(PK) 데이터베이스 대시보드.

## 🌐 Live Demo

👉 **[Open Dashboard](https://STARG-LEE.github.io/abswitch-mab-dashboard/)**

## 📊 Coverage

- **Total rows**: 466 (presentation × source 단위)
- **Unique INNs**: 126 (Whole mAb 기준 normalized)
- **FDA**: 205 rows (112 INNs)
- **EMA**: 261 rows (108 INNs)
- **vs Prof. Park PhaseW**: **96.0% coverage** (119/124 FDA∪EMA approved Whole mAbs)

## 🔍 Features

- **Overview**: 핵심 지표 대시보드 + FDA/EMA 교집합 차트
- **Substances**: Route, Physical form, Biosimilar 패밀리 분포
- **Concentrations**: API 농도 히스토그램 (originator vs biosimilar, IV vs SC)
- **PK parameters (F/CL/Vd)**: 박스플롯 + F vs CL 산점도, 추출 완전도
- **Excipients**: 15종 첨가제 빈도 (one-hot)
- **IV → SC Transitions**: 26개 dual-route mAb의 농도 fold-increase
- **vs PhaseW**: 교수님 PhaseW DB와 1:1 비교
- **Browse all data** (DataTables.js): 전체 466개 행 검색/필터/정렬/CSV/Excel 다운로드
- **Substance summary**: INN 그룹화 요약

## 📁 Files

- `index.html` — Dashboard (single-file, Plotly + DataTables CDN)
- `abswitch_v2_export.csv` — Full DB export (UTF-8 BOM)

## 🛠 Tech Stack

- **Plotly.js 2.35.2** — Interactive charts
- **DataTables.js 2.0.8** — Data table with search/filter/export
- **Vanilla HTML/CSS/JS** — No build step required

## 🧪 Data Source & Methodology

1. **Data Sources**:
   - FDA Label Section 3 (DOSAGE FORMS AND STRENGTHS) + Section 12.3 (PHARMACOKINETICS)
   - EMA SmPC Section 2 (Qualitative and Quantitative Composition) + Section 5.2 (Pharmacokinetic properties)
   - DailyMed SPL fallback for some FDA labels

2. **Extraction**: GPT-5 API + manual verification for key originators
3. **Biosimilar Inheritance**: Originator PK values inherited for biosimilar rows where labels lack PK data
4. **Whole mAb Filter** (per Prof. Park PhaseW policy):
   - **Excluded**: Bispecific, ADC, Fab fragment, Diagnostic/Polyclonal
   - **Included**: Hyaluronidase combos, INMAZEB, OPDUALAG, Phesgo, Ronapreve, Evusheld

## 📈 Coverage Tracking

| Version | Coverage | Note |
|---|---|---|
| v1 (initial) | 92.7% | First comparison |
| v2 (hyaluronidase mapping) | 94.4% | After combo product alignment |
| v3 (Whole mAb cleanup) | 95.2% | After removing 43 non-Whole-mAb rows |
| **v3.1 (label augmentation)** | **96.0%** | Current — added 5 missing labels |

## 🤝 Reference

Inspired by [Prof. Dae Keun Park's PhaseW Whole mAb Dashboard](https://sdkparkforbi.github.io/mAb/storybooks/abswitch_wmab/dashboard.html) (CHA University · AI Healthcare Convergence).

## 📄 License

For research purposes. Data extracted from publicly available FDA Labels and EMA SmPCs.

---

Generated with [Claude Code](https://claude.com/claude-code)
