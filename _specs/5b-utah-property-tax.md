# Spec 5b: Utah Property Tax Estimator (commercial vs. primary residential)

Research done 2026-10-21 by a research job with internet access. Every rule and figure below was read live on
2026-10-21. The build job has no internet: use only what is written here. Do not add any rule, rate or figure that is
not in this file.

## 1. What the page is for (plain English)

In Utah, property tax works like this:
1. The county assessor sets the property's **market value** as of January 1.
2. A home that is someone's **primary residence** (this includes apartments rented to full-time tenants) is taxed on
   only **55%** of that value, because of a 45% "residential exemption". Commercial, industrial and most other property
   is taxed on **100%** of its value.
3. The value being taxed (the **taxable value**) is multiplied by the **tax rate** of the property's **tax area**. A
   tax area is the patch of map where the same set of taxing bodies (county, school district, city, special districts)
   overlap. The rate is a decimal, for example 0.010504, which equals 1.0504% of taxable value.

The calculator estimates a yearly tax from a value, a property type and a rate. It shows the official 2025 low, high
and average rates for seven counties, and explains the appeal deadline.

## 2. Sources read (all read 2026-10-21)

| # | Source | URL | As-of shown on source |
|---|--------|-----|-----------------------|
| U1 | Utah Constitution, Article XIII, Section 2 | https://le.utah.gov/xcode/ArticleXIII/UC_AXIII_S2_1800010118000101.html (current version; index page https://le.utah.gov/xcode/ArticleXIII/Article_XIII,_Section_2.html) | Marked "Current Version" on le.utah.gov |
| U2 | Utah Constitution, Article XIII, Section 3 | https://le.utah.gov/xcode/ArticleXIII/UC_AXIII_S3_2018050820190101.html | Marked "Current Version" |
| U3 | Utah Code 59-2-103 (rate of assessment; residential exemption) | https://le.utah.gov/xcode/Title59/Chapter2/C59-2-S103_2025070120250507.html (index https://le.utah.gov/xcode/Title59/Chapter2/59-2-S103.html) | "Effective 7/1/2025"; "Amended by Chapter 234, 2025 General Session" |
| U4 | Utah Code 59-2-1004 (appeal to county board of equalization) | https://le.utah.gov/xcode/Title59/Chapter2/C59-2-S1004_2026010120250507.html (index https://le.utah.gov/xcode/Title59/Chapter2/59-2-S1004.html) | "Effective 1/1/2026"; "Amended by Chapter 337, 2025 General Session" |
| U5 | Utah Code 59-2-919.1 (valuation notice) | https://le.utah.gov/xcode/Title59/Chapter2/C59-2-S919.1_2026050620260701.html (index https://le.utah.gov/xcode/Title59/Chapter2/59-2-S919.1.html) | Marked "Current Version" (version file code 2026050620260701) |
| U6 | Utah Code 68-3-7 (how time is computed) | https://le.utah.gov/xcode/Title68/Chapter3/C68-3-S7_1800010118000101.html | "Amended by Chapter 236, 2012 General Session" |
| U7 | Utah State Tax Commission, "Tax Rates by Area" page (list of yearly files) | https://tax.utah.gov/propertytax/rates/area-rates/ | Newest file listed: "2025 Tax Rates by Area" |
| U8 | Utah State Tax Commission, "2025 Tax Rates by Tax Area" (Report 600) | https://files.tax.utah.gov/propertytax/tax-rates/area-rates/taxarearates2025.pdf | PDF, 505 pages. Page footer: "January 05, 2026 Report 600 (Area Tax Rates - State)". PDF properties: Title "2025 Tax Rates by Area", Author "Utah State Tax Commission", created 2026-01-09. |
| U9 | Utah State Tax Commission, "2025 Property Tax Annual Statistical Report" | https://files.tax.utah.gov/propertytax/annual-reports/2025annual.pdf (listed on https://tax.utah.gov/propertytax/general/annual-report) | Cover: "August 2026"; "This report provides assessment and property tax collection data for tax year 2025" |
| U10 | Utah State Tax Commission, "Tax Rates & Budgets" page | https://tax.utah.gov/propertytax/rates/approved-rates/ | Shows a "2026 Approved Tax Rates and Budget" table on the page (read through WebFetch; see section 3.4) |
| U11 | Utah State Tax Commission, "Primary Residential Exemption" page | https://tax.utah.gov/propertytax/general/primary-residential-exemption | No date shown (read through WebFetch) |

