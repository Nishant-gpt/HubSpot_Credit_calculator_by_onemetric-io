# HubSpot Credits Calculator - Refactor Documentation

## Overview
Complete refactor of the HubSpot AI Credits Calculator into a modern three-column layout with enhanced user experience and partner sales enablement features.

## Key Changes

### 🎨 Visual Design

#### Hero Section
- **Full-width gradient hero** with OneMetric.io branding
- **Left**: Breeze by OneMetric.io logo
- **Center**: H1 "HubSpot Credits Calculator" + subtitle
- **Right**: Live KPI card showing Included/Projected/Net credits
- **Collapsing behavior**: Smoothly collapses on scroll

#### Sticky Header
- Appears when scrolling past 200px
- Shows condensed KPIs (Included/Projected/Net)
- Includes "Talk to an HubSpot expert" CTA button
- Links to www.onemetric.io

#### Three-Column Layout
1. **Left Column (250px)**: Step navigation with visual indicators
2. **Center Column (flexible)**: Active step inputs and summary
3. **Right Column (350px)**: Dynamic partner talk-track panel

### 🔢 Feature Implementation

#### Step 1: Customer Agent
- **Input**: Conversations per month
- **Formula**: conversations × 100 credits
- **Quick-add chips**: +50, +100, +1000
- **Talk-track**: Full guidance for sales conversations

#### Step 2: Prospecting Agent (Monitor Contact)
- **Two modes via tabs**:
  - **Direct Input**: Companies/month × Contacts/company
  - **Goal Mode**: Meetings needed ÷ Conversion rate = Companies
- **Default contacts/company**: 2 (editable)
- **Benchmark chip**: "50–100 accounts/rep/month"
- **Formula**: companies × contacts/company × 100 credits
- **Quick-add chips**: Contextual based on active mode

#### Step 3: Prospecting Agent (Company Research)
- **Input**: Research results per month
- **Formula**: results × 10 credits
- **Quick-add chips**: +50, +100, +1000

#### Step 4: Data Agent
- **Three inputs**:
  - Questions per record
  - New records per month
  - Refreshes per month (dropdown: 1/4/30)
- **Formula**: questions × records × refreshes × 10
- **Quick-add chips**: Contextual per field

#### Step 5: Breeze Workflows
- **Input**: AI actions per month
- **Formula**: actions × 10 credits
- **Quick-add chips**: +50, +100, +1000

#### Step 6: Buyer Intent
- **Two inputs**:
  - Target accounts
  - Additional companies
- **Formula**: (targets + additional) × 10 credits
- **Quick-add chips**: +10, +50, +100 per field

#### Step 7: Data Hub
- **Three dropdowns**:
  - Dataset size (Small 25 / Medium 75 / Large 200 credits)
  - Destinations (number input)
  - Sync frequency (One-time 1, Monthly 1, Daily 30, Hourly 700, Fifteen-min 2900)
- **Formula**: sizeCredits × destinations × frequency

### 📊 Summary Block

#### Credit Display
- **Included Credits**: Default 500 (Starter tier)
- **Projected Usage**: Sum of all step calculations
- **Net Balance**: Included - Projected
  - Green if positive
  - Red if negative

#### Smart Recommendations (when deficit exists)
- **Capacity Packs**: ceil(deficit / 1000) × $10
- **Overage**: ceil(deficit / 10) × $0.10
- **Recommended badge**: Shows cheaper option
- **Helper text**: "Capacity packs suit consistent overages; overage is fine for spikes."

### 💡 Partner Talk-Track Panel

Dynamic content that updates per step with:
- **Primary Question**: Main discovery question
- **If they don't know**: Alternative framing
- **Common Benchmark**: Industry standards
- **Formula**: Plain English calculation
- **Example**: Concrete example with numbers

### ⚙️ Technical Features

#### State Management
```javascript
state = {
  currentStep: 0,
  included: 500,
  usage: {
    'customer-agent': 0,
    'prospecting-agent-monitor-contact': 0,
    'prospecting-monitor-mode': 'direct',
    'prospecting-monitor-companies': 0,
    'prospecting-monitor-contacts-per-company': 2,
    // ... all other usage values
  }
}
```

#### URL Sharing
- State encoded as base64 JSON in URL hash
- One-click copy to clipboard
- Automatic state restoration on load

#### CSV Export
- Feature, Usage, Credits/Unit, Total Credits
- Professional formatting
- One-click download

#### Theme Support
- Dark mode (default)
- Light mode
- Saved in localStorage
- Smooth transitions

### 🎯 UX Enhancements

#### Quick-Add Chips
- Contextual values per input type
- Hover effect with primary color
- Immediate calculation update

#### Input Validation
- Min/max constraints
- Step values for percentages
- Real-time visual feedback

#### Responsive Design
- Desktop: Full three-column layout
- Tablet: Hide talk-track panel, two columns
- Mobile: Single column stack, steps collapse

#### Accessibility
- Semantic HTML
- ARIA labels
- Keyboard navigation
- Focus indicators

### 📱 Responsive Breakpoints

```css
@media (max-width: 1200px) {
  /* Two columns: Steps + Inputs */
  /* Talk-track panel hidden */
}

@media (max-width: 768px) {
  /* Single column stack */
  /* Steps not sticky */
  /* Simplified header */
}
```

## Migration Notes

### Preserved from Original
- ✅ All calculation logic and credit rates
- ✅ URL state encoding/decoding
- ✅ CSV export functionality
- ✅ Theme toggle
- ✅ OneMetric.io branding
- ✅ Color palette (coral/orange primary)

### New Features
- ✅ Hero section with collapsing behavior
- ✅ Sticky header with KPIs
- ✅ Three-column layout
- ✅ Step-based navigation
- ✅ Goal Mode for Prospecting Agent
- ✅ Quick-add chips on all inputs
- ✅ Partner talk-track panel
- ✅ Smart recommendations (Capacity Packs vs Overage)
- ✅ Enhanced visual design

### Removed Features
- ❌ Plan selection (Smart CRM / Data Hub tiers) - Now uses default 500 credits
- ❌ Tooltips - Replaced with always-visible talk-track panel
- ❌ Old three-card layout - Now step-based workflow

## File Structure

```
index.html (single file)
├── <style> (all CSS)
├── <body>
│   ├── Hero section
│   ├── Sticky header
│   ├── Main three-column container
│   │   ├── Steps navigation
│   │   ├── Input panel + Summary
│   │   └── Talk-track panel
│   └── Theme toggle button
└── <script> (all JavaScript)
```

## Performance Optimizations

- **No dependencies**: Pure vanilla JS/CSS
- **Single file**: No network requests
- **Optimized rendering**: Only active step rendered
- **Efficient calculations**: Real-time updates without lag
- **Lazy scroll effects**: Smooth collapsing behavior

## Browser Compatibility

- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

## Future Enhancements

Potential additions:
1. Plan tier selection (Smart CRM / Data Hub)
2. Multiple currency support
3. Historical tracking
4. PDF export
5. Comparison mode (multiple scenarios)
6. Integration with HubSpot API
7. Team collaboration features
8. Admin dashboard
