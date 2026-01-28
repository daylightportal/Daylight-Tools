# Daylight Tools

Internal tools for Daylight solar partner operations.

## Tools Included

| Tool | Description |
|------|-------------|
| **Escalator Calculator** | 25-year payment projections with annual escalation rates |
| **Partner Intake Form** | Collect new partner information with local database |
| **Partner Tiers Directory** | View partners organized by tier and business type |
| **Network Qualifier** | Check if MA towns are in the Sunday Energy service area |
| **SVG to PNG Converter** | Batch convert SVG files with custom colors/dimensions |
| **MA Grid Reliability** | Live outage data from MEMA + solar sales content |

## Live Outage Data

The Grid Reliability dashboard pulls real data from MEMA (Massachusetts Emergency Management Agency). A GitHub Action runs every 15 minutes to fetch fresh data.

### How it works:
1. GitHub Action runs every 15 minutes
2. Fetches CSV from `mema.mapsonline.net/power_outage_public.csv`
3. Saves to `data/outages.csv`
4. Page reads from local file (no CORS issues!)

## Data Sources

- **Outage data**: [MEMA](https://mema.mapsonline.net/public.html) (updates every 15 min)
- **Grid statistics**: [U.S. Energy Information Administration](https://www.eia.gov/todayinenergy/detail.php?id=66744)
- **MA utility info**: [Mass.gov](https://www.mass.gov/info-details/power-outages)

## Customization

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

## License

Internal use only - Daylight Energy

---

Built with ☀️ for [Daylight](https://godaylight.com)
