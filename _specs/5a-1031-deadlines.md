# Spec 5a: 1031 Exchange Deadline Calculator

Research done 2026-10-21 by a research job with internet access. Every rule below was read live on 2026-10-21.
The build job has no internet: use only what is written here. Do not add any rule, date or figure that is not in this file.

## 1. What the page is for (plain English)

When an owner sells investment or business real estate and wants to defer the tax with a 1031 exchange, two clocks
start on the day the sale closes:

- **Day 45**: by the end of this day the owner must name, in writing, the replacement properties they might buy.
- **Day 180**: by the end of this day the owner must have received (closed on) the replacement property. But if the
  owner's tax return for the year of the sale is due earlier (and they don't extend it), that earlier due date is the
  real deadline.

The calculator takes the sale closing date and shows both deadlines, warns when a deadline lands on a weekend or
federal holiday (the deadline does **not** move), and checks a list of identified properties against the
3-property / 200% / 95% rules.

## 2. Sources read (all read 2026-10-21)

| # | Source | URL | As-of shown on source |
|---|--------|-----|-----------------------|
| S1 | 26 U.S.C. 1031 (Cornell LII) | https://www.law.cornell.edu/uscode/text/26/1031 | No currency date shown on the page text I extracted. Amendment note: Pub. L. 115-97 (2017) substituted "real property" for "property". |
| S2 | 26 CFR 1.1031(k)-1 (Cornell LII copy of the e-CFR) | https://www.law.cornell.edu/cfr/text/26/1.1031(k)-1 | No "current as of" date shown. |
| S3 | IRS, Instructions for Form 8824 (2025) | https://www.irs.gov/instructions/i8824 | "Page Last Reviewed or Updated: 30-Apr-2026" |
| S4 | IRS Fact Sheet FS-2008-18, "Like-Kind Exchanges Under IRC Code Section 1031" | https://www.irs.gov/newsroom/like-kind-exchanges-under-irc-code-section-1031 (reached from https://www.irs.gov/node/5256) | Dated "FS-2008-18, February 2008". The IRS marks it: "Notice: Historical Content This is an archival or historical document and may not reflect current law, policies or procedures." It points to the page in S5 "for updated information." |
| S5 | IRS, "Like-Kind Exchanges - Real Estate Tax Tips" | https://www.irs.gov/businesses/small-businesses-self-employed/like-kind-exchanges-real-estate-tax-tips | "Page Last Reviewed or Updated: 01-May-2026" |
| S6 | IRS Rev. Proc. 2018-58 (disaster postponements) | https://www.irs.gov/pub/irs-drop/rp-18-58.pdf | Section 20: "This revenue procedure is effective for acts that may be performed or disasters which occur on or after November 20, 2018." |
| S7 | IRS, "When to file" (individuals) | https://www.irs.gov/filing/individuals/when-to-file | "Page Last Reviewed or Updated: 22-May-2026" |
| S8 | 5 U.S.C. 6103 (federal legal public holidays, Cornell LII) | https://www.law.cornell.edu/uscode/text/5/6103 | No currency date shown. |

