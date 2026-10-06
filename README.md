# AquaWatch India

**Mapping Water Stress. Protecting Tomorrow.**

*Digital Mapping of Water Scarcity Hotspots in Indian Cities* — a CHE110 project at Lovely Professional University.

AquaWatch India is an interactive website that explores groundwater stress, rainfall patterns and urban water challenges across nine Indian cities: Delhi, Bengaluru, Chennai, Jaipur, Hyderabad, Ahmedabad, Mumbai, Kolkata and Ludhiana.

## Features

- **3D hero globe:** drag to rotate, hover over India to highlight it, and watch the camera move as you scroll.
- **3D India water-stress map:** four indicators, five toggleable layers, region and category filters, and a city panel.
- **City intelligence profiles:** groundwater and rainfall charts, pressures, interventions and sources for each city.
- **3D groundwater cutaway:** six-stage animation with extraction and recharge sliders, showing the water table and the cone of depression.
- **Solutions section:** a rainwater-harvesting calculator (V = A × R × C ÷ 1000) and a hypothetical city scenario tool.
- **City comparison:** a side-by-side table with overlaid charts, and no invented ranking.
- **Learning modules:** six CHE110 topics with expandable explanations and quizzes.
- **Methodology page:** a full source register.
- **Quality floor:** responsive layout, reduced-motion support, and fallbacks when WebGL is unavailable.

## Tech

It is a single static page (`index.html`) with no build step. Libraries load from CDNs:

| Library | Version | Used for |
|---|---|---|
| Three.js | r128 (+ OrbitControls) | 3D globe, map, cutaway |
| GSAP + ScrollTrigger | 3.12.5 | Intro and scroll animation |
| Chart.js | 4.4.1 | Charts |
| Google Fonts | Bricolage Grotesque, Figtree | Typography |

> An internet connection is needed for the CDN libraries and fonts.

## Run locally

Option 1 is to double-click `index.html`.

Option 2 is to run a local server, which is recommended:

```bash
# Python
python -m http.server 8000
# or Node
npx serve .
```

Then open http://localhost:8000.

## Upload to GitHub

1. Create a new repository on GitHub, for example `aquawatch-india`.
2. Click **Add file → Upload files**.
3. Drag in **the contents** of this folder: `index.html`, `README.md`, `assets/`, `vercel.json`, `.nojekyll`, `.gitignore`.
4. Commit.

Or use Git:

```bash
cd aquawatch-india
git init
git add .
git commit -m "AquaWatch India: initial site"
git branch -M main
git remote add origin https://github.com/<your-username>/aquawatch-india.git
git push -u origin main
```

## Deploy

**GitHub Pages:** go to the repo's **Settings → Pages**. Under Source, choose **Deploy from a branch**, then select `main` and `/ (root)`, and click Save. The site goes live at `https://<your-username>.github.io/aquawatch-india/` after a minute or two.

**Vercel:** go to vercel.com and choose **Add New → Project**. Import the GitHub repo. Set Framework Preset to **Other** and leave the build command empty. Click Deploy.

## Data — please read

City-level values marked **DEMO** on the site are demonstration data for the prototype. This covers groundwater categories, depth-to-water series, rainfall series and demand–supply shortfalls. They are **not official figures**.

Some figures are real and cited:
- The 18% world population and 4% freshwater shares come from NITI Aayog, Composite Water Management Index, 2018.
- The 135 L/person/day urban supply benchmark comes from the CPHEEO Manual.

To replace the demo data, find the `CITIES` array in the `<script>` block of `index.html`. Each city has these fields:

| Field | Meaning |
|---|---|
| `cat` | Groundwater category: Safe / Semi-critical / Critical / Over-exploited |
| `gwBase`, `gwSlope` | Generate the demo depth-to-water series; replace with a real `gw` array of 10 values, 2015–2024, in m bgl |
| `rainN` | Annual rainfall normal in mm |
| `gap` | Demand shortfall in %, or `null` for "Data unavailable" |
| `quality` | Water-quality note |

Official sources:
- Central Ground Water Board — https://cgwb.gov.in/
- INGRES (groundwater resource assessment) — https://ingres.iith.ac.in/
- India Meteorological Department — https://mausam.imd.gov.in/
- India-WRIS — https://indiawris.gov.in/

Official groundwater categories are issued per **assessment unit** (block, mandal or taluk), not per city.

## Limitations

- The India outline is a simplified schematic, not a survey boundary.
- The groundwater cutaway is an educational simulation, not a calibrated hydrological model.
- Scenario outputs are hypothetical, not forecasts.

---

Built for CHE110 (Environmental Studies), Lovely Professional University.
