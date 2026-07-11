# Cairo Metro Line 2 Monitoring Dashboard

## Overview
The Cairo Metro Line 2 Monitoring Dashboard is a modern, responsive web application designed to monitor environmental conditions across 20 metro stations. It provides real-time visualization of temperature and humidity data collected from 40 sensors (two per station). The dashboard is intended for metro operators, maintenance teams, and facility managers to quickly identify anomalies, track historical trends, and ensure optimal environmental conditions for equipment and passenger comfort.

## Features
- **Dashboard Overview**: A high-level view of all stations, aggregate KPIs, and system-wide alerts.
- **Station Navigation**: A dedicated "All Stations" page featuring a clean, consolidated table of all sensors across the network, sorted by temperature. Clicking a station seamlessly navigates to its individual dashboard.
- **Individual Station Pages**: Dedicated dashboards for each station showing combined sensor data, a dashboard-style hero card for average conditions, Station Health indicators, and historical trends.
- **Sensor Details Pages**: Drill-down views for individual sensors with detailed vitals (temperature, humidity, sensor status, signal strength) and reading history.
- **Temperature & Humidity Monitoring**: Visualizations of current readings, 7-day averages, and trends against warning and critical thresholds.
- **Alerts and Sensor Health**: Automatic categorization of readings into Normal, Warning, and Critical states, with a dedicated alerts log.
- **Charts and Visualizations**: Line charts, area charts, histograms, and comparative dual-line charts for deep data analysis.
- **Filters**: A slide-out filter panel to refine data by date range, station, and alert status.
- **Dark/Light Mode**: Full support for both dark and light themes with smooth transitions.
- **Auto-Refresh Simulation**: A toggleable auto-refresh feature to simulate real-time data incoming.

## Technologies Used
- **HTML5**: Semantic markup for the single-page application structure.
- **CSS3 (Vanilla)**: Custom styling using CSS variables for theming, Flexbox/Grid for layouts, and modern pseudo-selectors.
- **JavaScript (ES6+)**: Vanilla JS for logic, DOM manipulation, and dynamic SVG chart generation. No external frameworks (like React or Vue) are used.
- **SVG (Scalable Vector Graphics)**: Used natively within JavaScript to render lightweight, responsive, and customizable data visualizations (charts, gauges, histograms) without external charting libraries.

## How It Works
The application functions as a Single Page Application (SPA), managing different "views" within the DOM:

1. **Open the dashboard**: The app loads index.html, initializes the global state, processes the dataset from data.js, and renders the default Overview dashboard.
2. **Select Metro Line 2**: The sidebar allows users to focus on specific lines (currently, Line 2 is implemented).
3. **View All Stations**: Users can navigate to the "All Stations" page, which features a clean, consolidated table of all sensors across the network, sorted by temperature.
4. **Open a station**: Clicking a station in the table seamlessly navigates to a completely separate Station Details dashboard page.
5. **Explore the station dashboard**: The user can view the Station Health KPI (Healthy/Warning/Critical), average conditions hero card, temperature distribution, 7-day trends, and recent alerts for that specific location.
6. **Click a sensor**: The station dashboard features interactive "Sensor A" and "Sensor B" cards. Clicking either card drills down further.
7. **View the sensor details page**: The app navigates to a dedicated page for that exact device, showing its specific gauge, vitals (including Online/Offline status), alert history, and complete reading log. The back button returns the user to the station context.

Data flows entirely on the client side: RAW data is loaded, filtered through getter functions based on global state, and passed into specialized rendering functions that manipulate innerHTML with template literals and SVG strings.

## Dashboard Pages

### 1. Overview Page
The default landing view. It displays system-wide KPIs (total alerts, average system temperature), a master temperature history chart, an alert distribution histogram, a leaderboard of the top warning stations, and a recent alerts log across the entire line.

### 2. All Stations Page
A unified, easily scannable list of all active sensors sorted by temperature. This gives users immediate visibility into the hottest sensors and their current connection status.

### 3. Station Details Page
Focused on a single station (e.g., Shubra El-Kheima). It displays a large Hero Card for Average Conditions, a Station Health KPI, and individual status cards for Sensor A and Sensor B. It also provides a 7-day temperature distribution and daily average trends for the station.

### 4. Sensor Details Page
The deepest drill-down level. It focuses on a single hardware device (e.g., SEN001). It prominently features a radial gauge for current temperature, a vitals panel (including Online/Offline Sensor Status, signal bars), the sensor's specific alert history, and a tabular log of all historical readings.

## Dataset
The dataset (`assets/data/data.js`) represents simulated environmental data for the first week of July 2026.
It exposes a global `window.DASHBOARD_DATA` object containing:
- **sensors**: Array of 40 objects. (Columns: id, name, installed, building, room, floor).
- **readings**: Array of hourly data points. (Columns: t [timestamp], s [sensor ID], v [temperature value], h [humidity], b [battery %], sg [signal 1-5], st [status: Normal/Warning/Critical]).
- **alerts**: Array of triggered events based on readings crossing thresholds. (Columns: id, s, t, lvl, msg, status).
- **days**: Array of objects mapping dates to human-readable labels.

## Visualizations
The dashboard implements custom SVG visualizations generated purely via JavaScript:
- **Radial Gauge**: Used on the Sensor Details page and as a Hero Card on the Station Details page to show current temperature against a colored arc (green/amber/red).
- **Line Charts**: Used for Temperature History, featuring critical/warning threshold lines, tooltips, and data points.
- **Area Charts**: Used for Humidity Trends, utilizing gradients for a modern look.
- **Dual-Line Comparison Chart**: Used on the Station Details page to overlay Sensor A vs Sensor B daily averages.
- **Histograms / Bar Charts**: Used for Alert Distribution and Temperature Distribution, mapping frequencies to color-coded bars.
- **KPI Cards & Badges**: Clean, iconic representations of vital stats (Sensor Status, Signal, Alerts, Station Health) using color to indicate urgency.

## Screenshots

### Main Dashboard Overview
<img width="1565" height="852" alt="Image" src="https://github.com/user-attachments/assets/ca3fab46-41e2-4aa5-882a-a9bf155e526a" />
<img width="1579" height="789" alt="Image" src="https://github.com/user-attachments/assets/5ae9387f-68d0-48cb-a6be-c1489a63ba49" />

### All stations
<img width="1885" height="858" alt="Image" src="https://github.com/user-attachments/assets/d6729b39-389a-488c-9655-c0ca01337b84" />

### Station Details Page

<img width="1894" height="870" alt="Image" src="https://github.com/user-attachments/assets/5038f10c-ec6d-4d8a-b42b-1ef91bc46d24" />

<img width="1890" height="878" alt="Image" src="https://github.com/user-attachments/assets/b8d3a71a-cf06-4f59-ae90-6c95fdd7b2a5" />

<img width="1895" height="873" alt="Image" src="https://github.com/user-attachments/assets/b7d66138-483a-4bc8-8b14-08c7dd0755dc" />

### Sensor details

<img width="1904" height="868" alt="Image" src="https://github.com/user-attachments/assets/7c627608-5fc1-432d-8026-90834b4bf517" />

<img width="1904" height="877" alt="Image" src="https://github.com/user-attachments/assets/173ff1d1-c922-4138-9194-23f6a846fdba" />

### Global Filter Panel
<img width="1920" height="922" alt="Image" src="https://github.com/user-attachments/assets/d1b1b924-8ee8-448e-8e75-f0c07be6584a" />
