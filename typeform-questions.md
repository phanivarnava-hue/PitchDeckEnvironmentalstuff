# Typeform Questions for EV Calculator
## Complete Question Flow with Logic

---

## Form Title
**"EV vs Petrol: Which is Really Greener in the Netherlands?"**

**Subtitle:**
*Lifecycle emissions comparison based on real Dutch data from CE Delft and Nowtricity. Takes 2 minutes.*

---

## Question 1: Welcome Screen

**Type:** Welcome Screen (not a question)

**Title:**
"Let's Calculate Your Real Carbon Footprint"

**Description:**
```
Many people are skeptical about electric vehicles in the Netherlands.

"Isn't battery production super polluting?"
"Our electricity grid isn't clean enough, right?"
"Don't you need to drive 100,000 km before it's worth it?"

Let's answer these questions with real data.

This calculator compares the FULL lifecycle emissions:
✓ Manufacturing (including battery)
✓ Driving (based on NL electricity grid)
✓ Maintenance
✓ End-of-life/recycling

You'll get a personalized report showing exactly when an EV becomes cleaner than petrol/diesel.

Takes 2 minutes. No email required (unless you want the full report).
```

**Button Text:** "Start Calculator"

---

## Question 2: Car Size

**Type:** Multiple Choice (Required)

**Question:**
"What size car are you comparing?"

**Choices:**
- 🚗 **Small** (e.g., VW Polo, Nissan Leaf, VW ID.3)
- 🚙 **Medium** (e.g., VW Golf, Tesla Model 3, Toyota Corolla)
- 🚐 **Large/SUV** (e.g., VW Tiguan, Tesla Model Y, Audi e-tron)

**Helper Text:**
*Choose the size that matches your current or future car.*

**Variable Name:** `car_size`
**Values:** Small / Medium / Large

---

## Question 3: Compare Against

**Type:** Multiple Choice (Required)

**Question:**
"What would you compare the electric car to?"

**Choices:**
- ⛽ **Petrol car** (benzine)
- 🛢️ **Diesel car**
- 🔋 **Hybrid** (plug-in hybrid)

**Helper Text:**
*Most common comparison is petrol. Choose what you'd actually buy if not electric.*

**Variable Name:** `compare_to`
**Values:** Petrol / Diesel / Hybrid

---

## Question 4: Annual Kilometers

**Type:** Slider (Required)

**Question:**
"How many kilometers do you drive per year?"

**Slider Settings:**
- Minimum: 5,000 km
- Maximum: 40,000 km
- Default: 15,000 km
- Step: 1,000 km

**Helper Text:**
*Netherlands average is 12,500 km/year. Be honest - this affects the result!*

**Variable Name:** `km_per_year`
**Value:** Number (5000-40000)

---

## Question 5: Ownership Period

**Type:** Multiple Choice (Required)

**Question:**
"How long do you typically keep your cars?"

**Choices:**
- **5 years** (shorter ownership)
- **10 years** (most common)
- **15 years** (keep until it dies)

**Helper Text:**
*The longer you keep it, the more an EV's advantage grows.*

**Variable Name:** `years_owned`
**Values:** 5 / 10 / 15

---

## Question 6: Solar Panels

**Type:** Multiple Choice (Required)

**Question:**
"Do you have solar panels at home?"

**Choices:**
- ☀️ **Yes, I have solar panels** (charging would be cleaner)
- ⚡ **No, just regular grid electricity**
- 🔮 **Planning to get them soon**

**Helper Text:**
*Solar panels make EVs even cleaner! If planning to get them, choose "Yes" to see the potential.*

**Variable Name:** `has_solar`
**Values:** Yes / No / Planning

**Logic:**
- If "Yes" or "Planning" → Use EV_Solar variant from Google Sheets
- If "No" → Use standard EV variant

---

## Question 7: Email (Optional)

**Type:** Email (Optional)

**Question:**
"Want the full report sent to your email?"

**Description:**
```
Optional! You'll see the basic results on the next page.

But if you want:
✓ Detailed year-by-year breakdown
✓ Cost comparison (purchase + fuel)
✓ Downloadable PDF report
✓ Sources and methodology

Enter your email below.
```

**Placeholder:** your.email@example.com

**Variable Name:** `user_email`
**Value:** Email address or blank

---

## Question 8: Optional - Driving Type

**Type:** Multiple Choice (Optional)

**Question:**
"What type of driving do you mostly do?"

**Choices:**
- 🏙️ **Mostly city** (lower speeds, more regen braking)
- 🛣️ **Mixed city/highway** (average)
- 🚗 **Mostly highway** (higher speeds, less efficient)

**Helper Text:**
*Optional - helps fine-tune the calculation slightly.*

**Variable Name:** `driving_type`
**Values:** City / Mixed / Highway

**Logic:**
- This adjusts efficiency slightly (±5%)
- City: -5% from base operational emissions (EVs more efficient)
- Highway: +5% from base operational emissions
- Mixed: No adjustment

---

## Question 9: Final Screen - Processing

**Type:** Statement Screen

**Title:**
"Calculating your results..."

**Description:**
```
⚡ Comparing lifecycle emissions
📊 Calculating break-even point
🌳 Converting to real-world equivalents

This will take 5-10 seconds.
```

**Note:** This screen shows while Make.com processes the data

---

## Question 10: Thank You Screen

**Type:** Statement Screen

**Title:**
"Results are ready!"

