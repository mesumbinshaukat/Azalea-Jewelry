# Multi-Step Custom Engagement Ring Form - Implementation Guide

## Overview
This document outlines the complete implementation for transforming the current single-step form into a pixel-perfect 4-step multi-step form matching the reference website.

## Architecture

### Step Flow
1. **Step 1**: Upload images/URL, description, metal color, ring size
2. **Step 2**: Diamond specifications (shape selector, carat slider, cut/color/clarity)
3. **Step 3**: Review all data with edit links, user info form (email, name, phone, etc.)
4. **Step 4**: Thank you message with continue shopping button

### Key Features
- **Async Progression**: JavaScript-based step navigation (no page reloads)
- **Data Persistence**: localStorage for maintaining form data across steps
- **Dynamic Updates**: Real-time price calculation based on carat selection
- **Validation**: Step-by-step validation before progression
- **Edit Functionality**: Jump back to any step from review page
- **Pixel-Perfect Styling**: Exact match to reference screenshots

## Styling Specifications

### Colors
- Main background: `#FFFFFF`
- Accent/links/notes: `#8B4513` (brown)
- Text: `#000000`
- Buttons: `#000000` background, `#FFFFFF` text
- Secondary text/notes: `#666666`
- Borders: `#CCCCCC`
- Dividers: `#E0E0E0`

### Metal Circle Colors
- 14K White: `#F5F5F5`
- 14K Yellow: `#FFD700`
- 14K Rose: `#FFC0CB`
- 18K White: `#FAFAFA` (brighter)
- 18K Yellow: `#FFE55C` (brighter)
- 18K Rose: `#FFD4E5` (brighter)
- Platinum: `#E5E5E5`

### Typography
- Font family: `system-ui, -apple-system, Arial, sans-serif`
- Headings: `28px` bold
- Section titles: `18px` bold
- Body text: `16px`
- Notes: `14px` italic, color `#666666`
- Breadcrumbs: `12px`, color `#808080`

### Layout
- Container max-width: `1100px`
- Top/bottom padding: `60px`
- Element spacing: `30px`
- Circle icons: `40px` diameter
- Icon border: `2px solid #CCCCCC`
- Selected border: `3px solid #8B4513`

### Responsive (@media max-width: 767px)
- Stack elements vertically
- Reduce font sizes by ~20%
- Full-width buttons
- Adjust spacing

## JavaScript Functionality

### Step Navigation
```javascript
- showStep(stepNumber): Hide all steps, show target step
- validateStep(stepNumber): Validate current step before progression
- nextStep(): Validate and move to next step
- previousStep(): Move to previous step
- goToStep(stepNumber): Jump to specific step (for edit links)
```

### Data Management
```javascript
- saveFormData(): Save all form data to localStorage
- loadFormData(): Load form data from localStorage
- getFormData(): Get current form data object
- populateReview(): Populate review section with all data
```

### Dynamic Features
```javascript
- updateDiamondPrice(carat): Calculate price = carat * 1158
- updateDiamondDisplay(shape, carat): Update image and text
- handleShapeSelection(): Update selected shape
- handleCaratSelection(): Update carat and price
```

### File Upload
```javascript
- handleFileUpload(): Preview images (max 2 files, <5MB, jpg/png/webp)
- createImagePreview(): Show thumbnail with "View 1"/"View 2" labels
```

### Form Submission
```javascript
- submitForm(): POST to /contact with all data
- On success: Show Step 4 (thank you)
- Optional: Add to cart via AJAX Cart API
```

## Schema Settings

### Additional Settings Needed
```json
{
  "diamond_shapes": [
    {"name": "Round", "image": "..."},
    {"name": "Oval", "image": "..."},
    {"name": "Cushion", "image": "..."},
    {"name": "Emerald", "image": "..."},
    {"name": "Pear", "image": "..."},
    {"name": "Radiant", "image": "..."},
    {"name": "Asscher", "image": "..."},
    {"name": "Marquise", "image": "..."},
    {"name": "Heart", "image": "..."},
    {"name": "Princess", "image": "..."}
  ],
  "cut_options": ["Excellent", "Very Good", "Good", "Fair"],
  "color_options": ["D", "E", "F", "G", "H", "I", "J"],
  "clarity_options": ["FL", "IF", "VVS1", "VVS2", "VS1", "VS2", "SI1", "SI2", "I1"],
  "reason_options": ["Engagement", "Anniversary", "Birthday", "Other"]
}
```

## Implementation Steps

1. **Backup existing file**
2. **Update CSS**: Add multi-step styles, step visibility, new components
3. **Update HTML**: Wrap sections in step divs, add Step 2/3/4 markup
4. **Update JavaScript**: Add step navigation, validation, data persistence
5. **Update Schema**: Add diamond shapes, options, Step 2/3/4 settings
6. **Test**: Verify all steps, validation, data flow, submission

## File Structure

```
ai_gen_block_f911224.liquid
├── {% doc %} - Documentation
├── {% style %} - All CSS (500+ lines)
│   ├── Base styles
│   ├── Step 1 styles
│   ├── Step 2 styles (diamond selector)
│   ├── Step 3 styles (review)
│   ├── Step 4 styles (thank you)
│   └── Responsive styles
├── <custom-engagement-form> - HTML markup
│   ├── Breadcrumb
│   ├── Step 1: Upload & Basic Info
│   ├── Step 2: Diamond Specifications
│   ├── Step 3: Review & User Info
│   └── Step 4: Thank You
├── <script> - JavaScript (800+ lines)
│   ├── Class definition
│   ├── Step navigation
│   ├── Data management
│   ├── Validation
│   ├── Dynamic updates
│   └── Form submission
└── {% schema %} - Settings (200+ lines)
    ├── Step 1 settings
    ├── Step 2 settings
    ├── Step 3 settings
    └── Step 4 settings
```

## Total File Size Estimate
- CSS: ~600 lines
- HTML: ~800 lines
- JavaScript: ~900 lines
- Schema: ~250 lines
- **Total: ~2550 lines**

## Next Steps
Due to the file size limitations, the implementation will be done in phases:
1. Create complete CSS with all step styles
2. Update HTML with multi-step structure
3. Implement JavaScript for step navigation and features
4. Update schema with all settings

The file is too large to generate in a single response, so I'll create it section by section using targeted edits.
