# EV vs Conventional Car Calculator
## Emission Factors Database (Netherlands)
### Last Updated: January 15, 2026

---

## Netherlands Electricity Grid

### Current Grid Emissions (2025/2026 Data)
- **Average: 388 g CO2eq/kWh** (0.388 kg CO2eq/kWh)
- Source: [Nowtricity Netherlands](https://www.nowtricity.com/country/netherlands/)
- Energy mix: 28% renewable, 47.4% gas, rest coal/other

### Historical Context
- 2023: 268.5 g CO2/kWh (lowest this century)
- 2025: 388 g CO2eq/kWh (slight increase)
- Note: Grid is getting cleaner over time as renewables increase

### With Solar Panels (Household)
- **If user has solar: 0 g CO2/kWh** (assume self-generated clean electricity)
- Conservative estimate: 50 g CO2/kWh (accounting for grid backup)

---

## Electric Vehicles (BEV - Battery Electric Vehicle)

### Manufacturing Emissions

**Small EV** (e.g., Nissan Leaf, VW ID.3 base)
- Vehicle production: 5,000 kg CO2
- Battery production (40-50 kWh): 3,200-4,000 kg CO2 (80 kg CO2/kWh battery)
- **Total manufacturing: 8,000-9,000 kg CO2**

**Medium EV** (e.g., Tesla Model 3, VW ID.4)
- Vehicle production: 6,000 kg CO2
- Battery production (60-75 kWh): 4,800-6,000 kg CO2
- **Total manufacturing: 10,800-12,000 kg CO2**

**Large EV** (e.g., Tesla Model Y, Audi e-tron)
- Vehicle production: 7,000 kg CO2
- Battery production (80-100 kWh): 6,400-8,000 kg CO2
- **Total manufacturing: 13,400-15,000 kg CO2**

**Source:** [CE Delft - Indirect and Direct CO2 Emissions of Electric Cars](https://cedelft.eu/publications/indirect-and-direct-co2-emissions-of-electric-cars/)
**Battery factor:** 80 kg CO2 per kWh battery capacity (industry standard, includes mining, production, transport)

### Operational Emissions (Driving)

**Energy Consumption per km:**
- Small EV: 0.15 kWh/km (15 kWh/100km)
- Medium EV: 0.17 kWh/km (17 kWh/100km)
- Large EV: 0.20 kWh/km (20 kWh/100km)

**CO2 per km (Netherlands grid at 388 g/kWh):**
- Small EV: 0.15 × 0.388 = **0.058 kg CO2/km** (58 g/km)
- Medium EV: 0.17 × 0.388 = **0.066 kg CO2/km** (66 g/km)
- Large EV: 0.20 × 0.388 = **0.078 kg CO2/km** (78 g/km)

**With solar panels (50 g/kWh):**
- Small EV: 0.15 × 0.05 = **0.0075 kg CO2/km** (7.5 g/km)
- Medium EV: 0.17 × 0.05 = **0.0085 kg CO2/km** (8.5 g/km)
- Large EV: 0.20 × 0.05 = **0.010 kg CO2/km** (10 g/km)

### Maintenance Emissions
- **Lower than conventional:** Fewer moving parts, no oil changes
- Estimate: **0.005 kg CO2/km** (5 g/km)

### End-of-Life
- Battery recycling: -500 to -1,000 kg CO2 (credit for recovered materials)
- Vehicle recycling: Similar to conventional cars
- **Net end-of-life: -500 kg CO2** (conservative)

---

## Petrol Cars (ICE - Internal Combustion Engine)

### Manufacturing Emissions

**Small Petrol Car** (e.g., VW Polo, Toyota Yaris)
- Vehicle production: **5,500 kg CO2**

**Medium Petrol Car** (e.g., VW Golf, Toyota Corolla)
- Vehicle production: **6,500 kg CO2**

**Large Petrol Car** (e.g., SUV, VW Tiguan)
- Vehicle production: **7,500 kg CO2**

**Source:** CE Delft reports (petrol car manufacturing is ~30-40% less than equivalent EV due to no battery)

### Operational Emissions (Driving)

**Fuel Consumption:**
- Small petrol: 5.5 L/100km → 0.055 L/km
- Medium petrol: 6.5 L/100km → 0.065 L/km
- Large petrol: 8.0 L/100km → 0.080 L/km

**CO2 per liter of petrol:** 2.31 kg CO2/L
- Includes: Combustion (2.31 kg) + extraction/refining (0.50 kg) = **2.81 kg CO2/L total**

**CO2 per km:**
- Small petrol: 0.055 × 2.81 = **0.155 kg CO2/km** (155 g/km)
- Medium petrol: 0.065 × 2.81 = **0.183 kg CO2/km** (183 g/km)
- Large petrol: 0.080 × 2.81 = **0.225 kg CO2/km** (225 g/km)

### Maintenance Emissions
- **Higher than EV:** Oil changes, more wear parts
- Estimate: **0.015 kg CO2/km** (15 g/km)

### End-of-Life
- Vehicle recycling: Similar to EV
- **Net end-of-life: 0 kg CO2** (neutral)

---

## Diesel Cars

### Manufacturing Emissions

**Small Diesel Car**
- Vehicle production: **5,700 kg CO2**

**Medium Diesel Car**
- Vehicle production: **6,700 kg CO2**

**Large Diesel Car**
- Vehicle production: **7,700 kg CO2**

### Operational Emissions (Driving)

**Fuel Consumption:**
- Small diesel: 4.5 L/100km → 0.045 L/km
- Medium diesel: 5.5 L/100km → 0.055 L/km
- Large diesel: 7.0 L/100km → 0.070 L/km

**CO2 per liter of diesel:** 2.68 kg CO2/L
- Includes: Combustion (2.68 kg) + extraction/refining (0.55 kg) = **3.23 kg CO2/L total**

**CO2 per km:**
- Small diesel: 0.045 × 3.23 = **0.145 kg CO2/km** (145 g/km)
- Medium diesel: 0.055 × 3.23 = **0.178 kg CO2/km** (178 g/km)
- Large diesel: 0.070 × 3.23 = **0.226 kg CO2/km** (226 g/km)

### Maintenance Emissions
- **Similar to petrol**
- Estimate: **0.015 kg CO2/km** (15 g/km)

### End-of-Life
- **Net end-of-life: 0 kg CO2** (neutral)

---

## Hybrid Cars (Plug-in Hybrid - PHEV)

### Manufacturing Emissions

**Medium Hybrid** (e.g., Toyota Prius PHEV)
- Vehicle production: 6,500 kg CO2
- Battery production (15 kWh): 1,200 kg CO2
- **Total manufacturing: 7,700 kg CO2**

### Operational Emissions (Mixed)

**Assumptions:**
- 50% electric driving (short trips, charged daily)
- 50% petrol driving (long trips)

**Electric mode:** 0.17 kWh/km × 0.388 kg/kWh = 0.066 kg CO2/km
**Petrol mode:** 0.055 L/km × 2.81 kg/L = 0.155 kg CO2/km

**Average: (0.066 + 0.155) / 2 = 0.110 kg CO2/km** (110 g/km)

**Note:** Highly dependent on driving patterns and charging behavior

---

## Summary Table: CO2 per km (Operational Only)

| Vehicle Type | Small | Medium | Large |
|--------------|-------|--------|-------|
| **EV (NL grid)** | 58 g/km | 66 g/km | 78 g/km |
| **EV (with solar)** | 8 g/km | 9 g/km | 10 g/km |
| **Petrol** | 155 g/km | 183 g/km | 225 g/km |
| **Diesel** | 145 g/km | 178 g/km | 226 g/km |
| **Hybrid** | - | 110 g/km | - |

**Key Finding:** EVs emit 62-70% less CO2 per km than petrol/diesel (even with current NL grid)

---

## Total Lifecycle Emissions Calculator

### Formula:

**Total Lifecycle CO2 = Manufacturing + (Operational × Distance × Years) + Maintenance + End-of-Life**

### Example: Medium EV vs Medium Petrol (10 years, 15,000 km/year)

**Medium EV:**
- Manufacturing: 11,000 kg CO2
- Operational: 0.066 kg/km × 15,000 km/yr × 10 yr = 9,900 kg CO2
- Maintenance: 0.005 kg/km × 150,000 km = 750 kg CO2
- End-of-life: -500 kg CO2
- **Total: 21,150 kg CO2**

**Medium Petrol:**
- Manufacturing: 6,500 kg CO2
- Operational: 0.183 kg/km × 15,000 km/yr × 10 yr = 27,450 kg CO2
- Maintenance: 0.015 kg/km × 150,000 km = 2,250 kg CO2
- End-of-life: 0 kg CO2
- **Total: 36,200 kg CO2**

**Result: EV is 42% cleaner over 10 years (15,050 kg CO2 saved)**

---

## Break-Even Point Calculator

**When does EV become cleaner than petrol?**

Formula:
```
Manufacturing difference = EV manufacturing - Petrol manufacturing
Operational advantage per km = Petrol per km - EV per km
Break-even km = Manufacturing difference / Operational advantage
```

### Example: Medium EV vs Medium Petrol

- Manufacturing difference: 11,000 - 6,500 = 4,500 kg CO2 (EV "behind")
- Operational advantage: 0.183 - 0.066 = 0.117 kg CO2/km (EV "gains")
- **Break-even: 4,500 / 0.117 = 38,462 km**

At 15,000 km/year: **Break-even after 2.6 years**

---

## Variables to Include in Calculator

### User Inputs:
1. Car size (small/medium/large)
2. Car type to compare (petrol/diesel/hybrid)
3. Annual km driven (5,000 - 40,000)
4. Ownership period (5/10/15 years)
5. Solar panels? (yes/no)
6. Driving type (city/mixed/highway) - optional

### Outputs:
1. Total lifecycle CO2 for each car type
2. Break-even point (km and years)
3. Annual CO2 comparison
4. Visual timeline chart
5. Cost comparison (optional)
6. Equivalents ("Saved CO2 = X trees planted")

---

## Data Sources

1. **Netherlands Grid Emissions:** [Nowtricity Netherlands](https://www.nowtricity.com/country/netherlands/) & [ElectricityMaps](https://app.electricitymaps.com/zone/NL)

2. **CE Delft Research:** [Indirect and Direct CO2 Emissions of Electric Cars](https://cedelft.eu/publications/indirect-and-direct-co2-emissions-of-electric-cars/)

3. **CE Delft STREAM:** [STREAM Passenger Transport 2022](https://cedelft.eu/publications/stream-passenger-transport-2022/)

4. **Battery Production:** Industry standard 80 kg CO2/kWh (IEA, European studies)

5. **Fuel Emissions:** Standard factors: Petrol 2.31 kg CO2/L combustion + 0.50 kg upstream = 2.81 kg CO2/L total

6. **Vehicle Efficiency:** Real-world data from TNO and manufacturer specs

---

## Notes for Calculator Build

### Assumptions Made:
- Netherlands grid mix remains constant (conservative - it's actually getting cleaner)
- Average driving patterns
- Standard maintenance schedules
- Battery recycling credit included
- Grid emissions include upstream (well-to-wheel equivalent)

### Conservative Estimates Used:
- Higher manufacturing emissions for EVs
- Current grid mix (not future cleaner grid)
- No accounting for grid improvements over vehicle lifetime
- Standard efficiency (not optimized driving)

**This makes the calculator credible - we're not cherry-picking best-case scenarios.**

---

## Next Step: Build the Google Sheet

This data should be structured in a Google Sheet with columns:
- Vehicle_Type (EV_Small, EV_Medium, EV_Large, Petrol_Small, etc.)
- Manufacturing_CO2_kg
- Operational_CO2_per_km
- Maintenance_CO2_per_km
- End_of_life_CO2_kg

Then Make.com can lookup values based on user selections.

Want me to create the exact Google Sheets structure next?