Not usable today: uscode.house.gov returned a "Page Not Found" page (which said "The United States Code Online is
current through Public Law 119-120 (October 7, 2026)") and then a "site you requested is currently unavailable"
maintenance page. The official eCFR (ecfr.gov) redirected automated reads to a block page, so I could not compare the
Cornell copy of the regulation against ecfr.gov.

Quote note: quotes are copied from the page text. Only line breaks and spacing were cleaned up. The Cornell copy of
the regulation has typos ("relinguished", "vlaue", "othewise", "unambigously"); I kept them and marked them [sic].

## 3. The rules, with exact wording

### 3.1 The statute: 45 days and 180 days (S1, 26 U.S.C. 1031(a)(3))

> "(3) Requirement that property be identified and that exchange be completed not more than 180 days after transfer of exchanged property
> For purposes of this subsection, any property received by the taxpayer shall be treated as property which is not like-kind property if—
> (A) such property is not identified as property to be received in the exchange on or before the day which is 45 days after the date on which the taxpayer transfers the property relinquished in the exchange, or
> (B) such property is received after the earlier of—
> (i) the day which is 180 days after the date on which the taxpayer transfers the property relinquished in the exchange, or
> (ii) the due date (determined with regard to extension) for the transferor’s return of the tax imposed by this chapter for the taxable year in which the transfer of the relinquished property occurs."

Related wording in the same section (S1):

> "(1) In general No gain or loss shall be recognized on the exchange of real property held for productive use in a trade or business or for investment if such real property is exchanged solely for real property of like kind which is to be held either for productive use in a trade or business or for investment."

> "(2) Exception for real property held for sale This subsection shall not apply to any exchange of real property held primarily for sale."

> "(h) ... Real property located in the United States and real property located outside the United States are not property of a like kind."

### 3.2 The regulation: when each period starts and ends (S2, 26 CFR 1.1031(k)-1(b)(2))

> "(i) The identification period begins on the date the taxpayer transfers the relinquished property and ends at midnight on the 45th day thereafter."

> "(ii) The exchange period begins on the date the taxpayer transfers the relinquished property and ends at midnight on the earlier of the 180th day thereafter or the due date (including extensions) for the taxpayer's return of the tax imposed by chapter 1 of subtitle A of the Code for the taxable year in which the transfer of the relinquished property occurs."

> "(iii) If, as part of the same deferred exchange, the taxpayer transfers more than one relinquished property and the relinquished properties are transferred on different dates, the identification period and the exchange period are determined by reference to the earliest date on which any of the properties are transferred."

> "(iv) For purposes of this paragraph (b)(2), property is transferred when the property is disposed of within the meaning of section 1001(a)."

The regulation's own worked example (S2, 1.1031(k)-1(b)(3)). Use it as a test case:

> "M transfers property X to C on November 16, 1992."
> "(ii) The identification period ends at midnight on December 31, 1992, the day which is 45 days after the date of transfer of property X. The exchange period ends at midnight on March 15, 1993, the due date for M's Federal income tax return for the taxable year in which M transferred property X. However, if M is allowed the automatic six-month extension for filing its tax return, the exchange period ends at midnight on May 15, 1993, the day which is 180 days after the date of transfer of property X."

What this means for the math: day 45 = closing date + 45 calendar days; day 180 = closing date + 180 calendar days.
(Checked with Python: 1992-11-16 + 45 days = 1992-12-31, and + 180 days = 1993-05-15, which matches the example.)

### 3.3 IRS plain-language versions (S3 and S4)

Form 8824 instructions (2025), "Deferred Exchanges" (S3):

> "For real property associated with a deferred exchange to qualify as like kind, you must comply with the timing requirements for identification and receipt of replacement property. The replacement property for the exchange must be identified within 45 days after the property being given up is transferred. The replacement property must be received within 180 days, or by the due date of your tax return (including extensions), whichever is earlier."

Form 8824 instructions, Line 6 (S3):

> "The property must be received by the earlier of the following dates. The 180th day after the date you transferred the property given up in the exchange. The due date (including extensions) of your tax return for the year in which you transferred the property given up."

IRS FS-2008-18 (S4, which the IRS now marks as historical content):

> "The second limit is that the replacement property must be received and the exchange completed no later than 180 days after the sale of the exchanged property or the due date (with extensions) of the income tax return for the tax year in which the relinquished property was sold, whichever is earlier."

### 3.4 Weekends, holidays and extensions: what the IRS says

1. **IRS statement that the limits cannot be extended** (S4, FS-2008-18, February 2008, marked historical by the IRS):
   > "These limits cannot be extended for any circumstance or hardship except in the case of presidentially declared disasters."
2. **The regulation sets a fixed end time and has no weekend or holiday rule** (S2): each period "ends at midnight on
   the 45th day thereafter" / "the 180th day thereafter". I read all of (b)(2) and it has no rule about Saturdays,
   Sundays or holidays. In the regulation's own example the 180th day, May 15, 1993, was a Saturday (checked with
   Python), and the example still gives that day as the end of the exchange period.
