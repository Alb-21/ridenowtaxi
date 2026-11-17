# 🚖 RideNow — Smart Taxi Booking System

RideNow is a **frontend-only college project prototype** of a taxi booking app. Pick a pickup and destination on a map, see an estimated fare, and watch a demo driver move toward you in real time.

> ⚠️ **This is a demo.** There is no backend, no real accounts, no real payments, and no real drivers. All fares are demonstration values.

---

## ✨ Features

- **Map booking** — choose places from a preset list, click anywhere on an OpenStreetMap map, or use your device location.
- **Fare estimate** — base fare plus a per-kilometre rate (demo values: ₹50 + ₹15/km).
- **Demo live GPS** — a simulated driver moves smoothly to the pickup and then to the destination.
- **Optional real GPS** — the driver view can use the device's real location (only after you click and confirm).
- **Two dashboards** — Customer and Driver views stay in sync, even across tabs in the same browser.
- **Live tracking view** — follow the active ride on the map.
- **Ride status flow** — `PENDING → ACCEPTED → ARRIVED → IN_PROGRESS → COMPLETED` (cancellation allowed before the ride starts).
- **Accessible & responsive** — works on desktop and mobile, with focus outlines and ARIA labels on maps.

## 🔄 How It Works

1. **Customer** picks pickup and destination, then books a taxi.
2. **Driver** goes online and accepts the request.
3. Driver starts **Demo GPS**; the customer sees the taxi approach on the map.
4. Driver marks **arrived**, **starts**, and **completes** the ride.

## 🛠️ Tech Stack

| Area | Technology |
|------|------------|
| Markup / Styling | HTML5, CSS3 (no frameworks) |
| Logic | Vanilla JavaScript (ES6+) |
| Maps | [Leaflet](https://leafletjs.com/) 1.9.4 |
| Map data | [OpenStreetMap](https://www.openstreetmap.org/) tiles |
| Storage | Browser `localStorage` |

## 🚀 Getting Started

No installation or build step is required.

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/<your-repo>.git

# 2. Open the project folder
cd <your-repo>

# 3. Open the app in your browser
#    Double-click index.html, or serve it locally:
python -m http.server 8000
# then visit http://localhost:8000
```

> An **internet connection is required** to load Leaflet and the map tiles.
> Rename the HTML file to `index.html` if it has a different name.

### Host on GitHub Pages

1. Push the project to GitHub.
2. Go to **Settings → Pages**.
3. Under **Source**, choose the `main` branch and the `/ (root)` folder.
4. Save — your app will be live at `https://<your-username>.github.io/<your-repo>/`.

## 🧪 Try the Demo

1. Open the **Customer** view, choose a pickup and destination (e.g. *Ernakulam Junction → Lulu Mall*), and click **Book taxi**.
2. Open the **Driver** view, toggle **Online**, and **Accept** the request.
3. Click **Start Demo GPS** and watch the taxi move.
4. Click **Mark arrived → Start ride → Complete ride**.
5. Open **Live tracking** to follow the ride, or use **Reset demo** in the navbar to clear all data.

💡 Tip: open the Customer and Driver views in two tabs of the same browser to see them sync.

## 📍 Preset Locations (Kochi, India)

Ernakulam Junction · Marine Drive · Lulu Mall · Fort Kochi · Infopark · Kochi Airport

## ⚙️ Configuration

Demo settings live in the `CONFIG` object at the top of the script:

```js
const CONFIG = {
  baseFare: 50,      // demo base fare (₹)
  perKm: 15,         // demo rate per km (₹)
  center: [9.9312, 76.2673],       // default map centre
  driverStart: [9.9816, 76.2999],  // demo driver start point
  tickMs: 1000,      // demo GPS update interval
  stepKm: 0.08,      // distance moved per tick (80 m)
  key: 'ridenow_v1'  // localStorage key
};
```

## ⚠️ Limitations

- **Frontend only** — data is stored in `localStorage`, so it works **in one browser only**. Cross-device tracking would need a backend.
- **No authentication** — roles (customer/driver) are chosen, not logged in. The demo profiles are fictional.
- **Straight-line distance** — distance uses the Haversine formula, not real road routing, so fares are approximate.
- **Demo fares** — rates are for demonstration, not real prices.
- **Ride-state rules** are checked in the frontend only; a real system must enforce them on a server.

## 🔒 Privacy

- Real GPS is used **only after you click** and confirm the prompt.
- Location data stays in your browser and is **never sent anywhere**.
- Use **Reset demo** to delete all stored bookings and driver data.

## 🔮 Future Improvements

- Backend with a database and real-time updates (WebSockets / Firebase)
- User authentication and separate customer/driver accounts
- Road routing and ETA (e.g. OSRM or Google Directions)
- Payments integration
- Ride ratings and trip receipts

## 🙏 Acknowledgements

- Map data ©️ [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors
- Maps powered by [Leaflet](https://leafletjs.com/)

## 📄 License

This project is for educational purposes. Add a license of your choice (e.g. [MIT](https://choosealicense.com/licenses/mit/)) before sharing publicly.

---

Made with ❤️ as a college project.