Notes on reading:
- The old Tax Commission address propertytax.utah.gov now redirects (301) to https://tax.utah.gov/propertytax. Older
  links to propertytax.utah.gov files may not be stable; use the files.tax.utah.gov addresses above.
- tax.utah.gov refused direct scripted reads (HTTP 403), so U7, U10 and U11 were read through WebFetch, which
  summarises pages and can paraphrase. Their quotes below are labelled "(via WebFetch)". The PDFs U8 and U9 were saved
  by WebFetch and their text was pulled out with pdfplumber, so the figures from them are exact.
- le.utah.gov pages (U1 to U6) were read directly, so those quotes are exact (spacing cleaned up only).
- In quotes from the annual report (U9) I left out the small footnote numbers that follow some words (for example the
  source prints "taxable value1" and "45% exemption2").

## 3. The rules, with exact wording

### 3.1 Everything is valued at fair market value (U1, U3, U9)

Utah Constitution, Art. XIII, Sec. 2(1) (U1):

> "(1) So that each person and corporation pays a tax in proportion to the fair market value of his, her, or its tangible property, all tangible property in the State that is not exempt under the laws of the United States or under this Constitution shall be: (a) assessed at a uniform and equal rate in proportion to its fair market value, to be ascertained as provided by law; and (b) taxed at a uniform and equal rate."

Utah Code 59-2-103(2) (U3):

> "(2) All tangible taxable property located within the state shall be assessed and taxed at a uniform and equal rate on the basis of its fair market value, as valued on January 1, unless otherwise provided by law."

2025 Annual Statistical Report, page 2 (U9):

> "All taxable property in Utah is valued at 100 percent of its fair market value, based upon its location and status as of January 1st of each year."

> "Fair market value less any exemptions equals taxable value. Taxable value is the value against which the tax rate is applied to compute taxes charged."

### 3.2 The primary residential exemption: 45% (U2, U3, U9, U11)

Utah Constitution, Art. XIII, Sec. 3(2)(a)(iv) (U2): "The Legislature may by statute exempt the following from property
tax: ... (iv) up to 45% of the fair market value of residential property, as defined by statute;"

Utah Code 59-2-103 (U3), effective 7/1/2025:

> "(3) Subject to Subsections (4) through (6) and Section 59-2-103.5, for a calendar year, the fair market value of residential property located within the state is allowed a residential exemption equal to a 45% reduction in the value of the property."

> "(4) Part-year residential property located within the state is allowed the residential exemption described in Subsection (3) if the part-year residential property is used as residential property for 183 or more consecutive calendar days during the calendar year for which the owner seeks to obtain the residential exemption."

> "(5) No more than one acre of land per residential unit may qualify for the residential exemption described in Subsection (3)."

> "(6) (a) Except as provided in Subsections (6)(b)(ii) and (iii), a residential exemption described in Subsection (3) is limited to one primary residence per household. (b) An owner of multiple primary residences located within the state is allowed a residential exemption under Subsection (3) for: (i) subject to Subsection (6)(a), the primary residence of the owner; (ii) each residential property that is the primary residence of a tenant; and (iii) subject to Subsection 59-2-103.5(4), each residential property described in Subsection 59-2-102(35)(b)(ii)."

2025 Annual Statistical Report, page 2 (U9):

> "Currently, primary residential properties receive a 45% exemption. Primary residential property is any dwelling used as a person's primary residence, including condominiums, apartments and rental property, and includes up to one acre of land. The taxable value of all other properties, except some agricultural land, is assessed at 100% of fair market value."

The same page has a table, "FMV" vs. "Taxable Value": Primary Residential "100% 55%"; All Other Locally Assessed Real
"100% 100%".

Tax Commission exemption page (U11, via WebFetch): "Utah law allows a 45% exemption on the market value of qualifying
primary residential property." and the exemption "reduces the taxable value of eligible primary residences to 55% of
their fair market value." Also: "If the property is used as a residential rental, the owner must submit an approved
residential declaration."

