# HR Turnover & Workforce Attrition Analytics Dashboard

## Project Overview

This project is a simulated **HR Turnover & Workforce Attrition Analytics Dashboard** built using **Python, SQL and Power BI**.

The goal of this project was to explore how employee departure data can be transformed into meaningful business insights related to:
- Voluntary vs. involuntary turnover patterns
- Regretted loss identification and tracking
- Risk group monitoring (early-tenure employees)
- Termination seasonality and trend analysis
- Workforce stability and retention risk management

The dataset was fully generated using Python to simulate a real-world company workforce lifecycle, including both active headcount and termination records across 2025–2026. The dashboard was then developed in Power BI to analyze departure trends, departure reasons, talent impact, and retention risk across different employee segments and divisions.

This project also represents part of my learning journey from 2025–2026 workforce analytics practice.

---

## Business Context

In many organizations, managing turnover is not only about reducing headcount loss.

HR and business leaders must understand:
- **Who** is leaving — key talent, high performers, or early-tenure employees
- **Why** they are leaving — compensation, career development, or company restructuring
- **When** departures peak — post-bonus periods, post-Year-End Review cycles
- **Where** the highest attrition risk lies — by division, function, or tenure band
- **What** the financial and operational impact of talent loss may be

This dashboard simulates how organizations can monitor and respond to workforce attrition during active business cycles, balancing retention investment with operational continuity.

---

## Dataset Description

The dataset was synthetically generated using Python and does not contain any real employee data.

Two core data tables were built to simulate a realistic workforce environment:

### EMP900 — Active Employee Base
The active headcount file covering the 2025 and 2026 workforce, including 1,350 active employees per reference year.

Key fields include:
- Employee ID, User ID, Name, Gender, Date of Birth
- Division, Business Unit, Cost Center, Location
- Job Level, JML (Position Class), Grade, Salary
- Contract Type, Hire Date, Seniority Dates
- Key Position Level, Player Status
- HR Manager, Work Schedule

### EMP906 — Leavers / Termination File
The termination records file covering 530 leavers in 2025 (~39% attrition) and 405 leavers in 2026 through May (~30% attrition).

Key fields include:
- Termination Date, Last Day of Activity, Notification Date
- Type of Termination (Employee Decision / Company Decision)
- Termination Reason, Sub-Reason, Local Reason (Vietnamese)
- Tenure at Departure, Age at Departure
- Critical Departure Flag (binary: 1 for senior voluntary leavers)
- OK to Rehire, Confidential Termination, Severance Agreement
- New Company (competitor destination for voluntary leavers)

### Workforce Structure
| Division | Focus Area | Attrition Logic |
|---|---|---|
| TECH | Technology | Voluntary — competitor offers |
| FARM | Agriculture | Voluntary — career development |
| FOOD | Food Manufacturing | Involuntary — restructuring/redundancy |
| LOG | Logistics & Supply Chain | Voluntary — compensation gaps |
| CORP | Corporate Services / HR / FIN | Voluntary — career development |

### Termination Seasonality Design
The dataset was engineered to reflect realistic departure peaks:
- **January–February**: Post-13th month bonus & Year-End Review period
- **May**: Post-mid-year bonus cycle
- **Mid-year dip**: March–April shows lower departure volume

---

## Tools & Technologies

- **Python** → Synthetic HR & termination dataset generation
- **Pandas & NumPy** → Data preparation, transformation, and integrity validation
- **SQL** → Data querying and validation
- **Power BI** → Dashboard development and workforce storytelling
- **DAX** → Turnover rate KPIs, regretted loss metrics, and risk group calculations

---

## Dashboard Structure & Analysis

---

### 1. Executive Overview — Turnover Summary

The main landing page provides an at-a-glance summary of overall workforce attrition health.

#### Key Metrics (2026 YTD)
- **Overall Turnover Rate**: 30.0%
- **Employee Decision Rate**: 22.6%
- **Company Decision Rate**: 7.4%
- **Regretted Loss Rate**: 4.0%
- **Key Player Turnover**: 34.3%
- **Risk Group (YOS ≤ 3) Turnover**: 11.9%
- **Average Group Experience**: 4.0 years
- **Total Departures**: 405 out of 1,350 employees

#### Monthly Departure Trend (Jan–May 2026)
| Month | Departures | Turnover Rate |
|---|---|---|
| January | 130 | 9.63% |
| February | 115 | 8.52% |
| March | 52 | 3.85% |
| April | 34 | 2.52% |
| May | 74 | 5.48% |

