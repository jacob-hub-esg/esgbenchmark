# 🌿 Building Emissions Benchmark & Decarbonisation Tool

A web-based carbon accounting tool that helps property owners calculate their Scope 1 & 2 emissions, benchmark against EU peers, assess CSRD readiness, and visualise a pathway to Net Zero 2050.

> Built as part of a portfolio project exploring automated carbon accounting for the real estate sector — the industry responsible for 27% of global CO₂ emissions.

🔗 **[Live Demo →](https://your-codesandbox-link-here)**

---

## What It Does

### 1. 🏢 Building Profile
- Select from 20 European countries with real, localised grid emission factors
- Choose building type: Office, Residential, Retail, Industrial, Hotel, or Healthcare

### 2. ⚡ Energy Data Input
- Input annual kWh for natural gas (Scope 1), electricity, and district heating (Scope 2)
- Emission factors applied automatically per GHG Protocol methodology

### 3. ✅ CSRD Readiness Check
- 6-point checklist covering Scope tracking, energy audits, SBTi targets, and third-party verification
- Scored out of 100 with a readiness rating

### 4. 📊 Results Dashboard
- **Total emissions** and **emission intensity** (kg CO₂e/m²)
- **EU benchmark comparison** against best-in-class, average, and poor performers by building type
- **Scope 1 vs Scope 2 breakdown** with percentage split
- **Decarbonisation pathway chart** projecting trajectory to Net Zero 2050
- **CSRD readiness gauge** with gap analysis

---

## Methodology

| Source | Details |
|---|---|
| Scope 1 | Natural gas combustion @ 0.202 kg CO₂/kWh |
| Scope 2 | Country-specific grid emission factors (IEA 2023) |
| District Heat | Average EU district heating factor @ 0.17 kg CO₂/kWh |
| Benchmarks | EU building sector intensity averages by typology |
| Frameworks | GHG Protocol Corporate Standard, ESRS E1, CSRD |

---

## Emission Factors Covered

Denmark · Sweden · Norway · Finland · Germany · Netherlands · France · Italy · Spain · Poland · United Kingdom · Belgium · Lithuania · Latvia · Estonia · Czech Republic · Austria · Switzerland · Portugal · Greece

---

## Tech Stack

- **React** with hooks
- **Recharts** for data visualisation
- **GHG Protocol** methodology for emission calculations
- No backend — fully client-side

---

## Getting Started

```bash
# Clone the repo
git clone https://github.com/your-username/building-emissions-tool

# Install dependencies
npm install

# Run locally
npm start
```

Or open directly in CodeSandbox: **[your-codesandbox-link-here]**

---

## About the Author

**Joatham Jacob** — Energy & Environmental Engineer | ESG & Carbon Analyst

Sustainability specialist with hands-on experience in ESG reporting, carbon accounting, and decarbonisation strategy across European corporate environments. Proficient in GHG Protocol (Scope 1, 2 & 3), GRI, SASB, TCFD, ESRS, and CSRD frameworks.

📧 joathamjacob@gmail.com
🔗 [linkedin.com/in/joatham-jacob](https://linkedin.com/in/joatham-jacob)

---

## Related Projects

- 🧮 CO₂ Benchmark Calculator *(Legacy startup project)*
- 📊 CSRD Readiness Assessment Framework *(coming soon)*
- 🗺️ European Emission Factor Database *(coming soon)*

---

*This tool is intended for estimation and benchmarking purposes. For regulatory-grade reporting, verified primary data and certified methodologies should be used.*
