# EV Battery Monitoring Dashboard

---

## Overview

This repository contains a **real‑time EV battery monitoring web application** built with **Node.js**, **Express**, and a lightweight front‑end using **HTML**, **CSS**, and **JavaScript**.  The project connects to an ESP‑32 based Battery Management System (BMS) to collect voltage, current, temperature, and state‑of‑charge data, stores it in a SQLite database, and visualises the metrics on a responsive dashboard.

---

## Key Features

- **Live telemetry** from the ESP‑32 BMS (`esp32_bms.ino`).
- **REST API** (`server.js`) for fetching recent sensor data.
- **SQLite persistence** (`setup.sql`) with helper scripts for data simulation (`simulate-data.js`).
- **Responsive UI** (`index.html`, `style.css`, `script.js`) showing charts and gauges.
- **Health‑check utilities** (`check-data.js`, `check-db.js`).
- **Docker‑ready** (add a `Dockerfile` if you want container deployment).

---

## Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/BOMMUGOWTHAMSAIREDDY97/excel.git
   cd excel
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up the database**
   ```bash
   sqlite3 ev_bms.db < setup.sql
   ```

4. **Run the development server**
   ```bash
   npm start   # or: node server.js
   ```
   The dashboard will be available at `http://localhost:3000`.

---

## Project Structure

```
├─ .gitignore               # Git ignore patterns
├─ .env (optional)         # Environment variables
├─ ESP32_BMS.ino            # Firmware for the ESP‑32 BMS
├─ index.html               # Dashboard UI
├─ style.css                # Styling (modern, dark‑mode ready)
├─ script.js                # Front‑end logic (fetches API data)
├─ server.js                # Express server & API routes
├─ package.json             # NPM metadata & scripts
├─ setup.sql                # SQLite schema & seed data
├─ simulate-data.js         # Generates mock telemetry data
├─ check-data.js            # Simple health‑check for incoming data
├─ check-db.js              # Verifies DB connectivity
└─ README.md                # ← **You are here**
```

---

## Usage

- **Live data**: Ensure the ESP‑32 is flashed with `esp32_bms.ino` and connected to the same network as the server. The device will POST JSON payloads to `/api/telemetry`.
- **Simulated data**: Run `node simulate-data.js` to feed dummy data into the DB for UI testing.
- **API reference**
  - `GET /api/telemetry/latest` – Returns the most recent reading.
  - `GET /api/telemetry/history?limit=N` – Returns the last `N` records.

---

## Contributing

Contributions are welcome! Feel free to:
- Improve UI/UX (add charts, dark‑mode toggles, etc.).
- Refactor the back‑end (add TypeScript, improve error handling).
- Write unit tests for the API routes.

Please open an issue or submit a pull request.

---

## License

This project is licensed under the **MIT License** – see the `LICENSE` file for details.

---