**Description:**
```
✅ Your personalized comparison has been generated.

{{#if user_email}}
📧 We've sent the full report to: {{user_email}}
Check your inbox (and spam folder just in case).
{{else}}
📊 See your basic results below:

[Results will be displayed here - see "Results Display" section]
{{/if}}

🔗 Share this calculator:
[LinkedIn] [Twitter] [WhatsApp]

📄 Want to see the methodology and sources?
[Link to: /methodology page]

---

Built by [Your Name]
Data sources: CE Delft, Nowtricity, TNO
Last updated: January 2026
```

---

## Results Display (On Thank You Page or Email)

### Basic Results (Shown on Thank You page)

**Format:**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
YOUR RESULTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Car Size: {{car_size}}
Comparison: EV vs {{compare_to}}
Annual Driving: {{km_per_year}} km
Ownership: {{years_owned}} years
{{#if has_solar}}☀️ With solar panels{{/if}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🔋 ELECTRIC CAR
Total Lifetime CO2: {{ev_total_co2}} kg
   Manufacturing: {{ev_manufacturing}} kg
   Driving ({{total_km}} km): {{ev_driving}} kg
   Maintenance: {{ev_maintenance}} kg

⛽ {{compare_to|uppercase}} CAR
Total Lifetime CO2: {{conventional_total_co2}} kg
   Manufacturing: {{conventional_manufacturing}} kg
   Driving ({{total_km}} km): {{conventional_driving}} kg
   Maintenance: {{conventional_maintenance}} kg

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ THE VERDICT

Electric is {{percentage_cleaner}}% cleaner over {{years_owned}} years.

You'll save {{co2_saved}} kg CO2 total.

💡 Break-even point: {{breakeven_km}} km
   (That's {{breakeven_years}} years at your driving rate)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🌳 WHAT DOES THAT MEAN?

Your CO2 savings equals:
• {{trees_equivalent}} trees planted and grown for 1 year
• {{flights_equivalent}} Amsterdam-Paris flights avoided

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

⚠️ IMPORTANT CONTEXT

• Yes, EV battery production is emissions-intensive
• But lower operational emissions quickly make up for it
• Netherlands grid is getting cleaner each year (more renewables)
• These calculations use current NL grid mix (28% renewable)
{{#if has_solar}}
• With your solar panels, EV is even cleaner!
{{/if}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Variable Summary (For Make.com Mapping)

| Variable Name | Type | Values | Required |
|---------------|------|--------|----------|
| car_size | Choice | Small/Medium/Large | Yes |
| compare_to | Choice | Petrol/Diesel/Hybrid | Yes |
| km_per_year | Number | 5000-40000 | Yes |
| years_owned | Choice | 5/10/15 | Yes |
| has_solar | Choice | Yes/No/Planning | Yes |
| user_email | Email | email or blank | Optional |
| driving_type | Choice | City/Mixed/Highway | Optional |

---

## Typeform Settings

### Design Settings:
- **Theme:** Use custom colors (Dutch Blue #01689B, Orange #F39200)
- **Font:** Clean sans-serif (Karla or Inter)
- **Button text:** "Continue" → "Next" → "Calculate"

### Notifications:
- **Admin notification:** Send to your email when form is submitted
- **Respondent email:** Only if they provide email

### Share Settings:
- **Public link:** Yes (anyone can access)
- **Embed:** Enable (for landing page later)

---

## Logic Rules in Typeform

### Rule 1: Solar Panel Logic
```
IF has_solar = "Yes" OR has_solar = "Planning"
THEN Hidden field: solar_variant = "Yes"
ELSE Hidden field: solar_variant = "No"
```

### Rule 2: Driving Type Adjustment (Optional)
```
IF driving_type = "City"
THEN Hidden field: efficiency_multiplier = 0.95

IF driving_type = "Highway"
THEN Hidden field: efficiency_multiplier = 1.05

IF driving_type = "Mixed" OR blank
THEN Hidden field: efficiency_multiplier = 1.00
```

---

## Next Steps After Typeform is Built

1. ✅ Create Typeform using this structure
2. ✅ Copy Typeform webhook URL (for Make.com)
3. ✅ Test it yourself (fill it out 3-5 times)
4. ✅ Ready to connect to Make.com

---

## Pro Tips for Typeform

**1. Use Images:**
- Add car images to Q2 (Small/Medium/Large) to make it visual
- Add icons to choices (emoji work!)

**2. Progress Bar:**
- Enable progress bar (users like seeing how far they are)
- 7 questions = quick completion

**3. Mobile Optimization:**
- Test on phone (most people will use mobile)
- Keep text concise

**4. A/B Testing:**
- Later you can test different welcome messages
- Track completion rate

---

## Typeform Free Tier Limits

**What's included (free):**
- ✅ Unlimited questions
- ✅ 100 responses per month
- ✅ Basic logic jumps
- ✅ Email notifications

**What requires paid ($25/month):**
- ❌ >100 responses
- ❌ Remove Typeform branding
- ❌ Custom thank you page redirect
- ❌ File uploads

**For MVP: Free tier is enough!**

Once you get >100 responses/month, upgrade = validation that it's working!

---

## Ready to Build?

1. Go to [typeform.com](https://typeform.com)
2. Sign up (free account)
3. Click "Create a typeform"
4. Copy these questions one by one
5. When done, grab the webhook URL

Let me know when your Typeform is built and I'll create the Make.com automation flow!
