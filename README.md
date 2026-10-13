[Uploading README.md…]()
<div align="center">

# SRIT Crowd Management System

**Know how full every part of campus is, as it happens.**

Count people in and out of each zone, watch crowd levels live, and get an alert before an area gets too full.

![Single file](https://img.shields.io/badge/single-HTML%20file-2149c9?style=for-the-badge)
![No dependencies](https://img.shields.io/badge/dependencies-none-15906a?style=for-the-badge)
![Works offline](https://img.shields.io/badge/works-offline-c97a00?style=for-the-badge)
![Dark mode](https://img.shields.io/badge/dark%20mode-supported-0b1f3a?style=for-the-badge)

🟢🟢🟢🟢🟢🟢🟢🟢🟢🟢🟢🟢🟡🟡🟡🟡🔴🔴⚪⚪⚪⚪⚪⚪

</div>

---

## Why this exists

Gates, canteens, libraries and auditoriums fill up fast, and staff usually find out when it is already too late. This dashboard gives security teams a quick way to count entries, and gives everyone else a clear picture of how busy each zone is right now.

It is one HTML file. Open it in a browser and it works. There is nothing to install, build or host.

## Highlights

| | |
|---|---|
| **Crowd field** | The dashboard opens with 100 dots, each worth 1% of total campus capacity, colored Low, Medium or High. Tick marks show where your alert levels start. |
| **Live counter** | Big +1, −1, +10 and −10 buttons for each zone, built for a phone held at a gate. Every tap is time-stamped. |
| **Instant alerts** | When a zone reaches the High level, a banner appears, an optional beep sounds, and the alert is logged with the time. |
| **Analytics** | Peak count per hour for any zone, entries per day for the last 7 days, and a whole-campus occupancy heatmap. |
| **Reports** | A daily report you can print or save as PDF, plus CSV downloads of the report and the full event log. |
| **Live data feed** | Point it at a sensor or counter API and zone counts update by themselves every 10 seconds. |
| **Three access levels** | Admin, security staff and a no-login public view, each seeing only what they need. |
| **Light and dark themes** | One tap to switch. Keyboard focus and reduced-motion settings are respected. |

## Quick start

1. Download `SRIT_Crowd_Management_System.html`.
2. Open it in any modern browser.
3. Sign in with the first-use accounts below, or choose **View as public (no login)**.
4. Open **Settings → Load demo data** to see the charts filled in.

| Role | Username | Password |
|---|---|---|
| Administrator | `admin` | `srit@2026` |
| Security staff | `security` | `gate@2026` |

> Change both passwords in **Settings → User passwords** before real use.

### Put it on a shared screen or the campus network

Any static host works: GitHub Pages, Netlify, an internal web server, or a folder served with `python -m http.server`. Use the same address on every device so they share one data store.

## Who sees what

| Tab | Admin | Security | Public |
|---|:-:|:-:|:-:|
| Dashboard | ✅ | ✅ | ✅ |
| Counter | ✅ | ✅ | |
| Analytics | ✅ | ✅ | |
| Reports | ✅ | | |
| Campus Map | ✅ | ✅ | ✅ |
| Settings | ✅ | | |

## Default zones

Edit, rename, delete or add zones in **Settings**. These are the starting set:

| Zone | Capacity |
|---|---:|
| Main Gate | 600 |
| Canteen / Food Court | 450 |
| Library | 300 |
| Academic Block A | 900 |
| Academic Block B | 800 |
| Auditorium | 1,200 |
| Sports Ground | 500 |
| Hostel Entrance | 400 |

Crowd levels default to **Medium from 60%** and **High from 85%**. Both are adjustable.

## Connect a live data source

Instead of tapping counts by hand, you can feed the dashboard from a people-counter, camera system or your own server.

1. Open **Settings → Alert thresholds & options**.
2. Paste your endpoint into **Live data API URL**.
3. Select **Save settings**.

The endpoint must return JSON in this shape and allow CORS:

```json
[
  { "zone": "Library", "count": 123 },
  { "zone": "Main Gate", "count": 340 }
]
```

Zone names are matched without regard to upper or lower case. The dashboard polls the endpoint every 10 seconds and shows the time of the last successful update.

## Import, export and backup

| Task | Where |
|---|---|
| Download today's report | Reports → Download report CSV |
| Download every entry and exit | Reports → Download full event log |
| Print or save as PDF | Reports → Print / Save PDF |
| Back up everything | Settings → Backup (JSON) |
| Restore a backup | Settings → Restore backup |
| Set counts from a spreadsheet | Settings → Import CSV, with rows like `Library,120` |

## How your data is stored

All data stays **in your browser** (`localStorage`, key `sritcm`). Nothing is sent anywhere unless you set a live API URL.

- Open tabs on the same browser stay in sync every 5 seconds.
- Different devices do **not** share data with each other. For a single shared view, use the live API option or run the dashboard on one shared screen.
- The log keeps the most recent entries and trims older ones automatically.
- Use **Backup (JSON)** regularly. Clearing browser data erases the dashboard's data.

## Customize

Everything is in the one file.

| Change | Where |
|---|---|
| Starting zones and capacities | `def()` near the top of the script |
| Campus map address | `MAP_URL` constant near the top of the script |
| Brand colors | CSS variables at the top of the `<style>` block (`--ac`, `--ink`, `--ink2`) |
| Logo | The `i-logo` symbol in the SVG sprite at the start of `<body>` |
| Hours shown in charts | `H0` and `H1` at the start of the script (default 6 AM to 10 PM) |

The campus map tab embeds an external map site. Set `MAP_URL` to your own campus map.

## A note on security

The sign-in is stored in the browser and exists to keep a shared screen tidy, not to protect sensitive data. For campus-wide use, host the page behind your college login or VPN.

## Built with

Plain HTML, CSS and JavaScript. Charts are hand-drawn SVG. The only external request is the optional Bricolage Grotesque web font, and the page falls back to system fonts when offline.

---

<div align="center">

Made for the SRIT campus. Keep every zone comfortable. 🟢

</div>
