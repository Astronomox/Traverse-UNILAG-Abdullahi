# Traverse : UNILAG Campus Wayfinder

A monochrome campus navigation app for the University of Lagos, Akoka. Pick a start point and a destination from on-campus locations and get a real road route with turn-by-turn directions, total distance, and estimated walk time.

Built for the NITHUB Software Engineering Training programme.

---

## Features

- Real road routing via Leaflet Routing Machine and OSRM
- Turn-by-turn walking directions with distances
- Live geocoding from OpenStreetMap bounded to the UNILAG area
- Monochrome design, strictly black and white
- Custom university-inspired map marker
- Animated 3D node network on the landing page (Three.js r185, WebGL)
- Collapsible hamburger navigation on mobile
- Graph data structure underneath: adjacency matrix, BFS, and DFS implementations
- Easter egg in the browser console

---

## Stack

| Layer | Tech |
|---|---|
| Map | Leaflet 1.9.4 |
| Routing | Leaflet Routing Machine + OSRM |
| Tiles | CARTO Light (monochrome filtered) |
| 3D hero | Three.js r185 (WebGL) |
| Fonts | Archivo (Google Fonts) |
| Hosting | Netlify / GitHub Pages |

No build step. Single HTML file.

---

## Run locally

```bash
# clone
git clone https://github.com/Astronomox/Traverse-UNILAG-Abdullahi.git
cd Traverse-UNILAG-Abdullahi

# serve (pick any)
python -m http.server 8000
# or
npx serve
```

Open `http://localhost:8000`. An internet connection is required for map tiles and routing.

---

## Adding or correcting campus locations

Open `index.html` and find the `PLACES` array near the top of the script block. Each entry is:

```js
{ name:"Location Name", lat:6.5XXX, lng:3.3XXX }
```

Coordinates snap to the nearest road via OSRM, but accuracy improves with exact values. Get them by right-clicking any point on Google Maps and copying the coordinates.

---

## Graph implementation

The campus locations form an undirected weighted graph. The app implements:

- **Adjacency matrix** : N×N matrix where `matrix[i][j]` holds the haversine distance between connected nodes
- **BFS** : breadth-first search via a queue, guarantees fewest-stop path
- **DFS** : depth-first search via recursion

These run under the hood to power the route comparison logic.

---

## Built by

[Oriola Abdullahi Adeola](https://abdullahioriola.vercel.app/) for NITHUB Software Engineering Training