**What this means for the calculator:**
- Commercial, industrial, retail, office and vacant land (not farmland), plus residential property that is *not*
  anyone's primary residence (for example a vacation home): taxable value = 100% of market value.
- Primary residential, including apartments and rentals where a full-time tenant lives as their primary residence:
  taxable value = 55% of market value, on up to one acre of land per unit.
- Farmland assessed under the Farmland Assessment Act is out of scope. The page should say so; do not calculate it.

### 3.3 How the rate is expressed (U9, U8)

2025 Annual Statistical Report, page 3 (U9): "Tax rates are expressed as a percentage of taxable value."

In the rate file (U8) each rate is a decimal, for example "Total for Tax Area 001 - 0000 0.007335 0.007335 0.007335".
The three columns are headed "Certified Rate", "Auditor's Proposed Rate" and "Final Adopted Tax Rate". **Use the last
column (Final Adopted Tax Rate).**

Formula: `estimated tax = taxable value × rate` (with the rate as a decimal; 0.010504 = 1.0504%).

Statewide context, 2025 Annual Statistical Report page 3 (U9), "Taxes Charged / Tax Rates" table:
- "Primary Residential ... Actual % 0.94% ... Effective % 0.52%"
- "Commercial ... Actual % 0.94% ... Effective % 0.94%"
- The report notes: "Effective tax rates are a percentage of fair market value."

In plain English: statewide in 2025, homes and commercial property paid about the same rate on their taxable value
(0.94%). But because a home is taxed on only 55% of its value, its tax measured against full market value was 0.52%,
while commercial property's was 0.94%.

### 3.4 Where the official rates are published

**Newest by-tax-area file: 2025.**
- Page listing the files (U7): https://tax.utah.gov/propertytax/rates/area-rates/. Its newest link is "2025 Tax Rates
  by Area". Older years go back to 2003, all PDF.
- File (U8): https://files.tax.utah.gov/propertytax/tax-rates/area-rates/taxarearates2025.pdf. Format: **PDF**, 505
  pages, one block per tax area per county, every taxing entity listed with three rate columns and a "Total for Tax
  Area" line.

**County averages and ranges, official:** 2025 Annual Statistical Report (U9), Table 4, "UTAH AVERAGE TAX RATE BY
COUNTY FOR 2025" (report page 34), and Table 5, "HISTORICAL AVERAGE TAX RATES BY COUNTY" (report page 35). PDF.