3. **Form 8824 instructions (2025)** (S3): they say nothing about weekends or holidays.
4. **The only IRS extension: federally declared disasters** (S6, Rev. Proc. 2018-58, section 17.02(1)):
   > "The last day of a 45-day identification period set forth in § 1.1031(k)-1(b)(2)(i) of the Income Tax Regulations, the last day of a 180-day exchange period set forth in § 1.1031(k)-1(b)(2)(ii), and the last day of a period set forth in section 4.02(3) through (6) of Rev. Proc. 2000-37, 2000-2 C.B. 308, modified by Rev. Proc. 2004-51, 2004-2 C.B. 294, that fall on or after the date of a federally declared disaster, are postponed by 120 days or to the last day of the general disaster extension period authorized by an IRS News Release or other guidance announcing tax relief for victims of the specific federally declared disaster, whichever is later. However, in no event may a postponement period extend beyond: (a) the due date (including extensions) of the taxpayer’s tax return for the year of the transfer (See § 1.1031(k)-1(b)(2)(ii)); or (b) one year (See section 7508A(a))."

   Section 17.01 says this relief applies "if an IRS News Release or other guidance provides relief for acts listed in
   this revenue procedure". So it only applies when the IRS announces disaster relief for a particular disaster.

**Rule for the calculator:** never move a deadline to the next business day. If day 45 or the exchange deadline falls
on a Saturday, Sunday or federal legal holiday, show a warning (wording in section 5). Do not try to model disaster
postponements; just mention them in a note.

Federal legal public holidays, for the warning only (S8, 5 U.S.C. 6103(a)):

> "New Year’s Day, January 1. Birthday of Martin Luther King, Jr., the third Monday in January. Washington’s Birthday, the third Monday in February. Memorial Day, the last Monday in May. Juneteenth National Independence Day, June 19. Independence Day, July 4. Labor Day, the first Monday in September. Columbus Day, the second Monday in October. Veterans Day, November 11. Thanksgiving Day, the fourth Thursday in November. Christmas Day, December 25."