#### Top Termination Reasons
1. Competitor Offer — Better Package (100 departures)
2. Limited Growth Opportunity (90 departures)
3. Operational Redundancy (86 departures)
4. Workload & Flexibility Concerns (54 departures)

#### Analysis Focus
- Turnover trend visualization over time
- Voluntary vs. involuntary split
- Departure reason distribution
- Tenure band breakdown (< 1yr / 1–3yr / 3–6yr / 6yr+)
- Position class distribution of leavers

---

### 2. Full Detailed List

A fully filterable employee-level departure record table supporting drill-down investigation.

#### Filters Available
- Year, Legal Entity, Division
- Professional Field, Position Class
- Player Status, Type of Termination

#### Columns Displayed
- Termination Date, Division, User ID
- Name, Position Class (JML)
- Type of Termination, Termination Reason
- Professional Field, Key Position Level
- Player Status, Tenure (years), Age at Departure

#### Key Insight
The detailed list enables HR teams to move from aggregate trends into individual employee-level review — supporting exit interview validation, successor planning, and rehire eligibility checks.

---

### 3. Regretted Loss Analysis

This section focuses specifically on high-impact voluntary departures from Key Players and Top Talent.

#### Key Metrics (2026 YTD)
- **Total Regretted Loss**: 54 out of 1,350 employees
- **Regretted Loss Rate**: 4.0% overall
- **Peak Month**: February (21 departures, 1.6% monthly rate)

#### Monthly Regretted Loss Trend (Jan–May 2026)
| Month | Regretted Departures | Rate |
|---|---|---|
| January | 17 | 1.3% |
| February | 21 | 1.6% |
| March | 6 | 0.4% |
| April | 4 | 0.3% |
| May | 6 | 0.4% |

#### Regretted Loss by Reason
| Reason | Count |
|---|---|
| Limited Growth Opportunity | 21 |
| Competitor Offer — Better Package | 17 |
| Workload & Flexibility Concerns | 6 |
| Pursue Higher Education | 6 |
| Personal Business Venture | 3 |
| Geographic Relocation | 1 |

#### Regretted Loss by Tenure Band
- More than 6 years: **20** (highest — experienced talent walking out)
- 3 to 6 years: **16**
- 1 to 3 years: **14**
- Less than 1 year: **4**

#### Analysis Focus
- Identifying regretted loss concentration by division, role level, and tenure
- Understanding departure motivations driving high-value employee exits
- Informing targeted retention interventions for Key Players and Top Talent

#### Key Insight
The majority of regretted losses came from employees with 3+ years of tenure, suggesting that long-serving talent is most at risk of being attracted by competitor offers or limited career mobility. February's peak aligns with the post-Year-End Review period — a critical risk window for talent retention.

---

### 4. Risk Group Analysis (0–3 Years YOS)

This section focuses on early-tenure employees (Years of Service ≤ 3), who represent a structural retention vulnerability.

#### Key Metrics (2026 YTD)
- **Total Risk Group Departures**: 161 out of 1,350 employees
- **Risk Group Turnover Rate**: 11.9%
- **Peak Month**: January (54 departures, 4.00%)

#### Monthly Risk Group Trend (Jan–May 2026)
| Month | Departures | Rate |
|---|---|---|
| January | 54 | 4.00% |
| February | 50 | 3.70% |
| March | 21 | 1.56% |
| April | 11 | 0.81% |
| May | 25 | 1.85% |

#### Risk Group Departure by Reason
| Reason | Count |
|---|---|
| Operational Redundancy | 42 |
| Competitor Offer — Better Package | 37 |
| Limited Growth Opportunity | 35 |
| Workload & Flexibility Concerns | 21 |
| Pursue Higher Education | 11 |
| Geographic Relocation | 6 |
| Personal Business Venture | 6 |
| Contract Not Renewed | 1 |

#### Tenure Split within Risk Group
- Less than 1 year: **64** departures
- 1 to 3 years: **97** departures

#### Analysis Focus
- Early-tenure flight risk monitoring
- Onboarding effectiveness signals
- Position class concentration of early departures
- Identifying whether risk group departures are voluntary or driven by restructuring

#### Key Insight
The risk group showed the highest departure volume in January and February — the post-bonus and post-Year-End Review window — suggesting that newly joined employees may reassess career decisions immediately after their first performance cycle. The dominance of "less than 1 year" tenure in this group indicates onboarding retention is a priority area.

