# Google Sheets Structure for EV Calculator
## Step-by-Step Setup Guide

---

## Sheet 1: "Vehicle_Emissions" (Main Data)

### Columns (A-H):

| A: Vehicle_Type | B: Size | C: Fuel_Type | D: Manufacturing_CO2_kg | E: Operational_CO2_per_km | F: Maintenance_CO2_per_km | G: End_of_Life_CO2_kg | H: Notes |

### Data Rows:

```
Row 1 (Headers):
Vehicle_Type | Size | Fuel_Type | Manufacturing_CO2_kg | Operational_CO2_per_km | Maintenance_CO2_per_km | End_of_Life_CO2_kg | Notes

Row 2:
EV_Small | Small | Electric | 8500 | 0.058 | 0.005 | -500 | Nissan Leaf, VW ID.3

Row 3:
EV_Medium | Medium | Electric | 11000 | 0.066 | 0.005 | -500 | Tesla Model 3, VW ID.4

Row 4:
EV_Large | Large | Electric | 14000 | 0.078 | 0.005 | -500 | Tesla Model Y, Audi e-tron

Row 5:
EV_Small_Solar | Small | Electric_Solar | 8500 | 0.008 | 0.005 | -500 | With solar panels

Row 6:
EV_Medium_Solar | Medium | Electric_Solar | 11000 | 0.009 | 0.005 | -500 | With solar panels

Row 7:
EV_Large_Solar | Large | Electric_Solar | 14000 | 0.010 | 0.005 | -500 | With solar panels

Row 8:
Petrol_Small | Small | Petrol | 5500 | 0.155 | 0.015 | 0 | VW Polo, Toyota Yaris

Row 9:
Petrol_Medium | Medium | Petrol | 6500 | 0.183 | 0.015 | 0 | VW Golf, Toyota Corolla

Row 10:
Petrol_Large | Large | Petrol | 7500 | 0.225 | 0.015 | 0 | SUV, VW Tiguan

Row 11:
Diesel_Small | Small | Diesel | 5700 | 0.145 | 0.015 | 0 | VW Polo Diesel

Row 12:
Diesel_Medium | Medium | Diesel | 6700 | 0.178 | 0.015 | 0 | VW Golf Diesel

Row 13:
Diesel_Large | Large | Diesel | 7700 | 0.226 | 0.015 | 0 | SUV Diesel

Row 14:
Hybrid_Medium | Medium | Hybrid | 7700 | 0.110 | 0.010 | 0 | Toyota Prius PHEV
```

---

## Sheet 2: "Grid_Factors" (Electricity Emissions)

### Columns (A-C):

| A: Grid_Type | B: CO2_per_kWh | C: Description |

### Data Rows:

```
Row 1 (Headers):
Grid_Type | CO2_per_kWh | Description

Row 2:
NL_Grid_2026 | 0.388 | Netherlands average grid (28% renewable)

Row 3:
Solar_Panels | 0.050 | Household solar with grid backup

Row 4:
EU_Grid_Average | 0.295 | European average (for reference)
```

---

## Sheet 3: "Lookups" (Helper Data)

### Columns (A-E):

| A: Item | B: Value | C: Unit | D: Source | E: Notes |

### Data Rows:

```
Row 1 (Headers):
Item | Value | Unit | Source | Notes

Row 2:
Petrol_CO2_per_liter | 2.81 | kg CO2/L | Industry standard | Includes upstream emissions

Row 3:
Diesel_CO2_per_liter | 3.23 | kg CO2/L | Industry standard | Includes upstream emissions

Row 4:
Battery_CO2_per_kWh | 80 | kg CO2/kWh | IEA/CE Delft | Battery production emissions

Row 5:
Trees_CO2_per_year | 21 | kg CO2/year | EPA | Average tree absorbs 21kg CO2/year

Row 6:
Amsterdam_Paris_flight | 150 | kg CO2 | ICAO | For comparison equivalents

Row 7:
Average_NL_km_per_year | 12500 | km/year | CBS | Netherlands average
```

---

## Sheet 4: "Calculations" (Formula Examples)

This sheet shows the formulas you'll use in Make.com (for reference only, not used in automation)

### Columns (A-B):

| A: Formula_Name | B: Formula |

```
Row 1 (Headers):
Formula_Name | Formula

Row 2:
Total_Lifecycle_CO2 | Manufacturing + (Operational * km_per_year * years) + (Maintenance * km_per_year * years) + End_of_Life

Row 3:
Break_Even_km | (EV_Manufacturing - Conventional_Manufacturing) / (Conventional_Operational - EV_Operational)

Row 4:
Break_Even_Years | Break_Even_km / km_per_year

Row 5:
Trees_Equivalent | Total_CO2_Saved / 21

Row 6:
Flights_Equivalent | Total_CO2_Saved / 150

Row 7:
Annual_CO2_Year_N | Manufacturing + (Operational * km_per_year * N) + (Maintenance * km_per_year * N)
```

---

## How to Set This Up

### Step 1: Create New Google Sheet

