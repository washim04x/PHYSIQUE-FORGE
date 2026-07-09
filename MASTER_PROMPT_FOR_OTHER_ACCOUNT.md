# MASTER CONTEXT PROMPT — PERSONALIZED FITNESS WEB APP
# Copy this entire prompt and paste it into your other Gemini account
# along with BOTH research PDFs (Nutrition PDF + Exercise PDF)

---

## YOUR ROLE
You are an expert full-stack web developer AND elite sports nutritionist AND kinesiologist.
You have been given TWO deep research PDF documents:
1. A comprehensive Indian Sports Nutrition & Food Database PDF Y# Comprehensive Indian Sports Nutr.txt
2. A comprehensive Exercise & Training Protocol PDF # Part A Complete Exercise Database

Your task is to build a complete, stunning, premium-quality personalized fitness web app
using ONLY HTML + CSS + Vanilla JavaScript (single file or 2–3 files max).
NO backend server needed. NO Node.js. NO Python. NO database.
Everything runs in the browser, on the user's local machine, opened directly as an HTML file.

---

## WHAT THE APP DOES

A user visits the site and fills a one-page form with their personal details.
The app then generates a FULLY PERSONALIZED:
  1. Daily Diet Plan (6 meals, Indian foods, budget-matched, correct macros)
  2. Weekly Training Plan (4-day or 5-day split, goal-matched, phased over 8 weeks)

The output is displayed beautifully on the same page, and the user can PRINT it as a PDF.

---

## USER INPUT FORM — EXACT FIELDS REQUIRED

The form must collect:

1. Full Name (text input)
2. Age (number: 15–60)
3. Biological Sex (Male / Female)
4. Weight in kg (number: 35–150)
5. Height in cm (number: 140–210)
6. Primary Fitness Goal (dropdown):
   - Aesthetic V-Taper (wide shoulders, narrow waist, lean)
   - Classic Bodybuilder (maximize muscle mass)
   - Fat Loss / Weight Cut (lose fat, preserve muscle)
   - Strength & Powerlifting (raw strength)
   - Beginner General Fitness (just starting out)
   - Calisthenics / No Gym (bodyweight only)
7. Activity Level (dropdown):
   - Sedentary (desk job/student, no exercise)
   - Lightly Active (walk + occasional exercise)
   - Moderately Active (3–4 gym days per week)
   - Very Active (5–6 gym days per week)
   - Athlete (daily intense training)
8. Monthly Food Budget in ₹ (dropdown):
   - ₹1,000–1,500/month (hostel extreme budget)
   - ₹1,500–3,000/month (student budget)
   - ₹3,000–6,000/month (moderate budget)
   - ₹6,000–12,000/month (comfortable budget)
   - ₹12,000+/month (no budget restriction)
9. Cooking Access (dropdown):
   - Electric Kettle Only (hostel student)
   - Basic Kitchen (gas stove, vessel)
   - Full Kitchen (oven, multiple burners)
10. Gym Access (dropdown):
    - Full Gym (all machines and weights available)
    - Dumbbells Only (home setup)
    - Bodyweight / No Equipment
11. Dietary Preference (dropdown):
    - Non-Vegetarian (eggs + chicken + fish)
    - Vegetarian (eggs allowed, no meat)
    - Pure Vegetarian (no eggs, no meat)
    - Vegan (no animal products at all)
12. Any medical restrictions? (optional checkboxes):
    - Lower back injury (avoid deadlifts/heavy squats)
    - Knee issues (avoid deep squats)
    - Shoulder injury (modify pressing)
    - None

---

## CALCULATION ENGINE — HOW TO GENERATE THE PLAN

### Step 1: Calculate TDEE (Total Daily Energy Expenditure)
Use Mifflin-St Jeor Equation:
  Males: BMR = (10 × weight_kg) + (6.25 × height_cm) - (5 × age) + 5
  Females: BMR = (10 × weight_kg) + (6.25 × height_cm) - (5 × age) - 161

