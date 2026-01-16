# EV Calculator Project - Current Progress
**Last Updated:** January 16, 2026

---

## Project Overview

Building a no-code EV vs Conventional Car carbon footprint calculator specifically for Netherlands market.

**Tech Stack:**
- **Typeform:** User questionnaire
- **Google Sheets:** Emissions database
- **Make.com:** Automation & calculations
- **Gmail:** Deliver results

**Target Users:** Dutch EV skeptics who wonder "When does an EV become cleaner than petrol?"

---

## ✅ Completed

### 1. Research & Data Collection
- [x] Researched Netherlands grid emissions: 388g CO2/kWh (Nowtricity)
- [x] Compiled CE Delft lifecycle emissions data
- [x] Calculated break-even points for different vehicle types
- [x] Created `ev-calculator-emission-factors.md` with all data sources

### 2. Google Sheets Database
- [x] Created 4-sheet database structure
- [x] Sheet 1: Vehicle_Emissions (14 vehicle types)
- [x] Sheet 2: Grid_Factors (NL grid + solar)
- [x] Sheet 3: Lookups (helper data)
- [x] Sheet 4: Calculations (formula reference)
- [x] Shared with proper permissions
- [x] **Live spreadsheet:** https://docs.google.com/spreadsheets/d/1p3-_wP-xLeKzMiplyMC3Ohg56rWKSFscGPvv_Sv_VJ8/edit

### 3. Typeform Questionnaire
- [x] Created 8-question flow
- [x] Q1: Welcome screen
- [x] Q2: Current car size (Small/Medium/Large)
- [x] Q3: Current car type (Petrol/Diesel/Hybrid)
- [x] Q4: EV size considering (Small/Medium/Large)
- [x] Q5: Annual kilometers (5,000-40,000 slider)
- [x] Q6: Ownership period (5/10/15 years)
- [x] Q7: Solar panels (Yes/No/Planning)
- [x] Q8: Email (optional)
- [x] Set up notifications
- [x] **Live form:** https://form.typeform.com/to/Eeq0JZRO

### 4. Make.com Automation (In Progress)

#### Module 1: Typeform Trigger ✅
- [x] Connected Typeform account
- [x] Selected "EV vs Petrol Calculator" form
- [x] Set to "From now on"
- [x] Tested successfully (captured 8 questions of data)

#### Module 2: Google Sheets Lookup (EV Data) ✅
- [x] Connected Google Sheets
- [x] Selected "EV Calculator Database" spreadsheet
- [x] Sheet: Vehicle_Emissions
- [x] Filter on Column A (Vehicle_Type)
- [x] Formula created:
```
{{if(3.has_solar = "Yes" or 3.has_solar = "Planning"; "EV_" + 3.ev_size + "_Solar"; "EV_" + 3.ev_size)}}
```
- [x] Limit: 1
- [x] Saved successfully

#### Module 3: Google Sheets Lookup (Conventional Car Data) ✅
- [x] Connected Google Sheets (same connection)
- [x] Selected "EV Calculator Database" spreadsheet
- [x] Sheet: Vehicle_Emissions
- [x] Filter on Column A (Vehicle_Type)
- [x] Formula created:
```
{{3.compare_to + "_" + 3.car_size}}
```
- [x] Limit: 1
- [x] Saved successfully

#### Module 4: Set Multiple Variables (Calculations) 🔄
**Variables 1-8: Google Sheets Data Extraction ✅**
- [x] `ev_manufacturing` = `{{2.D}}`
- [x] `ev_operational_per_km` = `{{2.E}}`
- [x] `ev_maintenance_per_km` = `{{2.F}}`
- [x] `ev_end_of_life` = `{{2.G}}`
- [x] `conventional_manufacturing` = `{{3.D}}`
- [x] `conventional_operational_per_km` = `{{3.E}}`
- [x] `conventional_maintenance_per_km` = `{{3.F}}`
- [x] `conventional_end_of_life` = `{{3.G}}`