(Section 6103(b) has the "observed on Friday/Monday" rules, but they apply only "For the purpose of statutes relating
to pay and leave of employees". For the warning, flag the actual date listed above, and also flag Saturday and Sunday.)

### 3.5 Tax return due date (needed for the "earlier of" test) (S7)

> "Calendar year filers (most common) File on: April 15, 2026"
> "Fiscal year filers File on: The fourth month after your fiscal year ends, day 15. If day 15 falls on a Saturday, Sunday or legal holiday, the due date is delayed until the next business day."
> "If you can't file by the due date of your return, you can request an automatic 6-month extension of time to file."

How the calculator uses this:
- For "Individual, calendar year": return due date = April 15 of the year after the year of the sale. The S7 page
  shows "April 15, 2026" for returns filed in 2026. For other years the calculator applies the same April 15 rule;
  that is my reading of S7, not a date the IRS page prints.
- If the user says they will extend: the extended due date is 6 months later (October 15 of the following year; that
  is my arithmetic from the "automatic 6-month extension" sentence above). For a calendar-year individual, day 180 is
  always earlier than that date, so with an extension the deadline is simply day 180.
- I could not confirm whether the "delayed until the next business day" rule for the return due date also moves the
  1031 limit. The calculator uses April 15 itself (the earlier, safer date) and shows a note when April 15 falls on a
  weekend or holiday.
- Business entities and fiscal-year filers: I did not read IRS due-date pages for partnerships, S corporations or C
  corporations today. So the calculator must ask those users to type in their own return due date. It must not
  guess one.

### 3.6 Identification rules (S2, 26 CFR 1.1031(k)-1(c))

How to identify, (c)(2):

> "Replacement property is identified only if it is designated as replacement property in a written document signed by the taxpayer and hand delivered, mailed, telecopied, or otherwise sent before the end of the identification period to either— (i) The person obligated to transfer the replacement property to the taxpayer (regardless of whether that person is a disqualified person as defined in paragraph (k) of this section); or (ii) Any other person involved in the exchange other than the taxpayer or a disqualified person (as defined in paragraph (k) of this section). Examples of persons involved in the exchange include any of the parties to the exchange, an intermediary, an escrow agent, and a title company."

How to describe it, (c)(3):

> "Replacement property is identified only if it is unambiguously described in the written document or agreement. Real property generally is unambiguously described if it is described by a legal description, street address, or distinguishable name (e.g., the Mayfair Apartment Building)."

Property received early counts as identified, (c)(1):

> "However, any replacement property that is received by the taxpayer before the end of the identification period will in all events be treated as identified before the end of the identification period."

The 3-property and 200-percent rules, (c)(4)(i):

> "The taxpayer may identify more than one replacement property. Regardless of the number of relinguished [sic] properties transferred by the taxpayer as part of the same deferred exchange, the maximum number of replacement properties that the taxpayer may identify is— (A) Three properties without regard to the fair market values of the properties (the “3-property rule”), or (B) Any number of properties as long as their aggregate fair market value as of the end of the identification period does not exceed 200 percent of the aggregate fair market value of all the relinguished [sic] properties as of the date the relinguished [sic] properties were transferred by the taxpayer (the “200-percent rule”)."

What happens if you identify too many, and the 95-percent rule, (c)(4)(ii):

> "If, as of the end of the identification period, the taxpayer has identified more properties as replacement properties than permitted by paragraph (c)(4)(i) of this section, the taxpayer is treated as if no replacement property had been identified. The preceding sentence will not apply, however, and an identification satisfying the requirements of paragraph (c)(4)(i) of this section will be considered made, with respect to— (A) Any replacement property received by the taxpayer before the end of the identification period, and (B) Any replacement property identified before the end of the identification period and received before the end of the exchange period, but only if the taxpayer receives before the end of the exchange period identified replacement property the fair market vlaue [sic] of which is at least 95 percent of the aggregate fair market value of all identified replacement properties (the “95-percent rule”). For this purpose, the fair market value of each identified replacement property is determined as of the earlier of the date the property is received by the taxpayer or the last day of the exchange period."

Revoked identifications don't count, (c)(4)(iii):

> "For purposes of applying the 3-property rule, the 200-percent rule, and the 95-percent rule, all identifications of replacement property, other than identifications of replacement property that have been revoked in the manner provided in paragraph (c)(6) of this section, are taken into account."

Revoking, (c)(6):

> "An identification of replacement property may be revoked at any time before the end of the identification period. An identification of replacement property is revoked only if the revocation is made in a written document signed by the taxpayer and hand delivered, mailed, telecopied, or othewise [sic] sent before the end of the identification period to the person to whom the identification of the replacement property was sent."

IRS plain-language version of who gets the notice (S4, historical):

> "The identification must be in writing, signed by you and delivered to a person involved in the exchange like the seller of the replacement property or the qualified intermediary. However, notice to your attorney, real estate agent, accountant or similar persons acting as your agent is not sufficient."

### 3.7 Real property only (S5)

> "Under the Tax Cuts and Jobs Act, Section 1031 now applies only to exchanges of real property and not to exchanges of personal or intangible property."

> "However, real property in the United States is not like-kind to real property outside the United States."

## 4. Calculator inputs and outputs

### Inputs

| # | Field | Type | Required | Notes |
|---|-------|------|----------|-------|
| I1 | Closing date of the property you sold (the "relinquished property") | date | yes | Help text: "If you sold more than one property in the same exchange, enter the earliest closing date." (S2, (b)(2)(iii)) |
| I2 | Who files the tax return for the sale? | choice: "An individual, calendar-year return (Form 1040)" (default) / "A business entity, or a fiscal-year filer" | yes | |
| I3 | Will you extend your tax return for the year of the sale? | choice: Yes / No / Not sure (default "Not sure") | shown when I2 = individual | |
| I4 | Your tax return due date for the year of the sale, including any extension | date | required when I2 = entity/fiscal | Help text: "Ask your CPA. This calculator does not guess entity due dates." |
| I5 | Value of the property you sold (fair market value at closing) | dollars | optional (needed for the 200% / 95% check) | If several properties were sold, add them up. |
| I6 | Replacement properties you identified: name or address, and fair market value | repeating rows (up to 10) | optional | Name/address is only for display; the math uses the values. |

### Logic

1. `id_deadline = I1 + 45 days` (calendar days).
2. `day180 = I1 + 180 days` (calendar days).
3. Return due date:
   - Individual: `due = April 15 of (year of I1 + 1)`; `due_ext = October 15 of (year of I1 + 1)`.
   - Entity/fiscal: `due_user = I4` (already includes any extension).
4. Exchange deadline:
   - Individual + "No" extension: `min(day180, due)`.
   - Individual + "Yes": `min(day180, due_ext)` (this always equals day180 for calendar-year individuals, but compute it anyway).
   - Individual + "Not sure": show both results side by side and explain the difference.
   - Entity/fiscal: `min(day180, due_user)`.
5. For each date shown (id_deadline, exchange deadline, and `due` when it is the binding date): if the weekday is
   Saturday or Sunday, or the date is a federal legal holiday from section 3.4, set a warning flag. **Never move the date.**
6. `days_left = date - today` for each deadline; if it is negative, show "This date has passed."
7. Identification check (only if I6 has at least one row):
   - `n = number of rows`, `total = sum of row values`.
   - If `n <= 3`: "Within the 3-property rule."
   - Else if I5 is given and `total <= 2 * I5`: "Within the 200% rule (identified total $X is not more than 200% of $I5 = $Y)."
   - Else: "This list goes beyond both the 3-property rule and the 200% rule. Under the regulation you are treated as
     if you identified nothing, unless you meet an exception such as the 95% rule: you would have to receive at least
     95% of $total = $Z of the identified property by the exchange deadline." (`Z = 0.95 * total`)
   - If I5 is missing and n > 3: ask for I5.
8. When the return due date is the binding limit (individual, no extension, `due < day180`), show this sentence:
   "Because your sale closed late in the year, your tax return due date comes before day 180. Filing an extension
   keeps the full 180 days." Example: for a calendar-year individual, any 2026 sale closing on or after October 18,
   2026 has its day 180 after April 15, 2027 (checked: 2027-04-15 minus 180 days = 2026-10-17).

### Outputs (what the page shows)

- Identification deadline (day 45): date, weekday, days left, and the weekend/holiday warning if flagged.
- Day 180: date, weekday.
- Tax return due date used, and whether it or day 180 controls.
- Exchange deadline (receive the replacement property by): date, weekday, days left, warning if flagged.
- Identification check result (if values entered).
- A short "How to identify" box built from the quotes in section 3.6: in writing, signed, delivered before the end of
  day 45 to the seller of the replacement property or another person in the exchange (such as the intermediary,
  escrow agent or title company), not to your own agent, and described clearly by legal description, street address
  or a distinguishable name.
- Source line under the results (rule 7): "Rules: 26 U.S.C. 1031(a)(3); 26 CFR 1.1031(k)-1(b)(2) and (c); IRS
  Instructions for Form 8824 (2025). Sources read October 21, 2026." Each one links to its URL in section 2.

### Suggested warning and note wording (plain English)

- Weekend/holiday: "This date is a [Saturday / Sunday / federal holiday]. The deadline does not move to the next
  business day. Plan to finish before it."
- Disaster note: "The IRS can postpone these deadlines only when it announces relief for a federally declared
  disaster (Rev. Proc. 2018-58, section 17). Check with your qualified intermediary or CPA if a disaster affects you."
- Return due date note: "If April 15 falls on a weekend or holiday, the IRS moves the filing date to the next business
  day. Ask your CPA whether that changes your exchange deadline. This calculator uses April 15."

### Test cases (the build job should check its page against these)

| Test | Input | Expected |
|------|-------|----------|
| T1 (the regulation's example) | I1 = 1992-11-16; entity; I4 = 1993-03-15 | Day 45 = 1992-12-31 (Thursday). Day 180 = 1993-05-15. Exchange deadline = 1993-03-15. |
| T1b | Same, but I4 = 1993-05-15 or later (extended) | Exchange deadline = 1993-05-15 (Saturday, so the warning shows) |
| T2 | I1 = 2026-10-21; individual; extension = No | Day 45 = 2026-12-05 (Saturday, so the warning shows). Day 180 = 2027-04-19. Due date = 2027-04-15. Exchange deadline = 2027-04-15 (Thursday). Show the "late in the year" sentence. |
| T2b | Same, extension = Yes | Exchange deadline = 2027-04-19 (Monday) |
| T3 | I1 = 2026-06-01; individual; No | Day 45 = 2026-07-16. Day 180 = 2026-11-28 (Saturday, so the warning shows). Exchange deadline = 2026-11-28. |
| T4 | I1 = 2026-12-31; individual; No | Day 45 = 2027-02-14 (Sunday, so the warning shows). Day 180 = 2027-06-29. Exchange deadline = 2027-04-15. |
| T4b | Same, Yes | Exchange deadline = 2027-06-29 |
| T5 | I5 = 1,000,000; I6 = 600,000 / 500,000 / 500,000 / 300,000 | n = 4, total = 1,900,000, not more than 2,000,000, so within the 200% rule |
| T6 | I5 = 1,000,000; I6 = five rows totalling 2,500,000 | Beyond both rules. 95% amount = 2,375,000 |
| T7 | I5 = 1,000,000; I6 = 3 rows totalling 9,000,000 | Within the 3-property rule (values don't matter for 3 or fewer) |

All dates above were computed with Python on 2026-10-21.

## 5. Disclaimer text

"This calculator is general information, not tax or legal advice. It counts calendar days under 26 U.S.C. 1031(a)(3)
and Treasury Regulation 1.1031(k)-1 as read on October 21, 2026. Your actual deadlines depend on your facts, your tax
return due date and any IRS disaster relief. Confirm every date with your qualified intermediary and your CPA or tax
attorney before relying on it. Team Utah Commercial and RE/MAX Associates do not give tax advice."

(Rule 8 still applies: if a phone number is added near this disclaimer, "RE/MAX Associates" must appear with it.)

## 6. Could not confirm (do not put these on the page)

- **The official eCFR text.** ecfr.gov blocked automated reading, so the regulation text is the Cornell LII copy. The
  Cornell copy has no "current as of" date.
- **uscode.house.gov** was unreachable (not-found page, then a maintenance page). The statute text is from Cornell LII.
- **A current IRS page that says in so many words "weekends and holidays do not extend the 45/180-day periods."** I
  did not find one. The IRS "cannot be extended" sentence is in FS-2008-18, which the IRS now marks as historical
  content. Secondary (non-IRS) search results said the preamble to the 1991 final regulations (T.D. 8346, 56 FR 19933)
  dropped a proposed statement about section 7503 (the weekend/holiday rule). I could not open the preamble: the
  govinfo Federal Register file was over 10 MB and Tax Notes refused the request (HTTP 403). So that point is
  unconfirmed and left out.
- **Whether Rev. Proc. 2018-58 has been replaced.** A search on 2026-10-21 found nothing newer, but I did not confirm
  it on an IRS list.
- **Whether a return due date that moves for a weekend or holiday also moves the 1031 limit.** Not addressed by any
  source I read, so the calculator uses April 15.
- **Due dates for business-entity returns.** Not read today, so the user has to enter them.
