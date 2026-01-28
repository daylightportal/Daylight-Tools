# Daylight Tools

Internal tools for Daylight solar partner operations.

## Tools Included

| Tool | Description |
|------|-------------|
| **Escalator Calculator** | 25-year payment projections with annual escalation rates |
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
--daylight-orange: #F66F00;
--daylight-cream: #FFF7E9;
--daylight-cream-dark: #F3EAD9;
--daylight-black: #232220;
```

## License

Internal use only - Daylight Energy

---

Built with ☀️ for [Daylight](https://godaylight.com)