Activity multipliers:
  Sedentary = BMR × 1.2
  Lightly Active = BMR × 1.375
  Moderately Active = BMR × 1.55
  Very Active = BMR × 1.725
  Athlete = BMR × 1.9

### Step 2: Calculate Goal-Specific Caloric Target
  Aesthetic V-Taper / Body Recomposition: TDEE (maintenance, ±0)
  Classic Bodybuilder Bulk: TDEE + 300 kcal
  Fat Loss / Weight Cut: TDEE - 400 kcal
  Strength / Powerlifting: TDEE + 200 kcal
  Beginner General Fitness: TDEE - 100 kcal
  Calisthenics: TDEE (maintenance)

### Step 3: Calculate Macro Targets
  Aesthetic V-Taper:    Protein=2.0g/kg | Fat=0.8g/kg | Carbs=fill remainder
  Classic Bodybuilder:  Protein=2.2g/kg | Fat=1.0g/kg | Carbs=fill remainder
  Fat Loss:             Protein=2.4g/kg | Fat=0.8g/kg | Carbs=fill remainder
  Strength:             Protein=1.8g/kg | Fat=1.2g/kg | Carbs=fill remainder
  Beginner Fitness:     Protein=1.8g/kg | Fat=0.9g/kg | Carbs=fill remainder
  Calisthenics:         Protein=2.0g/kg | Fat=0.9g/kg | Carbs=fill remainder

### Step 4: Build a 6-Meal Daily Diet Plan from the Nutrition PDF data
Use the food macronutrient data from the Nutrition PDF to select foods that:
  a) Match the user's dietary preference (veg/non-veg/vegan)
  b) Can be prepared with their cooking access (kettle only, etc.)
  c) Fit within their monthly food budget
  d) Hit their macro targets across 6 meals

Meal timing structure (use these 6 slots):
  Meal 1 (06:30 AM) — Wake-up / Pre-morning (light, fast to prepare)
  Meal 2 (08:30 AM) — Pre-workout fuel (if training morning)
  Meal 3 (11:00 AM) — Lunch / Main meal
  Meal 4 (02:00 PM) — Afternoon snack
  Meal 5 (06:00 PM) — Post-workout / Evening meal
  Meal 6 (09:00 PM) — Dinner / Before-sleep protein

For each meal, display:
  - Meal name + time
  - List of food items with exact gram quantities
  - Per-meal macro breakdown (protein, carbs, fat, kcal)
  - Simple preparation instructions (1–2 sentences)

At the bottom of the diet plan show a DAILY TOTAL row with grand total macros vs target.

Include a monthly budget breakdown table showing which foods to buy, quantity needed 
per month, per-unit price, and total monthly cost. Final row = Total ₹/month.

### Step 5: Build a Weekly Training Plan from the Exercise PDF data
Select training split based on goal:
  Aesthetic V-Taper:   4-day split (Push/Pull/Legs-Core/V-Taper Specific)
  Classic Bodybuilder: 5-day split (Chest/Back/Shoulders/Arms/Legs)
  Fat Loss:            4-day Upper/Lower split + 2 LISS cardio days
  Strength:            4-day powerlifting (Squat/Bench/Deadlift/Accessory)
  Beginner Fitness:    3-day Full Body (Mon/Wed/Fri)
  Calisthenics:        4-day bodyweight (Push/Pull/Legs/Skills)

Adjust exercises based on gym access:
  Full Gym: full machine + barbell + dumbbell selection
  Dumbbells Only: dumbbell-only alternatives for every exercise
  Bodyweight: calisthenics alternatives for every exercise

Adjust for medical restrictions:
  Lower back: replace all deadlifts with hip thrusts + hyperextensions
  Knee: replace deep squats with leg press + terminal knee extensions
  Shoulder: replace overhead press with cable lateral raises + incline press

