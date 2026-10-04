# Hospitals per District in India 🏥🗺️

An interactive 3D map showing the number of mapped hospitals in each of India's 735 districts, built with [Kepler.gl](https://kepler.gl).

**🔗 Live map:** 



## What it shows

- Each district is colored (and extruded in 3D) by the number of hospitals mapped inside it
- **Darker and taller = more hospitals**
- Hover over a district to see its name and hospital count
- Use the legend and the filter controls to explore the distribution

## Data sources

| Data | Source |
|------|--------|
| Hospital locations (~50,000 points) | [OpenStreetMap](https://www.openstreetmap.org) contributors, via [Overpass Turbo / Geofabrik / your method] |
| District boundaries (ADM2) | [geoBoundaries](https://www.geoboundaries.org) (simplified) |

Hospital data is available under the [Open Database License (ODbL)](https://www.openstreetmap.org/copyright).

## Method

1. Downloaded hospital locations for India from OpenStreetMap as GeoJSON
2. Downloaded district-level (ADM2) boundaries from geoBoundaries
3. Ran a spatial join to count hospitals within each district polygon
4. Visualized the joined layer in Kepler.gl with:
   - A sequential color scale (quantile) on the hospital count
   - 3D extrusion by the same field
   - Tooltips, legend, and a range filter to highlight districts with few hospitals
5. Exported as an interactive HTML map

## Important caveats

- **This shows *mapped* hospitals, not all hospitals.** OpenStreetMap coverage is uneven across regions, so some low counts reflect missing data rather than a real shortage of facilities.
- **Raw counts ignore population.** Populous districts naturally have more hospitals. A hospitals-per-100,000-people version would be a fairer comparison (see Roadmap).
- Hospital counts are based on the number of unique facility names in each district, so unnamed or duplicate-named facilities may be undercounted.
- District boundaries come from geoBoundaries and may differ slightly from official government boundaries.

## Files

- `index.html`: the interactive map (open in any modern browser; needs an internet connection for the basemap and Kepler.gl libraries)
- `README.md`: this file

## Run locally

Download `index.html` and open it in a browser. No build step or server needed.

## Roadmap

- [ ] Normalize by district population (hospitals per 100,000 people)
- [ ] Separate public and private facilities
- [ ] Add hospital bed capacity where available
- [ ] Highlight the bottom quintile of districts as potential "medical deserts"

## Credits

Built by Alavya Sharma with [Kepler.gl](https://kepler.gl), OpenStreetMap, and geoBoundaries.

## License

Map and code: [MIT / CC BY 4.0, choose one].
Underlying data: ODbL (OpenStreetMap) and the geoBoundaries license (CC BY 4.0 for most boundaries; check the dataset's page).
