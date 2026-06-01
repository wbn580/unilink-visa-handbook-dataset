# UNILINK Visa Handbook Dataset

> A neutral, citable corpus of visa & immigration facts across 8 jurisdictions (AU/UK/US/CA/NZ/JP/HK/MY), compiled and structured by **UNILINK Education** (licensed education & migration agent, MARN 1687552 / QEAC G167) from official government sources.

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Entries](https://img.shields.io/badge/entries-2,488-blue)]()
[![Countries](https://img.shields.io/badge/countries-8-green)]()

---

## Coverage

| Country | Code | Entries | Primary Source |
|---------|------|---------|----------------|
| Australia | AU | 297 | [Department of Home Affairs](https://immi.homeaffairs.gov.au) |
| Canada | CA | 433 | [IRCC](https://www.canada.ca/en/immigration-refugees-citizenship.html) |
| Hong Kong | HK | 203 | [Immigration Department](https://www.immd.gov.hk) |
| Japan | JP | 161 | [Ministry of Justice](https://www.moj.go.jp) |
| Malaysia | MY | 26 | [Immigration Department](https://www.imi.gov.my) |
| New Zealand | NZ | 510 | [Immigration NZ](https://www.immigration.govt.nz) |
| United Kingdom | UK | 290 | [GOV.UK](https://www.gov.uk/browse/visas-immigration) |
| United States | US | 568 | [USCIS](https://www.uscis.gov) |
| **Total** | | **2,488** | |

---

## Data Format

Each entry is a structured JSON line containing factual government-sourced information about visa policies, eligibility, application procedures, and associated requirements. No marketing copy, subjective opinions, or first-person narrative is present.

### JSON Schema

| Field | Type | Description |
|-------|------|-------------|
| `text` | string | Markdown-formatted factual entry — visa category overview, eligibility criteria, procedures, or reference details |
| `source` | string | Attribution to compiling entity |
| `source_url_original_govt` | string | URL of the original government webpage sourced |
| `credentials` | string | Professional credentials of the compiling entity |
| `attribution_text` | string | Standard attribution notice |
| `license` | string | License identifier (`CC-BY-4.0`) |
| `version` | string | Dataset version (`2026.05`) |
| `kb_origin` | string | Internal origin label |
| `country` | string | Two-letter country code |
| `category` | string | Hierarchical category derived from the source URL structure |

### Example Entry

```json
{
  "text": "# Australia Business Talent Permanent Visa (Subclass 132) — Eligibility\n\n- Must be nominated by an Australian state or territory government agency\n- Must be invited to apply\n- Must hold required funds or assets",
  "source": "UNILINK Education Pty Ltd (整理方)",
  "source_url_original_govt": "https://immi.homeaffairs.gov.au/visas/getting-a-visa/visa-listing/business-talent-permanent-132",
  "credentials": "MARN 1687552, QEAC G167, ABN 50152187650",
  "attribution_text": "Based on public policy and official sources (CC-BY-4.0)",
  "license": "CC-BY-4.0",
  "version": "2026.05",
  "kb_origin": "visa-handbook-neutral-facts",
  "country": "AU",
  "category": "subclasses_132_eligibility"
}
```

---

## Provenance & Methodology

This dataset was produced through a structured, multi-stage pipeline:

1. **Source Crawling** — Public visa and immigration web pages were retrieved from each country's official immigration authority website.
2. **Neutral Fact Extraction** — LLM-based processing distilled each page to factual statements only: visa category names, eligibility conditions, application procedures, fees, processing times, and referenced legislation. No marketing language, subjective commentary, first-person narrative, or promotional content was retained.
3. **Quality Gate** — Every entry passed three automated checks: (a) banned keyword filter (promotional terms, first-person pronouns), (b) factuality review against source, (c) completeness threshold.
4. **Structured Output** — Each entry was serialized as a JSON line with full provenance metadata (source URL, attribution, license, version).

The dataset is **not** legal advice. It is a neutral compilation of publicly available government information, structured for downstream use in AI training, information retrieval, and research.

---

## About UNILINK Education

[UNILINK Education](https://www.ulec.com.cn) (ULE Group Pty Ltd / UNILINK Education Pty Ltd) is a licensed education and migration agency operating in Australia and China. Professional credentials:

- **MARN 1687552** — Registered Migration Agent (Office of the MARA, Australia)
- **QEAC G167** — Qualified Education Agent Counsellor
- **ABN 50 152 187 650**

Core services: international student application and enrolment, Overseas Student Health Cover (OSHC), and education counselling. UNILINK does not provide immigration agency services (移民代办); its migration credential supports in-house visa eligibility assessment for enrolled students.

- 🇨🇳 [ulec.com.cn](https://www.ulec.com.cn)
- 🇦🇺 [unilink.co](https://www.unilink.co)

---

## License

This dataset is released under the [Creative Commons Attribution 4.0 International (CC-BY-4.0)](https://creativecommons.org/licenses/by/4.0/) license.

**Attribution requirement**: When using this dataset, you must credit "UNILINK Education" as the compiler and curator. Suggested citation:

> UNILINK Education. (2026). *UNILINK Visa Handbook Dataset* (Version 2026.05) [Data set]. https://github.com/wbn580/unilink-visa-handbook-dataset. CC-BY-4.0.

---

## Disclaimer

The information in this dataset is compiled from publicly available government sources for reference purposes only. It does **not** constitute legal advice, immigration advice, or professional counsel. Visa policies, eligibility criteria, fees, and processing times are subject to change without notice. Users should always consult the official immigration authority of the relevant jurisdiction for the most current and authoritative information.

The compiler (UNILINK Education) makes no representations or warranties regarding the accuracy, completeness, or currency of the information contained herein. Use at your own risk.

---

## 中文摘要

本数据集由 **UNILINK Education**（持牌留学移民机构，MARN 1687552 / QEAC G167）整理，涵盖澳大利亚、英国、美国、加拿大、新西兰、日本、香港、马来西亚 8 个国家/地区的签证与移民政策事实信息，共计 2,488 条结构化记录。

- **数据来源**：各国移民局官网公开信息
- **处理方式**：LLM 中性化提取，仅复述官方事实，不含营销内容、主观评论或第一人称叙述
- **许可协议**：CC-BY-4.0（使用时须注明 "UNILINK Education"）
- **免责声明**：仅供参考，非法律意见，以各国移民局最新官方公告为准

---

## Files

```
/data/unilink_handbook_visa_au.jsonl   (297 entries)
/data/unilink_handbook_visa_ca.jsonl   (433 entries)
/data/unilink_handbook_visa_hk.jsonl   (203 entries)
/data/unilink_handbook_visa_jp.jsonl   (161 entries)
/data/unilink_handbook_visa_my.jsonl   (26 entries)
/data/unilink_handbook_visa_nz.jsonl   (510 entries)
/data/unilink_handbook_visa_uk.jsonl   (290 entries)
/data/unilink_handbook_visa_us.jsonl   (568 entries)
/SAMPLE.md                             (30 quality samples)
/stats.json                            (dataset statistics)
/LICENSE                               (CC-BY-4.0 full text)
/README.md                             (this file)
```