**2026 rates by entity (not by tax area):** the "Tax Rates & Budgets" page (U10) shows a table headed "2026 Approved Tax
Rates and Budget". Its columns are Tax Year, County, Entity Code, Entity Name, Budget Code, Budget Name, Final Rate,
Final Budgeted Revenue (via WebFetch). This is per taxing entity, not per tax area, so you cannot read a property's
total 2026 rate from it. The newest PDF on that page is "2025 Approved Tax Rates & Budgets"
(https://files.tax.utah.gov/propertytax/tax-rates/approved-rates/budgetratesbyentity2025.pdf). **Do not use the 2026
entity table on the page.** A 2026 by-tax-area file was not listed on 2026-10-21.

### 3.5 2025 total tax rates for the seven counties (official, exact)

Source: U9, Table 4, "UTAH AVERAGE TAX RATE BY COUNTY FOR 2025". Figures are copied exactly as printed. Columns:
NUMBER OF TAX AREAS / COUNTY MINIMUM TAX RATE / COUNTY MAXIMUM TAX RATE / AVERAGE TAX RATES.

| County | Number of tax areas | Minimum tax rate | Maximum tax rate | Average tax rates |
|--------|--------------------:|-----------------:|-----------------:|------------------:|
| BOX ELDER | 79 | 0.009188 | 0.011779 | 0.010112 |
| DAVIS | 128 | 0.007780 | 0.011159 | 0.010108 |
| SALT LAKE | 406 | 0.008035 | 0.020826 | 0.010504 |
| TOOELE | 75 | 0.009951 | 0.015497 | 0.011568 |
| UTAH | 152 | 0.007650 | 0.025019 | 0.009621 |
| WASHINGTON | 72 | 0.00583 | 0.017004 | 0.007584 |
| WEBER | 282 | 0.008601 | 0.012770 | 0.010371 |
| STATEWIDE | 1727 | (blank) | (blank) | 0.009025 |

(Washington's minimum is printed as "0.00583" in Table 4. The same rate appears as "0.005830" in the rate file, U8.
Same value.)

The same seven counties, prior year, from U9 Table 5 "HISTORICAL AVERAGE TAX RATES BY COUNTY" (2025 / 2024 columns,
exact): Box Elder 0.010112 / 0.008928; Davis 0.010108 / 0.009969; Salt Lake 0.010504 / 0.010662; Tooele 0.011568 /
0.012632; Utah 0.009621 / 0.009548; Washington 0.007584 / 0.007595; Weber 0.010371 / 0.010220; Statewide average
0.009025 / 0.009275.

**Checks I ran on these numbers (2026-10-21, Python + pdfplumber on U8):**
- The lowest and highest "Final Adopted Tax Rate" tax-area totals in U8 match Table 4's minimum and maximum for all
  seven counties. My tax-area counts match Table 4 for six counties; for Utah County I read 151 areas against Table
  4's 152.
- **The "average" in Table 4 is a simple average across tax areas, not weighted by property value.** My plain average
  of the tax-area totals reproduces Table 4's average exactly for Box Elder, Davis, Salt Lake, Tooele, Washington and
  Weber (Utah: 0.009620 from my 151 areas against 0.009621 printed). The report's table of contents calls Table 4
  "Utah Weighted Average Tax Rates for 2025", but the table's own heading says "UTAH AVERAGE TAX RATE BY COUNTY FOR
  2025". So label it "average tax-area rate", **not** "the typical rate" or "weighted average".

**Why some county maximums are so high (from U8, exact lines):** the top rate in four counties comes from a tax area
that includes a public infrastructure district (a special district created to pay for a new development's
infrastructure):
- Salt Lake, Tax Area 70E - 0000, total 0.020826, includes "5020 AUTO-MALL PUBLIC INFRASTRUCTURE DISTRICT 0.010000".
- Utah, Tax Area 113 - 0000, total 0.025019, includes "5000 MEDICAL SCHOOL CAMPUS PUBLIC INFRASTRUCTURE DISTRICT 0.015000".
- Tooele, Tax Area 059 - 0000, total 0.015497, includes "5000 OQUIRRH-POINT PUBLIC INFRASTRUCTURE DISTRICT NO 1 0.004000".
- Washington, Tax Area 065 - 0000, total 0.017004, includes "5015 BLACK DESERT PUBLIC INFRASTRUCTURE DISTRICT 0.010000".

Optional, if Stockton wants it: highest 2025 tax-area totals **leaving out tax areas that include a 5000-series
(infrastructure) district**. I worked these out from U8; they are not an official Tax Commission statistic, so label
them "calculated by Team Utah Commercial from the Tax Commission's 2025 rate file". Salt Lake 0.013694 (Tax Area 026 -
0000); Utah 0.012029 (Tax Area 155 - 0000); Tooele 0.014385 (Tax Area 007 - 0000); Washington 0.013777 (Tax Area 054 -
0000). For Davis, Box Elder and Weber the maximum does not change (Davis and Box Elder have no 5000-series district;
Weber's are all at 0.000000). The lowest rates do not change in any of the seven counties.

### 3.6 Appeal deadline: county board of equalization (U4, U5, U6)

Utah Code 59-2-1004(2)(a) (U4), effective 1/1/2026:

> "(2) (a) A taxpayer dissatisfied with the valuation or the equalization of the taxpayer's real property may make an application to appeal by: (i) subject to Subsection (2)(d), filing the application with the county board of equalization within the time period described in Subsection (3); or (ii) making an application by telephone within the time period described in Subsection (3) if the county legislative body passes a resolution under Subsection (11) authorizing a taxpayer to make an application by telephone."

Utah Code 59-2-1004(3) (U4), **the deadline rule**:

> "(3) (a) Except as provided in Subsection (3)(b) and for purposes of Subsection (2), a taxpayer shall make an application to appeal the valuation or the equalization of the taxpayer's real property on or before the later of: (i) September 15 of the current calendar year; or (ii) the last day of a 45-day period beginning on the day on which the county auditor provides the notice under Section 59-2-919.1. (b) In accordance with Title 63G, Chapter 3, Utah Administrative Rulemaking Act, the commission shall make rules providing for circumstances under which the county board of equalization is required to accept an application to appeal that is filed after the time period prescribed in Subsection (3)(a)."

What the appeal must include, 59-2-1004(4)(a)(i) (U4):

> "the taxpayer's estimate of the fair market value of the property and any evidence that may indicate that the assessed valuation of the taxpayer's property is improperly equalized with the assessed valuation of comparable properties"

The valuation notice, 59-2-919.1 (U5):

> "(1) On or before July 22 of each year, in addition to the notice requirements of Section 59-2-919, the county auditor shall notify each owner of real estate who is listed on the assessment roll."

The same section, (2)(c)(iii), says that for property the county assessor values, the notice must contain "(B) the
deadline for the taxpayer to make an application to appeal the valuation or equalization of the property under Section
59-2-1004".

How Utah counts days, 68-3-7 (U6):

> "(1) A person shall compute the period of time provided by law to perform an act by: (a) excluding the first day; and (b) except as provided in Subsection (2), including the last day. (2) If the last day is a legal holiday, a Saturday, or a Sunday, then a person shall: (a) exclude the day described in this Subsection (2) from the time computation described in Subsection (1); and (b) compute the period of time to include the end of the next day that is not a legal holiday, a Saturday, or a Sunday."

**What this means for the calculator (plain English):** the deadline to appeal your value to the county board of
equalization is September 15, or 45 days after your valuation notice if that is later. Because notices go out by July
22, September 15 is normally the deadline. Your valuation notice prints your exact deadline, so that is the date to
trust. Commercial owners follow the same rule.

Day-counting caution. 59-2-1004 says the 45-day period begins "on the day on which the county auditor provides the
notice", while 68-3-7 says to exclude the first day. So the 45-day date is either notice date + 44 or notice date + 45
days. For example, a July 22, 2026 notice gives Friday, September 4, 2026 or Saturday, September 5, 2026 (which 68-3-7
would push to the next day that is not a weekend or legal holiday). Either way it is earlier than September 15, 2026,
so September 15 controls. Only a notice dated around August 2 or later could make the 45-day date later than September
15 (August 2 + 45 days = September 16; August 3 + 44 days = September 16; checked with Python). I could not confirm
which count is right, or whether 68-3-7 moves a fixed September 15 date that lands on a weekend. September 15 falls on a
Saturday in 2029 and a Sunday in 2030 (checked with Python). **So the page should not compute an appeal date. It
should state the rule and tell people to use the deadline on their notice.**

## 4. Calculator inputs and outputs

### Inputs

| # | Field | Type | Required | Notes |
|---|-------|------|----------|-------|
| P1 | County | dropdown: Box Elder, Davis, Salt Lake, Tooele, Utah, Washington, Weber, Other Utah county | yes | "Other" hides the county rate box and requires P4. |
| P2 | Property type | choice: (a) "Commercial, industrial, office, retail or vacant land" (default); (b) "Primary residence: a home, condo or apartment where the owner or a full-time tenant lives as their main home"; (c) "Residential, but not anyone's primary residence (for example a vacation home)" | yes | Help text for (b): "Apartments and rentals count if a full-time tenant lives there as their primary residence (Utah Code 59-2-103(6)(b)(ii)). Your county may require a residential declaration." |
| P3 | Market value from your valuation notice or the assessor's records | dollars | yes | Help text: "Utah values property as of January 1." |
| P4 | Your tax rate | decimal (e.g., 0.010504) or percent, with a toggle | yes for "Other"; otherwise optional | Help text: "Your exact rate is on your valuation notice or tax bill. It depends on your tax area." |
| P5 | If you don't know your rate, use: | choice: County average (2025) [default] / County low (2025) / County high (2025) | shown when P4 is empty and P1 is not "Other" | Values from section 3.5. |

### Logic

1. `share = 0.55` if P2 = (b), else `1.00`. (Source: U3 (3); U9 page 2.)
2. `taxable_value = P3 × share`.
3. `rate = P4` if entered (convert a percent to a decimal by dividing by 100), else the Table 4 value picked in P5.
4. `estimated_tax = taxable_value × rate`, rounded to cents.
5. Comparison line: compute the tax on the same P3 at the same rate with share 1.00 and with share 0.55, and show both
   ("Same value taxed as commercial: $X. As a primary residence: $Y.").
6. If the rate came from P5, label the result "Estimate using the 2025 [average/low/high] tax-area rate for [County]
   County".

### Outputs

- Taxable value (and the share used: 100% or 55%).
- Rate used, shown both ways (e.g., "0.010504 (1.0504%)") with its source.
- Estimated yearly property tax.
- The commercial vs. primary-residence comparison line.
- County rate box (P1 not "Other"): "2025 tax-area rates in [County] County: lowest [min], highest [max], average
  [avg] across [n] tax areas." Then: "The highest rates are in new-development areas with a public infrastructure
  district." Show that second sentence only for Salt Lake, Utah, Tooele and Washington (see section 3.5).
- Appeal box (static text, no date math): "Think your value is too high? You can appeal to your county board of
  equalization. The deadline is September 15, or 45 days after your valuation notice if that is later. Use the
  deadline printed on your notice. You'll need your own estimate of the property's value and evidence such as
  comparable sales." (Source: Utah Code 59-2-1004(3)(a) and (4)(a), read October 21, 2026.)
- Source line under the results (rule 7): "Rates: Utah State Tax Commission, 2025 Property Tax Annual Statistical
  Report, Table 4 (published August 2026), and 2025 Tax Rates by Tax Area. Rules: Utah Code 59-2-103 and 59-2-1004.
  Read October 21, 2026." Each one links to its URL in section 2.

### Test cases

| Test | Input | Expected |
|------|-------|----------|
| T1 | Salt Lake; (a) commercial; P3 = 1,000,000; P5 = average | rate 0.010504; taxable 1,000,000.00; tax $10,504.00 |
| T2 | Salt Lake; (b) primary residence; P3 = 500,000; P5 = average | taxable 275,000.00; tax $2,888.60 |
| T3 | Washington; (a); P3 = 2,000,000; P5 = low | rate 0.005830; tax $11,660.00 |
| T4 | Utah; (a); P3 = 1,000,000; P5 = high | rate 0.025019; tax $25,019.00; the infrastructure-district sentence shows |
| T5 | Other county; (a); P3 = 750,000; P4 = 1.2 (percent) | rate 0.012; tax $9,000.00 |
| T6 | Davis; (c) not a primary residence; P3 = 400,000; P5 = average | share 1.00; rate 0.010108; tax $4,043.20 |

(T1 to T4 were computed with Python on 2026-10-21. T5 and T6 are simple arithmetic: 750,000 × 0.012 = 9,000.00;
400,000 × 0.010108 = 4,043.20.)

## 5. Disclaimer text

"This is an estimate for general information only, not tax, legal or appraisal advice. Your actual tax depends on the
value your county assessor sets, your exact tax area's rate, exemptions you qualify for, and rates adopted after the
2025 figures shown here (Utah State Tax Commission, read October 21, 2026). Check your county valuation notice and tax
bill, and contact your county assessor or a tax professional before relying on these numbers. Team Utah Commercial and
RE/MAX Associates do not give tax advice."

(Rule 8 still applies: if a phone number is added near this disclaimer, "RE/MAX Associates" must appear with it.)

## 6. Could not confirm (do not put these on the page)

- **2026 total rates by tax area.** Not published on 2026-10-21 (newest file is 2025). The 2026 table on U10 is per
  entity and was read only through WebFetch.
- **Exact wording on tax.utah.gov HTML pages (U7, U10, U11).** Read through WebFetch only (direct reads got HTTP 403),
  so those short quotes may be paraphrased. All figures used for math come from the PDFs (U8, U9), which were
  extracted exactly.
- **Whether the 45-day appeal period counts the notice day, and whether a September 15 that lands on a weekend
  moves.** 59-2-1004 and 68-3-7 point different ways (see 3.6). The page should not compute an appeal date.
- **Tax Commission rules on late appeals** (the rules mentioned in 59-2-1004(3)(b)). Not read today.
- **Farmland (Farmland Assessment Act) values** and **personal property** (business equipment) are out of scope; not
  researched.
- The Tax Commission's own property tax calendar PDF (https://files.tax.utah.gov/propertytax/media/property-tax-calendar.pdf)
  agrees with the September 15 / 45-day rule, but it is marked "Revised 02/14/2024", so I relied on the statute instead.