For each training day show a table with:
  # | Exercise | Muscle(s) | Sets × Reps | Rest | Mind-Muscle Cue

Show Phase 1 (Weeks 1–4) and Phase 2 (Weeks 5–8) separately for each day.
Phase 2 must include advanced techniques pulled from the Exercise PDF:
  - V-Taper goal: Drop Sets on all deltoid, 3-sec Eccentric on all back
  - Bodybuilder: Supersets, rest-pause
  - Fat Loss: Circuit format, shorter rest
  - Strength: Wave loading, cluster sets

---

## DESIGN REQUIREMENTS — PREMIUM DARK AESTHETIC

### Visual Style
- Dark background: #0D0D0D (near-black)
- Gold accent: #C9A84C with light variant #F0C96A
- Card backgrounds: #141414 and #1A1A1A
- Borders: #2A2A2A
- Body text: #E0E0E0
- Muted text: #888888
- Success/protein green: #2ECC71
- Warning red: #E03535
- Phase 1 blue: #1E90FF
- Phase 2 gold: #F0C96A

### Fonts (load from Google Fonts)
- Headings/Display: 'Bebas Neue' (dramatic, strong)
- UI/Numbers: 'Rajdhani' (technical, clean)
- Body text: 'Inter' (highly legible)

### Layout Structure
1. HERO SECTION — Full viewport height cover
   - Animated gradient background (dark to gold tones)
   - App name: "PHYSIQUE FORGE" in Bebas Neue, massive text
   - Tagline: "Your Personal Physique Blueprint — Engineered for Indian Bodies"
   - Floating particle animation or subtle pulse effect in background
   - Scroll-down arrow bouncing animation

2. FORM SECTION — Full-width card with glassmorphism effect
   - Split into 3 columns on desktop, 1 column on mobile
   - Each input has a label, icon, and hover glow effect
   - Progress indicator (Step 1/3, Step 2/3, Step 3/3 if multi-step)
   - Submit button: large, gold gradient, "GENERATE MY BLUEPRINT" text
   - Button has shimmer/pulse animation
   - Form validation with inline error messages in red

3. RESULTS SECTION — Hidden until form submitted
   - Appears with smooth fade-in animation
   - User's name displayed in hero text at top
   - Tab navigation: [📊 Your Stats] [🍱 Diet Plan] [🏋️ Training Plan] [💡 Tips]

   TAB 1 — YOUR STATS
   - Large metric cards: BMR | TDEE | Target kcal | Goal
   - Macro ring chart (CSS-only donut chart: protein=green, carbs=yellow, fat=orange)
   - Body stats summary card
   - Phase timeline (8-week visual bar)

   TAB 2 — DIET PLAN
   - Daily meal timeline (vertical, like a schedule)
   - Each meal is a card with expand/collapse animation
   - Per-meal macro mini-bars
   - Total daily macro summary bar chart
   - Monthly grocery list table with ₹ totals
   - Budget compliance indicator (green = within budget, red = over)
   - "What to avoid" callout box (red border, warning icon)

   TAB 3 — TRAINING PLAN
   - Weekly calendar view (Mon–Sun grid)
   - Each workout day is a clickable card that expands
   - Exercise table inside each day (Phase 1 shown by default, toggle to Phase 2)
   - Phase 2 technique badges (Drop Set in red, 3-Sec Eccentric in purple, etc.)
   - Day header shows: Day number, muscle groups, estimated time
   - Muscle group tags on each day card

   TAB 4 — TIPS
   - Goal-specific advice cards
   - Sleep recommendation
   - Hydration targets (bodyweight kg × 33ml)
   - Supplement recommendations from the research PDF
   - Common mistakes for that goal
   - Progress tracking guide

4. FOOTER — Dark, minimal
   - "Physique Forge — Powered by AI Research"
   - Note: "Consult a healthcare professional before starting any new diet or exercise program"