1. Go to [sheets.google.com](https://sheets.google.com)
2. Click "Blank" to create new sheet
3. Name it: "EV Calculator Database"

### Step 2: Create Sheet 1 (Vehicle_Emissions)

1. Rename "Sheet1" to "Vehicle_Emissions"
2. Copy the headers into Row 1 (A1:H1)
3. Copy all data rows (2-14) exactly as shown above
4. Format numbers:
   - Column D (Manufacturing): Number, 0 decimals
   - Column E (Operational): Number, 3 decimals
   - Column F (Maintenance): Number, 3 decimals
   - Column G (End-of-Life): Number, 0 decimals

### Step 3: Create Sheet 2 (Grid_Factors)

1. Click "+" at bottom to add new sheet
2. Name it "Grid_Factors"
3. Copy headers and data (Rows 1-4)
4. Format Column B: Number, 3 decimals

### Step 4: Create Sheet 3 (Lookups)

1. Add another new sheet
2. Name it "Lookups"
3. Copy headers and data (Rows 1-7)
4. Format Column B: Number, appropriate decimals

### Step 5: Create Sheet 4 (Calculations)

1. Add another new sheet
2. Name it "Calculations"
3. Copy formulas (reference only)

### Step 6: Share Settings

1. Click "Share" button (top right)
2. Change to "Anyone with the link can view"
3. Copy the link - you'll need this for Make.com

---

## Visual Layout Example (Sheet 1)

Here's what your first sheet should look like:

```
   A              B       C          D          E          F          G       H
1  Vehicle_Type   Size    Fuel_Type  Manufac... Opera...   Mainte...  End...  Notes
2  EV_Small       Small   Electric   8500       0.058      0.005      -500    Nissan Leaf
3  EV_Medium      Medium  Electric   11000      0.066      0.005      -500    Tesla Model 3
4  EV_Large       Large   Electric   14000      0.078      0.005      -500    Tesla Model Y
5  EV_Small_Solar Small   Electric_S 8500       0.008      0.005      -500    With solar
...
```

---

## Make.com Will Use This Data Like This:

**Example Lookup Logic:**

User selects:
- Size: "Medium"
- Compare to: "Petrol"
- Solar panels: "No"

Make.com does:
1. Lookup "EV_Medium" in Sheet1 → Get manufacturing, operational, etc.
2. Lookup "Petrol_Medium" in Sheet1 → Get manufacturing, operational, etc.
3. User inputs: 15,000 km/year, 10 years
4. Calculate:
   - EV Total = 11000 + (0.066 × 15000 × 10) + (0.005 × 15000 × 10) - 500
   - Petrol Total = 6500 + (0.183 × 15000 × 10) + (0.015 × 15000 × 10) + 0
5. Compare and generate result

---

## Data Validation (Double-Check These)

Before using in calculator:

**Check 1: Manufacturing Emissions Make Sense**
- EV > Conventional ✓ (because of battery)
- Difference ~3,000-6,000 kg CO2 ✓

**Check 2: Operational Emissions Make Sense**
- EV < Conventional by 2-3x ✓
- EV around 60-80 g/km ✓
- Petrol around 150-225 g/km ✓

**Check 3: Math Works**
- Break-even around 30,000-50,000 km ✓
- EV cleaner over 10 years ✓

**Check 4: Sources Cited**
- CE Delft ✓
- Nowtricity ✓
- Industry standards ✓

---

## Quick Copy-Paste Format (For Easy Setup)

### Sheet 1 Data (Tab-separated, ready to paste):

```
Vehicle_Type	Size	Fuel_Type	Manufacturing_CO2_kg	Operational_CO2_per_km	Maintenance_CO2_per_km	End_of_Life_CO2_kg	Notes
EV_Small	Small	Electric	8500	0.058	0.005	-500	Nissan Leaf, VW ID.3
EV_Medium	Medium	Electric	11000	0.066	0.005	-500	Tesla Model 3, VW ID.4
EV_Large	Large	Electric	14000	0.078	0.005	-500	Tesla Model Y, Audi e-tron
EV_Small_Solar	Small	Electric_Solar	8500	0.008	0.005	-500	With solar panels
EV_Medium_Solar	Medium	Electric_Solar	11000	0.009	0.005	-500	With solar panels
EV_Large_Solar	Large	Electric_Solar	14000	0.010	0.005	-500	With solar panels
Petrol_Small	Small	Petrol	5500	0.155	0.015	0	VW Polo, Toyota Yaris
Petrol_Medium	Medium	Petrol	6500	0.183	0.015	0	VW Golf, Toyota Corolla
Petrol_Large	Large	Petrol	7500	0.225	0.015	0	SUV, VW Tiguan
Diesel_Small	Small	Diesel	5700	0.145	0.015	0	VW Polo Diesel
Diesel_Medium	Medium	Diesel	6700	0.178	0.015	0	VW Golf Diesel
Diesel_Large	Large	Diesel	7700	0.226	0.015	0	SUV Diesel
Hybrid_Medium	Medium	Hybrid	7700	0.110	0.010	0	Toyota Prius PHEV
```

**To use:** Select all text above → Copy → Paste into A1 of your Google Sheet (it will auto-split into columns)

---

## Next Steps After Sheet is Built

Once you have this Google Sheet set up:

1. ✅ Copy the share link
2. ✅ Test a few manual calculations to verify data is correct
3. ✅ Ready to connect to Make.com

Then we'll build:
- Typeform (user questions)
- Make.com automation (connects everything)
- Result email template

---

## Need Help?

If you get stuck setting up the sheet, you can:
1. Share your Google Sheet link with me (I can check if it's correct)
2. Screenshot what you have so far
3. Or tell me where you're stuck

Ready to set this up? Let me know when you've created the sheet and I'll walk you through Typeform next!