---

## Key Business Insights

### 1. Post-Bonus Period Is the Highest Attrition Risk Window
Both overall turnover and regretted loss peaked in January–February, immediately following the Year-End Review and 13th month bonus payout cycle. Organizations must activate retention interventions **before** the bonus period, not after.

---

### 2. Regretted Loss Is Concentrated Among Experienced Employees
More than 67% of regretted loss came from employees with 3+ years of tenure. This signals that career development limitations and competitor compensation gaps are eroding the experienced talent pool — a costly structural issue given replacement costs and knowledge transfer risk.

---

### 3. Early-Tenure Employees Represent a Significant Volume Risk
161 employees within their first 3 years departed in just the first 5 months of 2026 — representing nearly 40% of total departures. This challenges both recruitment ROI and organizational continuity, especially in operational functions like Logistics and Agriculture.

---

### 4. Voluntary Turnover Dominates but Company Decisions Are Concentrated in Food Division
22.6% of turnover was employee-initiated while 7.4% was company-initiated. Company-driven separations were concentrated in the Food Manufacturing division due to restructuring logic — a pattern that may require separate workforce planning responses versus retention programs.

---

### 5. Higher Compensation and Limited Growth Are the Leading Flight Risks
The top two voluntary departure reasons — competitor compensation offers and limited internal career advancement — together accounted for the majority of regretted losses and risk group departures. This reinforces that compensation strategy and career pathing are the two most critical retention levers.

---

## Recommendations & Opportunities

### Retention Strategy
- Build a **pre-bonus retention communication program** for Key Players and high-risk tenure bands (1–3 years) before the January cycle
- Prioritize **career development roadmaps** for high-performing professionals in Technology, Logistics, and Agriculture — the three divisions showing the most growth-related departures
- Conduct **stay interviews** for employees with 3–6 years tenure who have not yet received promotion or significant role expansion

### Workforce Planning
- Monitor the **Risk Group cohort (0–3 YOS)** on a monthly basis, with an early alert if January volume exceeds the prior year's peak
- Design **structured 6-month and 12-month onboarding check-ins** for all new hires to improve first-year retention outcomes
- Align **succession planning** with regretted loss patterns to ensure critical role coverage, especially in Global Key Positions

### HR Analytics Enhancements
Potential future improvements include:
- Predictive attrition modeling using tenure, performance, compa ratio, and promotion lag
- Exit survey sentiment analysis to enrich termination reason classification
- Integration of external salary benchmarks to flag compensation-driven flight risk proactively
- Real-time headcount dashboards with automated alert triggers for abnormal monthly departure spikes
- Cohort survival analysis to measure onboarding program effectiveness over time

---

## Key Learnings

This project allowed me to combine HR domain knowledge with data engineering and business intelligence skills in a workforce analytics context.

### Technical Learnings
- Engineering realistic departure seasonality (peaked probability distributions) requires genuine HR operational knowledge
- Structuring leavers data (EMP906) is significantly more complex than active employee data — termination workflows have many edge cases
- Power BI DAX measures for turnover rates require careful denominator definition (headcount at period start vs. average headcount)
- Dashboard storytelling for HR audiences must balance executive-level KPIs with individual-level drill-down capability

### Business Learnings
- Turnover analysis is most actionable when segmented — overall rates mask critical talent and risk sub-populations
- The "regretted loss" concept is one of the most strategically important HR metrics and is often underreported in standard dashboards
- Early-tenure attrition often signals onboarding and expectation-setting failures rather than compensation issues alone
- Seasonality in departure timing is real, predictable, and actionable — organizations that plan around it retain more talent

### Personal Growth
This project helped me strengthen:
- HR data modeling and termination logic design
- Power BI dashboard architecture for multi-audience consumption (Executive / Operations / HRBP views)
- Python synthetic data generation with business-realistic constraints
- Translating workforce questions into measurable KPIs and visual narratives

---

## Final Reflection

This dashboard represents more than a turnover tracking tool.

It reflects how workforce data, when structured and visualized thoughtfully, can shift HR conversations from reactive headcount reporting to proactive talent risk management.

Through this project, I deepened my understanding of:
- How departure patterns connect to business cycles and compensation events
- How different employee segments require different retention responses
- How data storytelling can make complex workforce dynamics accessible to business leaders

I look forward to continuing to build projects that sit at the intersection of:
- HR Analytics & People Strategy
- Workforce Planning & Retention Design
- Business Intelligence & Data Storytelling

