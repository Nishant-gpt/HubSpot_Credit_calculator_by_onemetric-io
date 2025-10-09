# HubSpot AI Credits Calculator - Changelog

## Enhanced Calculator Update

### ✨ New Features

#### 1. Customer Agent - Visible Help Text
- **Added:** Always-visible help text below Customer Agent input field
- **Help Text:** "Estimate how many tickets or conversations each customer support agent is expected to handle per month. This helps calculate the AI cost per agent based on real workload."
- **Implementation:** No longer uses tooltip/hover - text is permanently displayed for better accessibility

#### 2. Prospecting Agent - Enhanced Calculation
- **New Input Fields:**
  - **Meetings or Demos Needed per Month** - Numeric input for expected monthly meetings/demos
    - Help text: "How many qualified meetings or demos do you expect your prospecting agent to book per month?"
  
  - **Expected Conversion Rate (%)** - Numeric input (1-100)
    - Help text: "What is your expected conversion rate from outreach to booked meetings? (e.g., 5%, 10%, 20%)"
    - Validation: Must be between 1 and 100

- **Auto-Calculated Result:**
  - Formula: `Contacts to Monitor = Meetings ÷ (Conversion Rate / 100)`
  - Example: 20 meetings at 5% conversion = 400 contacts
  - Displays: "➡️ You'll need to monitor approximately 400 contacts per month."
  - Auto-updates the Prospecting Agent input field with calculated value

#### 3. UI Enhancements
- **Always-visible help text** - No more hidden tooltips
- **Validation errors** - Soft validation messages for out-of-range values
- **Reset All Values button** - Added at bottom of "Estimate your month" section
- **Styled calculated results** - Highlighted in coral/orange theme color
- **Improved input grouping** - New fields have clear labels and help text

### 🔧 Technical Changes

#### CSS Updates
- Added `.help-text` class for visible help text
- Added `.calculated-result` for highlighted calculation displays
- Added `.prospecting-inputs` for grouped input styling
- Added `.input-group` for structured form fields
- Added `.validation-error` for error messages

#### JavaScript Updates
- Added `prospectingMeetings` and `prospectingConversionRate` to state
- New `updateProspectingCalculation()` function for dynamic calculation
- Updated `resetCalculator()` to reset new prospecting fields
- Updated `loadFromURL()` to restore prospecting values from shared links
- Enhanced `initializeUsageInputs()` with special rendering for Customer Agent and Prospecting Agent

### ✅ Acceptance Criteria Met
- [x] All help texts are always visible (no hover tooltips)
- [x] Prospecting Agent section includes new inputs + calculated contacts
- [x] Calculations update dynamically as user types
- [x] Layout, colors, and spacing remain consistent with current design
- [x] Conversion rate validation (1-100)
- [x] Reset Values button added
- [x] State preservation in URL sharing

### 🧪 Example Usage
1. Enter "20" in Meetings or Demos Needed
2. Enter "5" in Expected Conversion Rate (%)
3. See calculated result: "You'll need to monitor approximately 400 contacts per month"
4. Prospecting Agent input automatically updates to "400"
5. Credits calculation updates: 400 contacts × 100 credits = 40,000 credits

### 🎨 Design Consistency
- Maintains OneMetric.io dark/light theme
- Uses existing color palette (coral/orange primary)
- Follows same card layout patterns
- Preserves all accessibility features
- Responsive design intact
