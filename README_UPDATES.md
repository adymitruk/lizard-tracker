# Common Wall Lizard Tracker - Update Summary

## Date: April 26, 2026

## Changes Made

### 1. Manual Sighting Entry Dialog
Added a modal dialog that allows users to manually enter wall lizard sighting coordinates:

**Features:**
- Input fields for:
  - Latitude (with current map center pre-filled)
  - Longitude (with current map center pre-filled)
  - Date (defaults to today)
  - Location/Notes text area
  - Optional photo URL
- Submit button to add sighting to map
- Cancel button and click-outside-to-close functionality
- Success confirmation alert on save

### 2. Default Sighting Data
Added pre-populated wall lizard sighting data based on BC research (Engelstoft 2020 paper). These are established populations **NOT** on iNaturalist:

**Locations Added:**
1. **Powell River** - Established population (June 2015)
   - Lat: 49.8333, Lng: -123.1167
   - First confirmed mainland population
   
2. **Delta** - Established population (July 2015)
   - Lat: 49.0847, Lng: -123.0428
   - First confirmed mainland population
   
3. **Vedder Crossing/Chilliwack** - Established population (August 2015)
   - Lat: 49.1575, Lng: -121.8842
   - First confirmed mainland population
   
4. **Saanich Peninsula (Historical)** - Original introduction area (May 2020)
   - Lat: 48.4284, Lng: -123.4572
   - Site of 1967-1970 releases
   
5. **Sidney, Vancouver Island** - Recent sighting (June 2022)
   - Lat: 48.5518, Lng: -123.3472

### 3. Toggle Checkbox
Added "Show Default Sightings" checkbox in the header that:
- Defaults to **ON** (checked)
- Allows users to hide/show the pre-loaded data
- Updates the map and list in real-time when toggled
- Marked with "(Default Data)" label in the sidebar

### 4. README Section
Added a comprehensive README section in the sidebar explaining:

**How This App Works:**
- Data source: iNaturalist API (taxon_id: 55990)
- Default sightings include historical BC research records
- Toggle functionality instructions
- Manual entry instructions
- Search and navigation features

**Default Sightings Data:**
- Lists the three mainland established populations
- References the Engelstoft et al. 2020 research source

## Technical Implementation

### New Variables
- `manualSightings[]` - Array to store user-added sightings
- `DEFAULT_SIGHTINGS[]` - Array with 5 pre-loaded research-based sightings

### New Functions
- `renderMarkers()` - Updated to handle multiple data sources
- `renderList()` - Updated to display combined data
- Event listeners for:
  - Checkbox toggle
  - Manual sighting form submission
  - Modal open/close/cancel

### CSS Classes Added
- `.modal` - Dialog background overlay
- `.modal-content` - Dialog content container
- `.readme-section` - README styling
- `.sighting-toggle` - Checkbox container styling

## Usage Instructions

### For End Users:
1. **View Default Sightings**: The map loads with 5 pre-populated research-based sightings
2. **Toggle Default Sightings**: Uncheck "Show Default Sightings" to see only iNaturalist data
3. **Add New Sighting**: Click "+ Add Sighting" button, enter coordinates and details
4. **Search**: Enter a Vancouver postal code to center the map
5. **Explore**: Click markers or sidebar items to view photo and details

### For Developers:
- Manual sightings are stored in browser memory (session only)
- Default sightings are hardcoded in the script
- To persist manual sightings, integrate with localStorage or backend
- Default sightings marked with `isDefault: true` flag

## Data Sources

### iNaturalist API
- Endpoint: `https://api.inaturalist.org/v1/observations`
- Taxon ID: 55990 (Common Wall Lizard - Podarcis muralis)
- Returns recent observations (last 4 years) within 50km radius

### BC Research Data (Engelstoft et al. 2020)
- Published in *Northwestern Naturalist*
- PDF: https://bcreptilesandamphibians.ca/wp-content/uploads/2024/03/engelstoft-2020.pdf
- Documents rapid range expansion of Common Wall Lizards in BC
- Confirms three mainland established populations in 2015

### Additional Resources
- BC Reptiles & Amphibians: https://bcreptilesandamphibians.ca/common-wall-lizard/
- Invasive Species Council BC: https://bcinvasives.ca/invasives/european-wall-lizard/
- Report Invasives BC App: Available on iOS/Android

## Future Enhancements

### Potential Additions:
- [ ] LocalStorage persistence for manual sightings
- [ ] Backend database integration
- [ ] Export sightings to CSV/KML
- [ ] Photo upload support (instead of URL only)
- [ ] Edit/delete existing manual sightings
- [ ] Export default sightings for offline use
- [ ] Comparison view (iNaturalist vs. other databases)
- [ ] Alert notifications for new research data

### Integration Opportunities:
- Connect with iNaturalist API for one-click sharing
- Export to Report Invasives BC app format
- Sync with BC Conservation Data Centre
- Integration with E-Fauna BC database

---

**File Modified:** `/home/adam/repos/public/lizard-tracker/index.html`
**Last Updated:** April 26, 2026
