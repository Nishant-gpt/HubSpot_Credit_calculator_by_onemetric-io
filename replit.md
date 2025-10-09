# HubSpot AI Credits Calculator

## Overview
A single-file, zero-backend web application that calculates projected monthly HubSpot AI credit usage and cost. Built for OneMetric.io with a clean, enterprise-grade design.

## Purpose
Helps HubSpot customers estimate their monthly AI credit consumption and associated costs, with clear recommendations for expansion options when credits run low.

## Technology Stack
- **Pure HTML/CSS/JavaScript** (vanilla, no frameworks)
- **No build tools required**
- **No external dependencies**
- **Client-side only** (no backend needed)

## Features

### Core Functionality
1. **Plan Configuration**
   - Smart CRM/Marketing/Sales/Service/Content Hub tier selection (Starter/Pro/Enterprise)
   - Data Hub/Customer Platform tier selection (None/Starter/Pro/Enterprise)
   - Automatic calculation of included credits

2. **Usage Estimation**
   - Input fields for all HubSpot AI features
   - Organized by category (Agents, Automation, Buyer Intent, Data Studio, Beta Agents)
   - Real-time credit calculation as you type
   - Help tooltips for each feature

3. **Projection & Recommendations**
   - Shows included credits, projected usage, and net balance
   - Color-coded results (green = surplus, red = deficit)
   - Smart expansion recommendations when credits run out:
     - Capacity Packs ($10 per 1,000 credits)
     - Overage/Pay-as-you-go ($0.01 per credit, 10-credit minimum)
   - Automatically highlights the cheaper option

4. **Utilities**
   - **Reset**: Clear all inputs and restore defaults
   - **Export CSV**: Download detailed usage breakdown
   - **Share**: Generate shareable URL with encoded state

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
- **2025-10-09**: Initial implementation
  - Complete single-file calculator created
  - All features implemented and tested
  - OneMetric.io branding applied
  - Responsive design completed
  - Export and sharing functionality added
  - Testing hooks implemented

## Notes
- No API keys or secrets required
- All calculations happen client-side
- Works offline once loaded
- TBD/Beta features properly disabled and marked
- Clean, commented code for easy maintenance