**Variables 9-15: Calculate Totals (Next Step)**
- [ ] `total_km` = `{{1.km_per_year * 1.years_owned}}`
- [ ] `ev_operational_total` = `{{ev_operational_per_km * total_km}}`
- [ ] `ev_maintenance_total` = `{{ev_maintenance_per_km * total_km}}`
- [ ] `ev_total_co2` = `{{ev_manufacturing + ev_operational_total + ev_maintenance_total + ev_end_of_life}}`
- [ ] `conventional_operational_total` = `{{conventional_operational_per_km * total_km}}`
- [ ] `conventional_maintenance_total` = `{{conventional_maintenance_per_km * total_km}}`
- [ ] `conventional_total_co2` = `{{conventional_manufacturing + conventional_operational_total + conventional_maintenance_total + conventional_end_of_life}}`

---

## 🔄 In Progress

### Module 4 Continuation (Variables 9-15)
Currently adding calculation variables for totals (operational, maintenance, lifecycle CO2).

**Next immediate step:** Add variables 9-15 as listed above.

---

## ⏳ Remaining Tasks

### Module 4 Completion (Variables 16-21)
- [ ] `co2_saved` = Total savings calculation
- [ ] `breakeven_km` = Break-even point calculation
- [ ] `breakeven_years` = Break-even in years
- [ ] `percentage_cleaner` = EV advantage percentage
- [ ] `trees_equivalent` = CO2 saved in trees planted
- [ ] `flights_equivalent` = CO2 saved in flights avoided

### Module 5: Format Numbers for Email
- [ ] Add "Set variables" module
- [ ] Format all numbers with thousands separators
- [ ] Round appropriately (0-2 decimals)
- [ ] Create user-friendly display variables

### Module 6: Send Email via Gmail
- [ ] Connect Gmail account
- [ ] Set recipient to `{{1.user_email}}`
- [ ] Create subject line
- [ ] Build HTML email template with results
- [ ] Include visual formatting (colors, tables)
- [ ] Add social share buttons
- [ ] Include methodology link

### Testing & Launch
- [ ] Test complete automation end-to-end
- [ ] Fill form with test data
- [ ] Verify email received with correct calculations
- [ ] Check break-even point accuracy
- [ ] Activate scenario (turn on scheduling)
- [ ] Monitor first real submissions

### Landing Page (Future)
- [ ] Create simple Carrd landing page
- [ ] Add "Start Calculator" button linking to Typeform
- [ ] Write compelling copy addressing EV skepticism
- [ ] Launch and promote on LinkedIn

---

## Key Decisions Made

1. **Netherlands-specific data:** Using 388g CO2/kWh grid emissions (2025 Nowtricity data)
2. **Separate questions for current vs future car:** Based on user feedback that combined question didn't make sense
3. **Solar panel bonus:** Separate lookup for EV_Solar variants (cleaner charging)
4. **Optional email:** Users can see basic results without giving email
5. **Conservative estimates:** Not cherry-picking best-case scenarios for credibility
6. **Make.com "From now on":** Only process new submissions after activation

---

## Resources & Links

**Documentation Files:**
- `ev-calculator-emission-factors.md` - Research data and sources
- `google-sheets-structure.md` - Database setup guide
- `typeform-questions.md` - Complete question flow
- `makecom-automation-guide.md` - Step-by-step automation setup

**Live Components:**
- Typeform: https://form.typeform.com/to/Eeq0JZRO
- Google Sheets: https://docs.google.com/spreadsheets/d/1p3-_wP-xLeKzMiplyMC3Ohg56rWKSFscGPvv_Sv_VJ8/edit

**Data Sources:**
- Nowtricity Netherlands: https://www.nowtricity.com/country/netherlands/
- CE Delft: https://cedelft.eu/publications/indirect-and-direct-co2-emissions-of-electric-cars/

---

## Timeline

- **January 14:** Project pivot from CSRD to EV calculator
- **January 15:** Research, data compilation, Google Sheets setup, Typeform creation
- **January 16:** Make.com automation in progress (Modules 1-3 complete, Module 4 halfway)
- **Estimated completion:** January 17-18 (full automation working)
- **Launch target:** January 20 (with landing page)

---

## Notes

- User background: Sustainable development, water board consulting
- Located in Netherlands
- Goal: Generate revenue quickly with simple no-code project
- Addresses real Dutch market skepticism about EV environmental benefits
- Conservative data approach ensures credibility

---

**Current blocker:** None - making steady progress on Make.com setup

**Next session:** Continue with Variables 9-15, then 16-21, then Module 5 & 6
