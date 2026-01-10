# Google Analytics 4 Setup Guide

## 🎯 Get Your GA4 Measurement ID

### Step 1: Create Google Analytics Account

1. Go to [Google Analytics](https://analytics.google.com)
2. Sign in with your Google account
3. Click **"Start measuring"** or **"Admin"** (gear icon)

### Step 2: Create Property

1. Click **"Create Property"**
2. Fill in details:
   - **Property name:** "Maykol Medrano Website"
   - **Timezone:** Your timezone
   - **Currency:** USD (or your preference)
3. Click **"Next"**

### Step 3: Configure Business Details

1. **Industry:** Education / Research
2. **Business size:** Select appropriate size
3. **How you plan to use GA:** Research, Marketing
4. Click **"Create"**

### Step 4: Set Up Data Stream

1. Select **"Web"** platform
2. Enter website details:
   - **Website URL:** `https://maykolmedrano.github.io`
   - **Stream name:** "Main Website"
3. Click **"Create stream"**

### Step 5: Get Your Measurement ID

1. You'll see your **Measurement ID** in format: `G-XXXXXXXXX`
2. Copy this ID (looks like: `G-ABC123XYZ`)

### Step 6: Update _quarto.yml

Replace the placeholder in `_quarto.yml` line 16:

```yaml
# Before:
google-analytics: "G-XXXXXXXXXX"

# After:
google-analytics: "G-ABC123XYZ"  # Your actual ID
```

---

## 📊 Custom Events Already Configured

Your site will automatically track these events:

### User Engagement
- ✅ `theme_change` - When users toggle dark/light mode
- ✅ `scroll_depth` - At 25%, 50%, 75%, 100%
- ✅ `time_on_page` - Session duration per page

### Content Interaction
- ✅ `file_download` - CV download tracking
- ✅ `project_view` - Research project clicks
- ✅ `software_click` - Package link clicks (PyPI/GitHub)
- ✅ `badge_click` - Badge interactions

### External Engagement
- ✅ `social_click` - LinkedIn, GitHub, Twitter clicks
- ✅ `email_click` - Email contact tracking
- ✅ `search` - Internal site search usage

---

## 📈 Viewing Custom Events in GA4

### After 24-48 hours:

1. Go to **Reports** → **Engagement** → **Events**
2. You'll see all custom events listed
3. Click any event to see parameters (project_name, platform, etc.)

### Create Custom Reports:

1. Go to **Explore** → **Blank**
2. Add dimensions:
   - Event name
   - Event parameters (project_name, platform, theme_mode)
3. Add metrics:
   - Event count
   - Total users
4. Create visualizations

---

## 🎯 Recommended GA4 Setup

### Enable Enhanced Measurement

1. Go to **Admin** → **Data Streams** → Click your stream
2. Enable these automatic events:
   - ✅ Page views
   - ✅ Scrolls
   - ✅ Outbound clicks
   - ✅ Site search
   - ✅ File downloads

### Set Up Conversions

Mark these as conversions:

1. Go to **Configure** → **Events**
2. Mark as conversion:
   - `file_download` (CV downloads)
   - `software_click` (Package engagement)
   - `email_click` (Contact conversion)

### Create Audiences

**Engaged Researchers:**
- Users who: viewed projects AND downloaded CV
- Use for: Understanding research interest

**Package Users:**
- Users who: clicked PyPI or GitHub links
- Use for: Open source engagement

**Dark Mode Users:**
- Users with: theme_mode = dark
- Use for: UX preferences

---

## 🔍 Sample GA4 Queries

### Most Popular Projects
```
Events → project_view → Group by: project_name
```

### Software Package CTR
```
Events → software_click → Group by: platform (PyPI vs GitHub)
```

### Theme Preference
```
Events → theme_change → Group by: theme_mode
```

### Content Depth
```
Events → scroll_depth → Group by: percent_scrolled
```

---

## 🚀 Advanced: GA4 API Access (Optional)

If you want to pull analytics data programmatically:

1. Go to **Admin** → **Property Settings** → **API Access**
2. Enable **Google Analytics Data API**
3. Use Python client:
   ```python
   from google.analytics.data_v1beta import BetaAnalyticsDataClient
   # Query custom events programmatically
   ```

---

## ⚠️ Important Notes

- Custom events may take 24-48 hours to appear in GA4
- Real-time debugging: **Admin** → **DebugView** (requires Chrome extension)
- Keep your Measurement ID private (though it's client-side anyway)
- GA4 tracks pageviews automatically once configured

---

## ✅ Verification Checklist

After setup:

- [ ] GA4 Measurement ID added to `_quarto.yml`
- [ ] Site redeployed with new ID
- [ ] Visited your site and checked DebugView
- [ ] Confirmed pageviews appearing in real-time
- [ ] Custom events visible after 24-48 hours
- [ ] Conversions configured
- [ ] Custom reports created

---

## 🎉 You're All Set!

Once you add your GA4 Measurement ID, you'll have professional-grade analytics tracking:

- 📊 10+ custom events
- 🎯 Conversion tracking
- 👥 Audience segmentation
- 📈 Advanced reporting
- 🔍 Research impact metrics

---

## 📚 Additional Resources

- [GA4 Documentation](https://support.google.com/analytics/answer/10089681)
- [Custom Events Guide](https://support.google.com/analytics/answer/9267735)
- [GA4 for Researchers](https://analytics.google.com/analytics/academy/)

Need help? The GA4 setup is already complete in the code - you just need the ID!