### Animation Requirements
- Hero section: floating particle background or animated gradient shift
- Form inputs: focus glow (gold border glow on focus)
- Submit button: shimmer sweep animation on hover
- Results appear: staggered fade-in animation (each card 0.1s delay apart)
- Tab switching: smooth slide/fade transition
- Exercise cards: expand with smooth max-height transition
- All hover effects on cards: slight Y-axis lift (transform: translateY(-4px))
- Macro donut chart: CSS-only animated ring (no Chart.js needed)
- Phase timeline: animated progress bar fill

### Responsive Design
- Desktop: 3-column form layout, wide exercise tables
- Tablet: 2-column form, scrollable tables
- Mobile: 1-column, card-based stacked layout, tables scroll horizontally

### Print / PDF Export
- "Download as PDF" button that triggers window.print()
- @media print CSS: white background, black text, remove animations
- All data prints cleanly on A4

---

## TECHNICAL IMPLEMENTATION NOTES

### File Structure (single file preferred):
index.html — Contains ALL HTML + embedded CSS + embedded JavaScript

### JavaScript Architecture:
1. foodDatabase object — embed key foods from Nutrition PDF as JS object
   Structure: { "egg_boiled": { kcal: 155, protein: 13, carbs: 1.1, fat: 11, 
   price_per_100g_inr: 8, prep: "kettle", diet: ["non-veg"] }, ... }

2. exerciseDatabase object — embed exercises from Exercise PDF as JS object
   Structure: { "lateral_raise": { muscle: "lateral_deltoid", equipment: ["dumbbells"],
   phase1: {sets:4, reps:"12-15", rest:"60s"}, 
   phase2: {sets:5, reps:"15+drop", rest:"45s", technique:"triple_drop_set"},
   cue: "Lead with elbows at 45°...", goals: ["vtaper", "bodybuilder"] }, ... }

3. trainingPlans object — pre-defined 4-day and 5-day splits per goal
   Maps goal → array of training days → array of exercise IDs

4. mealBuilder function — takes (macroTargets, budget, dietPref, cookingAccess) 
   → returns array of 6 meal objects each with foods + quantities + macros

5. planGenerator function — main entry point
   Takes all form values → runs all calculations → returns full plan object

6. renderPlan function — takes plan object → renders all HTML into results section

### Data Embedding Strategy:
Since the Nutrition PDF and Exercise PDF contain hundreds of data points, embed 
the MOST IMPORTANT ones (top 30 foods, top 8 exercises per muscle group) directly 
in the JavaScript. Do NOT try to embed everything — be selective and choose the 
foods/exercises that cover 90% of use cases based on what's in the PDFs.

---

## CONTENT TO EXTRACT FROM THE NUTRITION PDF

From the PDF, extract and embed as JavaScript data:
1. Top 25 most common Indian fitness foods with exact macros per 100g
2. Budget price per 100g in ₹ (use Kolkata/general India 2025-2026 prices)
3. Cooking method tag for each (kettle / basic-kitchen / full-kitchen / no-prep)
4. Dietary tag for each (non-veg / veg / vegan)
5. Goal suitability tags (protein-source / carb-source / fat-source / all-purpose)
6. Kettle preparation method in 1 sentence

---

## CONTENT TO EXTRACT FROM THE EXERCISE PDF

