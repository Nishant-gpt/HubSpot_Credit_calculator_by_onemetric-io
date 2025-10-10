# HubSpot AI Credits Calculator

## Overview
A modern, single-file web application featuring a three-column layout with hero section, step-based navigation, and partner sales enablement tools. Built for OneMetric.io (Breeze by OneMetric.io).

## Purpose
Helps HubSpot customers estimate their monthly AI credit consumption with:
- Step-by-step guided workflow
- Partner talk-track guidance for sales conversations
- Smart expansion recommendations (Capacity Packs vs Overage)
- Goal-based prospecting calculations

## Technology Stack
- **Pure HTML/CSS/JavaScript** (vanilla, no frameworks)
- **No build tools required**
- **No external dependencies**
- **Client-side only** (no backend needed)

## Features

### Hero Section
- **Full-width gradient hero** with OneMetric.io branding
- **Left**: Breeze by OneMetric.io logo
- **Center**: H1 "HubSpot Credits Calculator" + subtitle
- **Right**: Live KPI card (Included/Projected/Net credits)
- **Collapsing behavior**: Smoothly collapses on scroll, replaced by sticky header

### Three-Column Layout
1. **Left Column**: Step navigation (7 steps) with visual active indicators
2. **Center Column**: Active step inputs + Summary block
3. **Right Column**: Dynamic partner talk-track panel

### Calculation Steps (Step-by-Step Workflow)
1. **Customer Agent**: Conversations per month × 100 credits
2. **Prospecting Agent (Monitor Contact)**: 
   - Direct Mode: Companies × Contacts/company × 100
   - Goal Mode: Meetings ÷ Conversion% = Companies
3. **Prospecting Agent (Company Research)**: Results × 10 credits
4. **Data Agent**: Questions × Records × Refreshes × 10 credits
5. **Breeze Workflows**: AI Actions × 10 credits
6. **Buyer Intent**: (Target Accounts + Additional) × 10 credits
7. **Data Hub**: Size Credits × Destinations × Sync Frequency

### Partner Talk-Track Panel
Dynamic content per step with:
- **Primary Question**: Main discovery question for sales conversations
- **If they don't know**: Alternative framing
- **Common Benchmark**: Industry standards
- **Formula**: Plain English calculation
- **Example**: Concrete example with numbers

### Smart Recommendations
- Shows Included credits, Projected usage, Net balance
- Color-coded (green = surplus, red = deficit)
- When deficit exists:
  - **Capacity Packs**: ceil(deficit/1000) × $10
  - **Overage**: ceil(deficit/10) × $0.10
  - Highlights cheaper option as "RECOMMENDED"
  - Helper text about use cases

### UX Enhancements
- **Quick-add chips**: +50/+100/+1000 on all numeric inputs
- **Theme toggle**: Dark/light mode with localStorage persistence
- **Sticky header**: Appears on scroll with condensed KPIs and CTA
- **Responsive design**: 3-col desktop, 2-col tablet, 1-col mobile

### Utilities
- **Share**: Generate shareable URL with encoded state
- **Export CSV**: Download detailed usage breakdown
- **Reset All**: Clear all inputs and restore defaults

### Data Model
The calculator includes complete pricing data for:
- 16 HubSpot AI features across 5 categories
- 6 plan tiers with included credits
- 2 expansion options

All data is embedded directly in the HTML file for offline operation.

## Design
- **Branding**: OneMetric.io
- **Style**: Minimal, enterprise-clean
- **Layout**: Three-panel responsive design
  - Left: Plan Setup
  - Center: Usage Inputs
  - Right: Projection Summary (sticky on desktop)
- **Mobile-first**: Responsive for all screen sizes
- **Visual elements**: Rounded cards, subtle shadows, strong typography

## Project Structure
```
.
├── index.html           # Complete application (single file)
├── TEST_RESULTS.md      # Comprehensive test documentation
└── replit.md           # This file
```

## Running the Application

### Local Development
```bash
python -m http.server 5000
```
Then open http://localhost:5000

### Replit
The app is configured to run automatically on port 5000. Just click "Run" or use the web preview.

## Testing
The application includes built-in testing hooks accessible via browser console:

```javascript
// Access current state
window.__test__.getState()

// Get calculated values
window.__test__.getIncludedCredits()
window.__test__.getProjectedUsage()
window.__test__.getNetBalance()

// Access data model
window.__test__.getCreditTable()
```

## How It Works

### Calculation Logic
1. **Included Credits** = Smart CRM tier credits + Data Hub tier credits
2. **Projected Usage** = Σ(feature count × credits per unit)
3. **Net Balance** = Included - Projected
4. **When deficit exists**:
   - Capacity Packs: ceil(deficit / 1000) × $10
   - Overage: ceil(deficit / 10) × $0.10
   - Recommends the cheaper option

### State Management
- State stored in JavaScript object
- Persisted to URL hash for sharing (base64-encoded JSON)
- Automatically loaded on page load if hash present

### CSV Export Format
```csv
Feature,Category,Count,Credits per Unit,Subtotal Credits
[usage rows...]

Summary
Included Credits,[total]
Projected Usage,[total]
Net Balance,[total]
```

## Browser Compatibility
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Recent Changes
- **2025-10-10**: Complete Refactor - Three-Column Layout
  - NEW: Hero section with collapsing behavior on scroll
  - NEW: Sticky header with condensed KPIs and CTA
  - NEW: Three-column layout (Steps | Inputs | Talk-Track)
  - NEW: Step-based navigation workflow (7 steps)
  - NEW: Partner talk-track panel with sales enablement content
  - NEW: Goal Mode for Prospecting Agent (meetings ÷ conversion = companies)
  - NEW: Quick-add chips (+50/+100/+1000) on all numeric inputs
  - NEW: Smart recommendations (Capacity Packs vs Overage comparison)
  - Enhanced: All calculations with visual formula displays
  - Enhanced: Responsive design (3-col/2-col/1-col)
  - Preserved: URL sharing, CSV export, theme toggle
  - Preserved: All calculation logic and credit rates

- **2025-10-09**: Branding Update
  - Replaced text logo with OneMetric logo image
  - Updated CTA to "Talk to an HubSpot expert" linking to www.onemetric.io

## Notes
- No API keys or secrets required
- All calculations happen client-side
- Works offline once loaded
- TBD/Beta features properly disabled and marked
- Clean, commented code for easy maintenance
