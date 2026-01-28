# Daylight Tools

Internal tools for Daylight solar partner operations.

## 🚀 Live Site

Once deployed, your site will be at: `https://YOUR-USERNAME.github.io/daylight-tools/`

## 📁 Tools Included

| Tool | Description |
|------|-------------|
| **Escalator Calculator** | 25-year payment projections with annual escalation rates |
| **Partner Intake Form** | Collect new partner information with local database |
| **Partner Tiers Directory** | View partners organized by tier and business type |
| **Network Qualifier** | Check if MA towns are in the Sunday Energy service area |
| **SVG to PNG Converter** | Batch convert SVG files with custom colors/dimensions |
| **MA Grid Reliability** | Live outage data from MEMA + solar sales content |

## ⚡ Live Outage Data

The Grid Reliability dashboard pulls real data from MEMA (Massachusetts Emergency Management Agency). A GitHub Action runs every 15 minutes to fetch fresh data.

### How it works:
1. GitHub Action runs every 15 minutes
2. Fetches CSV from `mema.mapsonline.net/power_outage_public.csv`
3. Saves to `data/outages.csv`
4. Page reads from local file (no CORS issues!)

### First-time setup for live data:

After you push the repo to GitHub:

1. Go to your repo on GitHub
2. Click **Settings** → **Actions** → **General**
3. Under "Workflow permissions", select **Read and write permissions**
4. Click **Save**
5. Go to **Actions** tab
6. Click on "Fetch MEMA Outage Data" workflow
7. Click **Run workflow** to trigger the first data fetch

The data will auto-update every 15 minutes after that!

## 🛠️ Deployment Instructions

### Step 1: Create GitHub Repository

1. Go to [github.com](https://github.com) and sign in
2. Click the **+** icon → **New repository**
3. Name it `daylight-tools`
4. Select **Public**
5. Click **Create repository**

### Step 2: Upload Files

1. On your new repo page, click **"uploading an existing file"**
2. Drag and drop ALL contents of this folder (including `.github` folder)
3. Click **Commit changes**

### Step 3: Enable GitHub Pages

1. Go to **Settings** → **Pages**
2. Under "Build and deployment":
   - Source: **Deploy from a branch**
   - Branch: **main** / **/ (root)**
3. Click **Save**
4. Wait 1-2 minutes for deployment

### Step 4: Enable Workflow Permissions

1. Go to **Settings** → **Actions** → **General**
2. Scroll to "Workflow permissions"
3. Select **Read and write permissions**
4. Click **Save**

### Step 5: Trigger First Data Fetch

1. Go to **Actions** tab
2. Click **Fetch MEMA Outage Data**
3. Click **Run workflow** → **Run workflow**

Your site is now live with auto-updating outage data! 🎉

## 📊 Data Sources

- **Outage data**: [MEMA](https://mema.mapsonline.net/public.html) (updates every 15 min)
- **Grid statistics**: [U.S. Energy Information Administration](https://www.eia.gov/todayinenergy/detail.php?id=66744)
- **MA utility info**: [Mass.gov](https://www.mass.gov/info-details/power-outages)

## 🎨 Customization

### Brand Colors (in CSS variables)
```css
--daylight-orange: #FF6B35;
--daylight-cream: #FFF8F0;
--daylight-cream-dark: #F5EDE3;
--daylight-black: #1A1A1A;
```

### Adding Partners to Tiers Directory
Edit `tools/partner-tiers.html` and add entries to the `partners` array:
```javascript
const partners = [
  { 
    name: "John Smith", 
    company: "Solar Co", 
    email: "john@solar.com", 
    phone: "(555) 123-4567", 
    projects: 45,      // Determines tier automatically
    size: "51-200", 
    crews: 5, 
    type: "EPC"        // "EPC", "EPC with Inside Sales", or "Sales Org"
  },
];
```

## 📝 License

Internal use only - Daylight Energy

---

Built with ☀️ for [Daylight](https://godaylight.com)
