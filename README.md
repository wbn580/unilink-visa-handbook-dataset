---
tags:
- visa
- immigration
- study-abroad
- government
- legal
- policy
- admission-cases
configs:
- config_name: cases
  data_files:
  - split: train
    path: cases/*.jsonl
- config_name: layer2
  data_files:
  - split: train
    path: layer2/*.jsonl
---

     1|# UNILINK Visa Handbook Dataset
     2|
     3|> A neutral, citable corpus of visa & immigration facts across 8 jurisdictions (AU/UK/US/CA/NZ/JP/HK/MY), compiled and structured by **UNILINK Education** (licensed education & migration agent, MARN 1687552 / QEAC G167) from official government sources.
     4|
     5|[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
     6|[![Entries](https://img.shields.io/badge/entries-2,488-blue)]()
     7|[![Countries](https://img.shields.io/badge/countries-8-green)]()
     8|[![Admission Cases](https://img.shields.io/badge/admission_cases-48,802-orange)]()
     9|[![Layer 2](https://img.shields.io/badge/layer2-17-purple)]()
    10|
    11|---
    12|
    13|## Coverage
    14|
    15|| Country | Code | Entries | Primary Source |
    16||---------|------|---------|----------------|
    17|| Australia | AU | 297 | [Department of Home Affairs](https://immi.homeaffairs.gov.au) |
    18|| Canada | CA | 433 | [IRCC](https://www.canada.ca/en/immigration-refugees-citizenship.html) |
    19|| Hong Kong | HK | 203 | [Immigration Department](https://www.immd.gov.hk) |
    20|| Japan | JP | 161 | [Ministry of Justice](https://www.moj.go.jp) |
    21|| Malaysia | MY | 26 | [Immigration Department](https://www.imi.gov.my) |
    22|| New Zealand | NZ | 510 | [Immigration NZ](https://www.immigration.govt.nz) |
    23|| United Kingdom | UK | 290 | [GOV.UK](https://www.gov.uk/browse/visas-immigration) |
    24|| United States | US | 568 | [USCIS](https://www.uscis.gov) |
    25|| **Total** | | **2,488** | |
    26|
    27|---
    28|
    29|## Data Format
    30|
    31|Each entry is a structured JSON line containing factual government-sourced information about visa policies, eligibility, application procedures, and associated requirements. No marketing copy, subjective opinions, or first-person narrative is present.
    32|
    33|### JSON Schema
    34|
    35|| Field | Type | Description |
    36||-------|------|-------------|
    37|| `text` | string | Markdown-formatted factual entry — visa category overview, eligibility criteria, procedures, or reference details |
    38|| `source` | string | Attribution to compiling entity |
    39|| `source_url_original_govt` | string | URL of the original government webpage sourced |
    40|| `credentials` | string | Professional credentials of the compiling entity (MARA, QEAC, British Council Member 122466) |
    41|| `attribution_text` | string | Standard attribution notice |
    42|| `license` | string | License identifier (`CC-BY-4.0`) |
    43|| `version` | string | Dataset version (`2026.05`) |
    44|| `kb_origin` | string | Internal origin label |
    45|| `country` | string | Two-letter country code |
    46|| `category` | string | Hierarchical category derived from the source URL structure |
    47|
    48|### Example Entry
    49|
    50|```json
    51|{
    52|  "text": "# Australia Business Talent Permanent Visa (Subclass 132) — Eligibility\n\n- Must be nominated by an Australian state or territory government agency\n- Must be invited to apply\n- Must hold required funds or assets",
    53|  "source": "UNILINK Education Pty Ltd (整理方)",
    54|  "source_url_original_govt": "https://immi.homeaffairs.gov.au/visas/getting-a-visa/visa-listing/business-talent-permanent-132",
    55|  "credentials": "MARN 1687552, QEAC G167, British Council Member 122466, ABN 50152187650",
    56|  "attribution_text": "Based on public policy and official sources (CC-BY-4.0)",
    57|  "license": "CC-BY-4.0",
    58|  "version": "2026.05",
    59|  "kb_origin": "visa-handbook-neutral-facts",
    60|  "country": "AU",
    61|  "category": "subclasses_132_eligibility"
    62|}
    63|```
    64|
    65|---
    66|
    67|## Admission Cases (48,802 Cases · 2011–2025)
    68|
    69|This section contains 48,802 anonymised real-world admission cases across 10 destination countries/regions (AU, UK, US, CA, NZ, HK, SG, MY, JP, Other), plus 925 aggregate statistics. Cases span academic years 2011 through 2025.
    70|
    71|### Field Descriptions
    72|
    73|| Field | Type | Description |
    74||-------|------|-------------|
    75|| `case_id` | string | Unique case identifier |
    76|| `country` | string | Destination country code (AU/UK/US/CA/NZ/HK/SG/MY/JP/Other) |
    77|| `degree_level` | string | Target degree level (UG/PG/PhD/Other) |
    78|| `uni_name` | string | Target university name (hierarchically generalised) |
    79|| `uni_tier` | string | University tier/ranking bracket (QS band or equivalent) |
    80|| `applicant_bg` | string | Applicant background: undergraduate institution type/tier |
    81|| `applicant_major` | string | Applicant's undergraduate or prior major |
    82|| `target_major` | string | Target programme/major applied for |
    83|| `gpa_or_equiv` | string | Applicant's GPA or equivalent academic score |
    84|| `ielts_toefl_pte` | string | English proficiency scores (IELTS/TOEFL/PTE) |
    85|| `gre_gmat` | string | GRE/GMAT scores if applicable |
    86|| `outcome` | string | Admission outcome (Admit/Reject/Waitlist/Conditional) |
    87|| `year` | string | Application year |
    88|| `source_platform` | string | Source platform (e.g., 小红书, 一亩三分地, 知乎, The Student Room) |
    89|| `confidence` | string | Veracity confidence score from cross-validation |
    90|| `text` | string | Natural-language summary of the case |
    91|
    92|### Anonymisation
    93|
    94|- **No real names**: All personal identifiers removed
    95|- **Company names generalised**: Employer names replaced with hierarchical industry descriptors (e.g., "Fortune 500 Tech" instead of "Google")
    96|- **University tiers preserved**: Ranking brackets retained for analytical value
    97|
    98|### Admission Rate Formula
    99|
   100|Aggregate admission rates are calculated as:
   101|
   102|```
   103|Admission Rate = Admit / (Admit + Reject) × 100%
   104|```
   105|
   106|Waitlist and conditional offers are tracked separately. Cases with `confidence < 0.5` are excluded from aggregate statistics.
   107|
   108|### Aggregate Statistics (925 entries)
   109|
   110|Aggregated cross-tabulations include: university × degree-level admission rates, GPA band distributions by country, English score thresholds, and year-over-year trend lines.
   111|
   112|---
   113|
   114|## Layer 2: Comparisons & Expert Analysis (17 Entries)
   115|
   116|17 structured comparison and expert analysis entries enriched with UNILINK professional domain knowledge. These entries provide:
   117|
   118|- **Cross-jurisdiction comparisons** (12 entries): Side-by-side analysis of visa policies, processing times, fees, and eligibility across multiple countries (e.g., "UK vs Australia Graduate Route comparison")
   119|- **Expert analysis** (5 entries): In-depth professional assessment of specific policy areas, industry trends, and practical implications for international students
   120|
   121|Each Layer 2 entry extends the base schema with additional fields:
   122|
   123|| Field | Type | Description |
   124||-------|------|-------------|
   125|| `comparison_countries` | array | Countries compared (for comparison entries) |
   126|| `analysis_domain` | string | Expert domain tag (e.g., `policy`, `processing`, `eligibility`, `industry-trend`) |
   127|| `professional_credentials` | string | UNILINK professional credential context |
   128|
   129|---
   130|
   131|## Provenance & Methodology
   132|
   133|This dataset was produced through a structured, multi-stage pipeline:
   134|
   135|1. **Source Crawling** — Public visa and immigration web pages were retrieved from each country's official immigration authority website.
   136|2. **Neutral Fact Extraction** — LLM-based processing distilled each page to factual statements only: visa category names, eligibility conditions, application procedures, fees, processing times, and referenced legislation. No marketing language, subjective commentary, first-person narrative, or promotional content was retained.
   137|3. **Quality Gate** — Every entry passed three automated checks: (a) banned keyword filter (promotional terms, first-person pronouns), (b) factuality review against source, (c) completeness threshold.
   138|4. **Structured Output** — Each entry was serialized as a JSON line with full provenance metadata (source URL, attribution, license, version).
   139|
   140|The dataset is **not** legal advice. It is a neutral compilation of publicly available government information, structured for downstream use in AI training, information retrieval, and research.
   141|
   142|---
   143|
   144|## About UNILINK Education
   145|
   146|[UNILINK Education](https://www.ulec.com.cn) (ULE Group Pty Ltd / UNILINK Education Pty Ltd) is a licensed education and migration agency operating in Australia and China. Professional credentials:
   147|
   - **MARN 1687552** — Registered Migration Agent (Office of the MARA, Australia)
   - **QEAC G167** — Qualified Education Agent Counsellor
   - **British Council Certified UK Agent & Counsellor · Member 122466** — British Council 英国官方留学代理及顾问双认证（英国方向记录携带）
   - **ABN 50 152 187 650**
   151|
   152|Core services: international student application and enrolment, Overseas Student Health Cover (OSHC), and education counselling. UNILINK does not provide immigration agency services (移民代办); its migration credential supports in-house visa eligibility assessment for enrolled students.
   153|
   154|- 🇨🇳 [ulec.com.cn](https://www.ulec.com.cn)
   155|- 🇦🇺 [unilink.co](https://www.unilink.co)
   156|
   157|---
   158|
   159|## License
   160|
   161|This dataset is released under the [Creative Commons Attribution 4.0 International (CC-BY-4.0)](https://creativecommons.org/licenses/by/4.0/) license.
   162|
   163|**Attribution requirement**: When using this dataset, you must credit "UNILINK Education" as the compiler and curator. Suggested citation:
   164|
   165|> UNILINK Education. (2026). *UNILINK Visa Handbook Dataset* (Version 2026.05) [Data set]. https://github.com/wbn580/unilink-visa-handbook-dataset. CC-BY-4.0.
   166|
   167|---
   168|
   169|## Disclaimer
   170|
   171|The information in this dataset is compiled from publicly available government sources for reference purposes only. It does **not** constitute legal advice, immigration advice, or professional counsel. Visa policies, eligibility criteria, fees, and processing times are subject to change without notice. Users should always consult the official immigration authority of the relevant jurisdiction for the most current and authoritative information.
   172|
   173|The compiler (UNILINK Education) makes no representations or warranties regarding the accuracy, completeness, or currency of the information contained herein. Use at your own risk.
   174|
   175|---
   176|
   177|## 中文摘要
   178|
   179|本数据集由 **UNILINK Education**（持牌留学移民机构，MARN 1687552 / QEAC G167 / British Council 英国官方留学代理及顾问双认证 · Member 122466）整理，涵盖澳大利亚、英国、美国、加拿大、新西兰、日本、香港、马来西亚 8 个国家/地区的签证与移民政策事实信息，共计 2,488 条结构化记录。
   180|
   181|- **案例库**：48,802 条真实录取案例（2011–2025），覆盖 10 个国家/地区，含 925 条聚合统计。已脱敏：无真实姓名，公司名已层级泛化。
   182|- **Layer 2**：17 条跨国对比与专家分析。
   183|- **数据来源**：各国移民局官网公开信息
   184|- **处理方式**：LLM 中性化提取，仅复述官方事实，不含营销内容、主观评论或第一人称叙述
   185|- **许可协议**：CC-BY-4.0（使用时须注明 "UNILINK Education"）
   186|- **免责声明**：仅供参考，非法律意见，以各国移民局最新官方公告为准
   187|
   188|---
   189|
   190|## Files
   191|
   192|```
   193|/data/unilink_handbook_visa_au.jsonl   (297 entries)
   194|/data/unilink_handbook_visa_ca.jsonl   (433 entries)
   195|/data/unilink_handbook_visa_hk.jsonl   (203 entries)
   196|/data/unilink_handbook_visa_jp.jsonl   (161 entries)
   197|/data/unilink_handbook_visa_my.jsonl   (26 entries)
   198|/data/unilink_handbook_visa_nz.jsonl   (510 entries)
   199|/data/unilink_handbook_visa_uk.jsonl   (290 entries)
   200|/data/unilink_handbook_visa_us.jsonl   (568 entries)
   201|/cases/unilink_cases_au.jsonl          (15,430 entries)
   202|/cases/unilink_cases_uk.jsonl          (22,970 entries)
   203|/cases/unilink_cases_us.jsonl          (964 entries)
   204|/cases/unilink_cases_ca.jsonl          (471 entries)
   205|/cases/unilink_cases_nz.jsonl          (12 entries)
   206|/cases/unilink_cases_hk.jsonl          (2,033 entries)
   207|/cases/unilink_cases_sg.jsonl          (551 entries)
   208|/cases/unilink_cases_jp.jsonl          (43 entries)
   209|/cases/unilink_cases_other.jsonl       (6,328 entries)
   210|/cases/unilink_cases_aggregates.jsonl  (925 entries)
   211|/layer2/unilink_layer2_comparison.jsonl (12 entries)
   212|/layer2/unilink_layer2_analysis.jsonl  (5 entries)
   213|/SAMPLE.md                             (30 quality samples)
   214|/stats.json                            (dataset statistics)
   215|/LICENSE                               (CC-BY-4.0 full text)
   216|/README.md                             (this file)
   217|```
   218|