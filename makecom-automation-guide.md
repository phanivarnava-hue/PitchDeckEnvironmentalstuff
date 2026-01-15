# Make.com Automation Guide
## EV Calculator: Typeform → Google Sheets → Email

---

## Overview: What We're Building

**The Flow:**
```
User fills Typeform
    ↓
Make.com receives data
    ↓
Make.com looks up emission factors from Google Sheets
    ↓
Make.com calculates total CO2 for EV and conventional car
    ↓
Make.com calculates break-even point
    ↓
Make.com formats email with results
    ↓
Make.com sends email to user
```

**Time to build:** 45-60 minutes
**Cost:** €9/month (Make.com starter plan)
**Difficulty:** Medium (lots of steps, but I'll guide you)

---

## Prerequisites

Before starting, you need:
- ✅ Typeform link: https://form.typeform.com/to/Eeq0JZRO
- ✅ Google Sheet: https://docs.google.com/spreadsheets/d/1p3-_wP-xLeKzMiplyMC3Ohg56rWKSFscGPvv_Sv_VJ8/edit
- ✅ Email account (Gmail recommended for Make.com)

---

## Step 1: Create Make.com Account

1. Go to [make.com](https://www.make.com)
2. Click "Get Started Free"
3. Sign up with Google (easiest)
4. Choose "Personal" plan (free for testing, then €9/month)

---

## Step 2: Create New Scenario

1. After logging in, click **"Create a new scenario"**
2. You'll see a blank canvas with a **"+"** button
3. This is where we'll build the automation

---

## Step 3: Add Typeform Trigger

**Module 1: Typeform - Watch Responses**

1. Click the **"+"** button on canvas
2. Search for **"Typeform"**
3. Select **"Typeform"** app
4. Choose trigger: **"Watch Responses"** (this monitors for new submissions)
5. Click **"Create a connection"**
   - Name: "Typeform Connection"
   - Click the link to authorize Typeform
   - Sign in to Typeform, allow access
6. Once connected:
   - **Form:** Select your form "EV vs Petrol Calculator"
   - **Limit:** Leave at 1 (processes one response at a time)
7. Click **"OK"**

**Test it:**
- Click **"Run Once"** at bottom
- Go fill out your Typeform with test data
- Come back to Make.com
- You should see the test response appear
- Click "OK" to continue

---

## Step 4: Add Google Sheets Lookups

We need to look up emission data based on user selections.

**Module 2: Google Sheets - Search Rows**

1. Click **"+"** after Typeform module
2. Search for **"Google Sheets"**
3. Select **"Google Sheets"** app
4. Choose action: **"Search Rows"**
5. Click **"Create a connection"**
   - Sign in to Google
   - Allow access to Google Sheets
6. Configure search:
   - **Spreadsheet:** Select "EV Calculator Database"
   - **Sheet:** Select "Vehicle_Emissions"
   - **Filter:**
     - Column: `A` (Vehicle_Type)
     - Operator: `Text: Equal to`
     - Value: **(This is complex, see below)**

**Building the Vehicle_Type lookup value:**

We need to construct the correct Vehicle_Type based on user's answers.

**Logic:**
- If comparing EV: `EV_{{size}}_{{solar}}`
- Examples:
  - User selects "Medium EV" + "No solar" → `EV_Medium`
  - User selects "Small EV" + "Has solar" → `EV_Small_Solar`

**In Make.com Value field, use this formula:**

```
{{if(3.has_solar = "Yes" or 3.has_solar = "Planning"; "EV_" + 3.ev_size + "_Solar"; "EV_" + 3.ev_size)}}
```

**Explanation:**
- `3.has_solar` = solar panels answer (adjust number if different module)
- `3.ev_size` = EV size answer
- If solar = Yes or Planning → add "_Solar"
- Otherwise → just standard EV

7. **Output:** Set to "All"
8. Click **"OK"**

**Module 3: Google Sheets - Search Rows (Conventional Car)**

1. Click **"+"** after previous module
2. Add another **"Google Sheets - Search Rows"**
3. Use same connection
4. Configure:
   - **Spreadsheet:** EV Calculator Database
   - **Sheet:** Vehicle_Emissions
   - **Filter:**
     - Column: `A` (Vehicle_Type)
     - Operator: `Text: Equal to`
     - Value: `{{3.compare_to}}_{{3.current_size}}`
       - Example: If user selected "Petrol" and "Medium" → `Petrol_Medium`

5. Click **"OK"**

---

## Step 5: Calculations (Tools - Set Variables)

Now we calculate total lifecycle CO2.

**Module 4: Tools - Set Multiple Variables**

1. Click **"+"**
2. Search for **"Tools"**
3. Select **"Set Multiple Variables"**
4. We'll create ~15 variables for all our calculations

**Variables to create:**

### Variable 1: total_km
**Name:** `total_km`
**Value:** `{{3.km_per_year * 3.years_owned}}`
**Description:** Total kilometers over ownership period

### Variable 2: ev_manufacturing
**Name:** `ev_manufacturing`
**Value:** `{{2.D}}`
**Description:** EV manufacturing CO2 (from Module 2, column D)

### Variable 3: ev_operational_per_km
**Name:** `ev_operational_per_km`
**Value:** `{{2.E}}`
**Description:** EV operational CO2 per km

### Variable 4: ev_operational_total
**Name:** `ev_operational_total`
**Value:** `{{ev_operational_per_km * total_km}}`
**Description:** EV driving emissions total

### Variable 5: ev_maintenance_per_km
**Name:** `ev_maintenance_per_km`
**Value:** `{{2.F}}`
**Description:** EV maintenance per km

### Variable 6: ev_maintenance_total
**Name:** `ev_maintenance_total`
**Value:** `{{ev_maintenance_per_km * total_km}}`
**Description:** EV maintenance total

### Variable 7: ev_end_of_life
**Name:** `ev_end_of_life`
**Value:** `{{2.G}}`
**Description:** EV end of life emissions

### Variable 8: ev_total_co2
**Name:** `ev_total_co2`
**Value:** `{{ev_manufacturing + ev_operational_total + ev_maintenance_total + ev_end_of_life}}`
**Description:** EV total lifecycle CO2

### Variable 9-15: Same for Conventional Car

Repeat Variables 2-8 but for conventional car:

**Variable 9:** `conventional_manufacturing` = `{{3.D}}`
**Variable 10:** `conventional_operational_per_km` = `{{3.E}}`
**Variable 11:** `conventional_operational_total` = `{{conventional_operational_per_km * total_km}}`
**Variable 12:** `conventional_maintenance_per_km` = `{{3.F}}`
**Variable 13:** `conventional_maintenance_total` = `{{conventional_maintenance_per_km * total_km}}`
**Variable 14:** `conventional_end_of_life` = `{{3.G}}`
**Variable 15:** `conventional_total_co2` = `{{conventional_manufacturing + conventional_operational_total + conventional_maintenance_total + conventional_end_of_life}}`

### Variable 16-20: Comparisons

**Variable 16:** `co2_saved`
**Value:** `{{conventional_total_co2 - ev_total_co2}}`
**Description:** Total CO2 saved by EV

**Variable 17:** `percentage_cleaner`
**Value:** `{{round((co2_saved / conventional_total_co2) * 100; 0)}}`
**Description:** Percentage EV is cleaner

**Variable 18:** `breakeven_km`
**Value:** `{{round((ev_manufacturing - conventional_manufacturing) / (conventional_operational_per_km - ev_operational_per_km); 0)}}`
**Description:** Break-even point in km

**Variable 19:** `breakeven_years`
**Value:** `{{round(breakeven_km / 3.km_per_year; 1)}}`
**Description:** Break-even in years

**Variable 20:** `trees_equivalent`
**Value:** `{{round(co2_saved / 21; 0)}}`
**Description:** Trees equivalent (21 kg CO2/tree/year)

**Variable 21:** `flights_equivalent`
**Value:** `{{round(co2_saved / 150; 1)}}`
**Description:** Amsterdam-Paris flights avoided

---

## Step 6: Format Numbers (Optional but Recommended)

**Module 5: Tools - Set Multiple Variables (Formatting)**

Add one more "Set Variables" module to format numbers nicely:

**Variable 1:** `ev_total_formatted`
**Value:** `{{formatNumber(ev_total_co2; 0; ","; ".")}}`
**Description:** EV total with thousand separators

**Variable 2:** `conventional_total_formatted`
**Value:** `{{formatNumber(conventional_total_co2; 0; ","; ".")}}`

**Variable 3:** `co2_saved_formatted`
**Value:** `{{formatNumber(co2_saved; 0; ","; ".")}}`

*(Continue for all numbers you want to display)*

---

## Step 7: Send Email

**Module 6: Gmail - Send an Email**

1. Click **"+"**
2. Search for **"Gmail"**
3. Select **"Send an Email"**
4. Create connection (sign in to Gmail)
5. Configure email:

**To:** `{{3.user_email}}`

**Subject:** `Your EV vs {{3.compare_to}} Comparison Results`

**Content Type:** HTML

**Content:** (See email template below)

---

## Email Template (HTML)

```html
<html>
<body style="font-family: Arial, sans-serif; max-width: 600px; margin: 0 auto; padding: 20px;">

<h1 style="color: #01689B;">Your EV Carbon Footprint Results</h1>

<p>Hi there! Here's your personalized comparison:</p>

<hr style="border: 2px solid #F39200;">

<h2 style="color: #01689B;">Your Inputs</h2>
<ul>
  <li><strong>Current car:</strong> {{3.current_size}} {{3.compare_to}}</li>
  <li><strong>Considering:</strong> {{3.ev_size}} Electric</li>
  <li><strong>Annual driving:</strong> {{3.km_per_year}} km</li>
  <li><strong>Ownership:</strong> {{3.years_owned}} years</li>
  <li><strong>Total distance:</strong> {{total_km}} km</li>
  {{#if(3.has_solar = "Yes" or 3.has_solar = "Planning")}}<li>☀️ <strong>With solar panels</strong></li>{{/if}}
</ul>

<hr style="border: 2px solid #F39200;">

<h2 style="color: #01689B;">🔋 Electric Car</h2>
<table style="width: 100%; border-collapse: collapse;">
  <tr style="background-color: #f0f0f0;">
    <td style="padding: 10px;"><strong>Total Lifetime CO2:</strong></td>
    <td style="padding: 10px; text-align: right;"><strong>{{ev_total_formatted}} kg</strong></td>
  </tr>
  <tr>
    <td style="padding: 10px;">Manufacturing:</td>
    <td style="padding: 10px; text-align: right;">{{formatNumber(ev_manufacturing; 0; ","; ".")}} kg</td>
  </tr>
  <tr>
    <td style="padding: 10px;">Driving ({{total_km}} km):</td>
    <td style="padding: 10px; text-align: right;">{{formatNumber(ev_operational_total; 0; ","; ".")}} kg</td>
  </tr>
  <tr>
    <td style="padding: 10px;">Maintenance:</td>
    <td style="padding: 10px; text-align: right;">{{formatNumber(ev_maintenance_total; 0; ","; ".")}} kg</td>
  </tr>
  <tr>
    <td style="padding: 10px;">End-of-life credit:</td>
    <td style="padding: 10px; text-align: right;">{{ev_end_of_life}} kg</td>
  </tr>
</table>

<h2 style="color: #01689B; margin-top: 30px;">⛽ {{3.compare_to}} Car</h2>
<table style="width: 100%; border-collapse: collapse;">
  <tr style="background-color: #f0f0f0;">
    <td style="padding: 10px;"><strong>Total Lifetime CO2:</strong></td>
    <td style="padding: 10px; text-align: right;"><strong>{{conventional_total_formatted}} kg</strong></td>
  </tr>
  <tr>
    <td style="padding: 10px;">Manufacturing:</td>
    <td style="padding: 10px; text-align: right;">{{formatNumber(conventional_manufacturing; 0; ","; ".")}} kg</td>
  </tr>
  <tr>
    <td style="padding: 10px;">Driving ({{total_km}} km):</td>
    <td style="padding: 10px; text-align: right;">{{formatNumber(conventional_operational_total; 0; ","; ".")}} kg</td>
  </tr>
  <tr>
    <td style="padding: 10px;">Maintenance:</td>
    <td style="padding: 10px; text-align: right;">{{formatNumber(conventional_maintenance_total; 0; ","; ".")}} kg</td>
  </tr>
</table>

<hr style="border: 2px solid #F39200; margin-top: 30px;">

<h2 style="color: #39870C;">✅ The Verdict</h2>

<div style="background-color: #F1F8E9; padding: 20px; border-left: 4px solid #39870C; margin: 20px 0;">
  <h3 style="margin-top: 0;">Electric is {{percentage_cleaner}}% cleaner over {{3.years_owned}} years.</h3>
  <p style="font-size: 18px; margin: 10px 0;">You'll save <strong>{{co2_saved_formatted}} kg CO2</strong> total.</p>
  <p style="margin-bottom: 0;">💡 <strong>Break-even point:</strong> {{formatNumber(breakeven_km; 0; ","; ".")}} km (that's {{breakeven_years}} years at your driving rate)</p>
</div>

<hr style="border: 2px solid #F39200;">

<h2 style="color: #01689B;">🌳 What Does That Mean?</h2>

<p>Your CO2 savings equals:</p>
<ul>
  <li>🌳 <strong>{{trees_equivalent}} trees</strong> planted and grown for 1 year</li>
  <li>✈️ <strong>{{flights_equivalent}} Amsterdam-Paris flights</strong> avoided</li>
</ul>

<hr style="border: 2px solid #F39200;">

<h2 style="color: #01689B;">⚠️ Important Context</h2>

<ul>
  <li>Yes, EV battery production is emissions-intensive</li>
  <li>But lower operational emissions quickly make up for it</li>
  <li>Netherlands grid is getting cleaner each year (more renewables)</li>
  <li>These calculations use current NL grid mix (28% renewable, 388g CO2/kWh)</li>
  {{#if(3.has_solar = "Yes" or 3.has_solar = "Planning")}}<li>☀️ With your solar panels, the EV is even cleaner!</li>{{/if}}
</ul>

<hr style="border: 2px solid #F39200;">

<h3 style="color: #01689B;">📚 Data Sources</h3>

<p style="font-size: 12px;">
All data from peer-reviewed sources:<br>
• CE Delft - Lifecycle emissions research<br>
• Nowtricity - Netherlands grid emissions (2026)<br>
• Industry standards for manufacturing & maintenance<br>
</p>

<p style="font-size: 12px; color: #666;">
Questions? Reply to this email.<br>
Share this calculator: <a href="https://form.typeform.com/to/Eeq0JZRO">https://form.typeform.com/to/Eeq0JZRO</a>
</p>

<p style="font-size: 11px; color: #999; margin-top: 40px;">
Built with data, not hype. Last updated: January 2026.
</p>

</body>
</html>
```

---

## Step 8: Test the Entire Flow

1. Click **"Run Once"** at bottom of Make.com
2. Go to your Typeform: https://form.typeform.com/to/Eeq0JZRO
3. Fill it out with test data
4. Submit
5. Watch Make.com process (you'll see each module light up)
6. Check your email for results

**If it works:** 🎉 You're done!

**If errors:** Check which module failed, fix the formula, try again

---

## Step 9: Activate Scenario

Once testing works:

1. Click **"Scheduling"** toggle (top right)
2. Set to **"Immediately"** (processes every new response instantly)
3. Click **"ON"** to activate
4. Your calculator is now LIVE! 🚀

---

## Troubleshooting Common Issues

### Issue 1: "Variable not found"
**Fix:** Check module numbers (they might be different, like 2.D vs 3.D)

### Issue 2: "Calculation result is NaN"
**Fix:** Make sure Google Sheets columns have numbers, not text

### Issue 3: Email not sending
**Fix:** Check user provided email in Typeform

### Issue 4: Break-even is negative
**Fix:** Check if conventional car operational is actually higher than EV

---

## Make.com Costs

**Free Tier:**
- 1,000 operations/month
- Limited to 15-minute intervals

**Starter Plan (€9/month):**
- 10,000 operations/month
- Instant processing
- **Recommended for this project**

**Operation count:**
- Each form submission = ~6 operations (Typeform + 2 Sheets + calculations + email)
- 10,000 operations = ~1,600 form submissions/month
- More than enough for starting out!

---

## Next Steps After Make.com Works

1. ✅ Build landing page (Carrd - simple one-pager with "Start Calculator" button)
2. ✅ Share on LinkedIn/social media
3. ✅ Get feedback from first 10-20 users
4. ✅ Iterate and improve

---

## Need Help?

Make.com can be complex! If you get stuck:
1. Screenshot the error
2. Tell me which module is failing
3. I'll help debug

Good luck! This is the most technical part, but once it works, it's magical ✨

---

## Quick Checklist

Before starting Make.com:
- [✅] Typeform link ready
- [✅] Google Sheet link ready
- [✅] Gmail account ready
- [ ] Make.com account created
- [ ] 45-60 minutes set aside
- [ ] Coffee/tea prepared ☕

Let's build this!
