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

### Header (Sticky 56px)
- **Left**: OneMetric.io logo · Breeze branding
- **Center**: "HubSpot Credits Calculator" title
- **Right**: "How credits work" + "Talk to an expert" (OneMetric.io link)

### Sidebar Navigation (280px)
- **8 calculator steps** with icons, labels, and live credit badges
- **Active step highlighting** with purple border and background tint
- **Per-step credit totals** update in real-time as inputs change
- **Responsive behavior**: Horizontal scroll on mobile

### Content Card
- **Clean, focused design** with step title and helper text
- **Next section button** for easy step-by-step navigation
- **Tool cards** for interactive configuration options
- **Section cards** group related inputs

### Calculation Steps
1. **Subscription Base**: Plan selection (Starter/Pro/Enterprise) + Data Hub toggle
2. **Customer Agent**: Conversations × 100 credits
3. **Prospecting Agent**: 
   - Monitor Contact (Direct/Goal Mode) × 100 credits
   - Company Research × 10 credits
4. **Data Agent**: Questions × Records × Refreshes × 10 credits
5. **Buyer Intent**: (Target + Additional) × 10 credits
6. **Breeze Workflows**: AI Actions × 10 credits
7. **Data Hub**: Dataset Size × Destinations × Sync Frequency
8. **Results**: Summary, top drivers, expansion recommendations

### Tool Cards
- **Selectable cards** for plan tiers, modes, dataset sizes
- **Visual feedback** with purple highlight when active
- **Icon + name + helper text** for clarity

### Results Step (Dedicated)
- **Summary cards**: Included, Projected, Net balance
- **Top 3 drivers**: Visual bar chart showing largest credit consumers
- **Expansion options**: Capacity Packs vs Overage comparison
- **Recommended badge**: Highlights cheaper expansion option
- **Export actions**: CSV download, Share URL, Reset calculator

### UX Features
- **Quick-add chips**: +50/+100/+1000 on numeric inputs
- **Toggle switches**: Clean UI for boolean options
- **Input helpers**: Inline explanatory text below each input
- **Responsive design**: Adapts from desktop to mobile
- **Purple/coral theme**: Primary #7C3AED, Accent #FF7A59

### Utilities
- **Share**: Copy shareable URL with base64-encoded state
- **Export CSV**: Download detailed usage breakdown
- **Reset**: Clear all inputs and restore defaults
- **URL state**: Automatic loading from shared links

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
- **2025-10-10**: Complete UI Redesign - Sidebar Layout
  - NEW: Sidebar navigation (280px) with 8 steps, icons, and live credit badges
  - NEW: Sticky header (56px) with OneMetric.io · Breeze branding
  - NEW: Tool card interface for plan selection, mode switching, dataset sizes
  - NEW: Dedicated Results step with summary, top drivers, and expansion options
  - NEW: Purple/coral color scheme (Primary: #7C3AED, Accent: #FF7A59)
  - NEW: Per-step credit totals displayed in sidebar badges (live updates)
  - NEW: Clean, focused design matching modern SaaS UI patterns
  - Enhanced: Responsive sidebar (horizontal scroll on mobile)
  - Enhanced: Visual hierarchy with cards, shadows, and rounded corners
  - Preserved: All calculation formulas and credit rates
  - Preserved: URL state encoding, CSV export, reset functionality
  - Preserved: Direct & Goal Mode for Prospecting Agent

- **2025-10-09**: Branding Update
  - Replaced text logo with OneMetric logo image
  - Updated CTA to "Talk to an HubSpot expert" linking to www.onemetric.io

## Notes
- No API keys or secrets required
- All calculations happen client-side
- Works offline once loaded
- TBD/Beta features properly disabled and marked
- Clean, commented code for easy maintenance