From the PDF, extract and embed as JavaScript data:
1. 6–8 exercises per muscle group (prioritize most effective ones)
2. For each exercise: sets, reps, rest for Phase 1 AND Phase 2
3. Mind-muscle cue (1 sentence, taken from the PDF's technique section)
4. Equipment required tag (barbell / dumbbell / machine / cable / bodyweight)
5. Goal suitability tags (vtaper / bodybuilder / fat-loss / strength / beginner / calisthenics)
6. Any waist-thickening warning tag (from the anti-waist-thickening guide in the PDF)

---

## SPECIAL RULE: AESTHETIC V-TAPER GOAL

When the user selects "Aesthetic V-Taper" as their goal:
  - NEVER include: barbell squat, conventional deadlift, weighted crunches, 
    Russian twists, cable side bends, heavy barbell overhead press
  - ALWAYS include: lateral raises (dumbell + cable), wide-grip pulldowns, 
    face pulls, straight-arm pulldowns, single-arm cable lateral raise
  - Core work = planks, hollow body holds, hanging leg raises ONLY
  - Show a special callout box: "⚠️ Waist-First Protocol Active — 
    Exercises that thicken the obliques have been automatically excluded"
  - Phase 2 for V-Taper: Drop Sets on ALL deltoid movements, 
    3-Sec Eccentric on ALL lat/back movements

---

## EXAMPLE OUTPUT STRUCTURE FOR CLARITY

When a user enters: Name=Ravi, Age=22, Male, 70kg, 172cm, 
Goal=Aesthetic V-Taper, Activity=Moderately Active, 
Budget=₹1,500–3,000/month, Cooking=Kettle Only, Gym=Full Gym, Diet=Non-Vegetarian

The app should calculate:
  BMR = (10×70) + (6.25×172) - (5×22) + 5 = 700+1075-110+5 = 1670
  TDEE = 1670 × 1.55 = 2,588 → round to 2,600 kcal
  Target = TDEE (recomp, no surplus/deficit) = 2,600 kcal
  Protein = 70kg × 2.0 = 140g = 560 kcal
  Fat = 70kg × 0.8 = 56g = 504 kcal
  Carbs = (2600-560-504)/4 = 384 kcal = 96g → wait that's too low
  (Note: adjust the formula so carbs are not too low — use 40/30/30 as fallback)
  Better: Protein=140g(560kcal=22%), Carbs=260g(1040kcal=40%), Fat=111g(999kcal=38%)
  
Diet for kettle-only budget ₹1,500–3,000:
  Meal 1 (6:30am): 40g Sattu + hot water + lemon → 11g P / 23g C / 4g F / 170 kcal
  Meal 2 (8:30am): 4 boiled eggs + 50g soya chunks → 42g P / 10g C / 20g F / 390 kcal
  Meal 3 (11am): 250g cooked rice + 100g chicken → 32g P / 70g C / 8g F / 475 kcal
  etc.

Training (V-Taper, Full Gym):
  Monday: DAY 1 — PUSH (Chest/Shoulders/Triceps)
  Phase 1: Incline DB Press 4×8-10 | Seated DB Press 3×8-12 | Lateral Raise 4×12-15 | etc.
  Phase 2: Incline DB Press 4×6-8 | Seated DB Press DROP SET 4×10+drop | 
           Lateral Raise TRIPLE DROP SET 5×15+12+10 | etc.

---

## FINAL DELIVERABLE

Build the COMPLETE web app as a single HTML file.
The file should be named: physique_forge.html
It must work when opened directly in Chrome or Edge (file:/// protocol, no server needed).
All CSS must be embedded in <style> tags.
All JavaScript must be embedded in <script> tags.
Google Fonts should be loaded from the CDN link in the <head>.

The MINIMUM viable app must include:
✅ The complete input form with all 12 fields
✅ TDEE + macro calculation logic
✅ Diet plan generator with at least 20 Indian foods embedded as data
✅ Training plan generator with at least 5 exercises per muscle group
✅ Beautiful dark/gold premium UI with all animations
✅ Results displayed in 4 tabs
✅ Print-to-PDF functionality
✅ Mobile responsive layout
✅ Input validation with error messages

DO NOT use any external libraries except Google Fonts.
DO NOT require a server or backend.
DO NOT use placeholder content — use real data from the two PDFs provided.

Build the ENTIRE app in one response. Do not split across multiple messages.
The final file should be ready to open immediately in a browser.
