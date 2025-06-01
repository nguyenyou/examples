# Text Truncation Demo Examples

This repository contains comprehensive examples of text truncation techniques across different CSS layout scenarios. The demos show how `text-overflow: ellipsis` works in various real-world situations.

## 📁 Files

- `truncate.html` - Complete interactive demo with 5 different scenarios
- `index.html` - Main landing page

## 🎯 Text Truncation Scenarios

### 1. Fixed Width Container (Resizable)
**Use Case:** Classic scenario where you have a fixed-width container that needs to display potentially long content.

**CSS Approach:**
```css
.container {
  width: 300px; /* Fixed width */
}

.text-truncate {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```

**Real-world Examples:**
- Sidebar navigation items
- Card titles with fixed dimensions
- Modal headers with character limits

---

### 2. Auto Width with Max Width
**Use Case:** Flexible containers that can grow up to a certain point, then truncate.

**CSS Approach:**
```css
.container {
  width: auto;
  max-width: 400px;
}

.text-truncate {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```

**Real-world Examples:**
- Responsive breadcrumbs
- Tag labels that shouldn't exceed certain widths
- Notification messages
- Chat bubbles with max width constraints

---

### 3. Flexbox Layout
**Use Case:** When text is inside flex containers with different flex behaviors.

**CSS Approach:**
```css
.flex-container {
  display: flex;
  gap: 15px;
}

.flex-item {
  min-width: 0; /* Critical for truncation to work! */
}

/* Different flex behaviors */
.flex-fixed { flex: 0 0 120px; }      /* Fixed width */
.flex-grow { flex: 1; }               /* Grows to fill space */
.flex-shrink { flex: 0 1 200px; }     /* Can shrink below base width */
```

**Key Point:** `min-width: 0` is essential on flex items to allow them to shrink below their content size.

**Real-world Examples:**
- Navigation bars with flexible menu items
- Dashboard cards in flexible layouts
- Toolbar buttons with text labels
- Multi-column layouts with text content

---

### 4. CSS Grid Layout
**Use Case:** Grid layouts where some columns are fixed and others are flexible.

**CSS Approach:**
```css
.grid-container {
  display: grid;
  grid-template-columns: 150px 1fr 100px; /* fixed, flexible, fixed */
  gap: 15px;
}

.grid-item {
  min-width: 0; /* Critical for grid items too! */
}
```

**Key Point:** Like flexbox, `min-width: 0` is necessary on grid items for truncation to work properly.

**Real-world Examples:**
- Data tables with mixed column types
- Email client layouts (sender, subject, date)
- File managers (icon, name, size, date)
- Product listings with structured data

---

### 5. Table Layout
**Use Case:** Traditional HTML tables where certain columns need to truncate.

**CSS Approach:**
```css
.demo-table {
  table-layout: fixed; /* Optional but recommended */
  width: 100%;
}

.truncate-column {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  max-width: 0; /* Special trick for table cells! */
}
```

**Key Point:** `max-width: 0` is the special technique needed for table cell truncation to work.

**Real-world Examples:**
- User management tables (long email addresses)
- File path displays in admin panels
- Log viewers with long messages
- Data tables with description columns

## 🔧 Technical Implementation Details

### Essential CSS Properties for Text Truncation
```css
.text-truncate {
  overflow: hidden;        /* Hide overflowing content */
  white-space: nowrap;     /* Prevent line wrapping */
  text-overflow: ellipsis; /* Show ellipsis (...) */
}
```

### Critical Layout-Specific Requirements

| Layout Type | Required CSS | Why It's Needed |
|-------------|--------------|-----------------|
| **Fixed Width** | `width: XXXpx` | Sets the truncation boundary |
| **Auto/Max Width** | `max-width: XXXpx` | Defines the maximum width before truncation |
| **Flexbox** | `min-width: 0` on flex items | Allows flex items to shrink below content width |
| **CSS Grid** | `min-width: 0` on grid items | Allows grid items to shrink below content width |
| **Table** | `max-width: 0` on table cells | Special technique for table cell truncation |

### Common Pitfalls and Solutions

1. **Flexbox/Grid not truncating:** Add `min-width: 0` to the flex/grid items
2. **Table cells not truncating:** Use `max-width: 0` instead of `width`
3. **Nested containers:** Ensure all parent containers allow the child to shrink
4. **Text still wrapping:** Check for `white-space: nowrap` and ensure no conflicting CSS

## 🚀 Interactive Demo Features

- **Resizable container** in Scenario 1 to see real-time truncation
- **Multiple text samples** including URLs, file paths, emails, and long sentences
- **Responsive design** that works on mobile devices
- **Visual CSS explanations** for each scenario
- **Color-coded sections** for easy navigation

## 📱 Mobile Considerations

The demo includes responsive design that:
- Stacks flex containers vertically on mobile
- Converts grid layouts to single columns
- Maintains touch-friendly resize handles
- Ensures readability on small screens

## 🎨 Styling Tips

- Use consistent padding and margins for visual hierarchy
- Add visual indicators (borders, colors) to distinguish different scenarios
- Include hover states for interactive elements
- Consider accessibility with proper contrast ratios

## Development

```sh
bun ./**/*.html
```

Open `truncate.html` in your browser to see all scenarios in action!

## 🔗 Use Cases by Industry

- **E-commerce:** Product names, descriptions, user reviews
- **Social Media:** Post content, usernames, hashtags
- **Enterprise Software:** File paths, user emails, log messages
- **Mobile Apps:** Navigation items, card content, list items
- **Data Dashboards:** Metric names, descriptions, category labels
