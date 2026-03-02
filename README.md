# Basketball Analytics Dashboards

<img src="https://octodex.github.com/images/Professortocat_v2.png" align="right" height="200px" />

Real-time dashboards and services for basketball standings, clinching detection, and automated alerts.

## 🏀 Features

- **31 NCAA D1 Conferences** - Displays standings for all Division I conferences
- **Live Data** - Fetches real-time standings from Stats Perform API
- **Clinching Detection** - Automatically highlights teams that have clinched their conference in green
- **Comprehensive Stats** - Shows overall record, conference record, and games back
- **Auto-Refresh** - Updates standings every 5 minutes
- **Responsive Design** - Works on desktop and mobile devices

## 📊 Available Services

### NBA Playoff Clinch Alert Service
- **`nba-playoff-alerts.html`** - Production-lean MVP service that monitors NBA standings and posts real-time playoff clinch alerts to Microsoft Teams
  - **Features:**
    - Real-time NBA standings from Stats Perform API
    - Automatic playoff clinching detection (top 10 teams per conference)
    - Microsoft Teams webhook integration
    - Alert history tracking
    - Auto-refresh every 5 minutes
    - Test webhook functionality

### College Basketball Conference Dashboard
- **`index.html`** - Main dashboard that fetches live data from the API
- **`demo.html`** - Demo version with mock data to showcase the clinching logic

## 🎯 Clinching Logic

### NBA Playoff Clinching
A team **clinches a playoff spot** when:
1. They are ranked in the top 10 of their conference (Eastern or Western)
2. Their current overall wins exceed the maximum possible wins of the team in 11th place

The maximum possible wins for the 11th place team = current wins + remaining games (82 total games in NBA regular season)

**Microsoft Teams Integration:**
- When a team clinches, an automated alert is sent to the configured Teams channel
- Alerts include team name, conference, rank, and record information
- Uses Microsoft Teams MessageCard format with adaptive card styling
- Prevents duplicate alerts by tracking previously clinched teams

### College Basketball Conference Clinching
A team **clinches their conference** when:
1. They are in first place (most conference wins)
2. Their current conference wins exceed the maximum possible wins of the second-place team

The maximum possible wins for second place = current wins + remaining conference games

## 📋 Conferences Included

The dashboard includes all 31 NCAA Division I conferences with their specific conference game counts:

| Conference | Games | Conference | Games |
|------------|-------|------------|-------|
| America East | 16 | Metro Atlantic Athletic | 20 |
| American Conference | 18 | Mid-American | 18 |
| Atlantic 10 | 18 | Mid-Eastern | 14 |
| Atlantic Coast | 20 | Missouri Valley | 20 |
| Atlantic Sun | 18 | Mountain West | 20 |
| Big East | 20 | Northeast | 16 |
| Big Ten | 20 | Ohio Valley | 20 |
| Big 12 | 20 | Patriot League | 18 |
| Big Sky | 18 | Southeastern | 20 |
| Big South | 18 | Southern | 18 |
| Big West | 20 | Southland | 20 |
| Coastal Athletic | 18 | Southwestern Athletic | 18 |
| Conference USA | 20 | Summit League | 16 |
| Horizon | 20 | Sun Belt | 18 |
| Ivy League | 14 | West Coast | 18 |
|  |  | Western Athletic | 16 |

## 🚀 Usage

### NBA Playoff Alerts Service

1. **Open the Service**: Open `nba-playoff-alerts.html` in a web browser
2. **Configure Teams Webhook**:
   - Go to your Microsoft Teams channel
   - Click on the three dots (•••) > Connectors > Incoming Webhook
   - Configure a new webhook and copy the URL
   - Paste the webhook URL into the service and click "Save Configuration"
3. **Test the Integration**: Click "Test Webhook" to verify the connection
4. **Start Monitoring**: Click "Start Monitoring" to begin watching for playoff clinches
5. **Automatic Alerts**: When a team clinches a playoff spot, the service automatically sends a formatted alert to your Teams channel

### College Basketball Dashboard

Simply open `index.html` in a web browser. The dashboard will:
1. Automatically fetch the latest standings data
2. Calculate and highlight teams that have clinched
3. Refresh data every 5 minutes

### View the Demo

Open `demo.html` to see the dashboard with mock data demonstrating the clinching logic in action.

## 🔗 API Integration

### NBA Playoff Alerts
Data is fetched from the Stats Perform NBA API:
```
https://prod.origin.api.stats.com/v1/stats/basketball/nba/standings
```

### College Basketball Dashboard
Data is fetched from the Stats Perform CBK API:
```
https://prod.origin.api.stats.com/v1/stats/basketball/cbk/standings
```

## 🎨 Visual Indicators

### NBA Service
- **Green Background** - Team has clinched a playoff spot
- **Alert Log** - Shows history of all playoff clinch alerts sent to Teams
- **Status Indicator** - Shows if the monitoring service is running or stopped

### College Basketball Dashboard
- **Green Background** - Team has clinched their conference
- **Games Back** - Shows how many games behind the leader each team is

## 📸 Screenshots

### Main Dashboard
![Dashboard UI](https://github.com/user-attachments/assets/d5ffa251-d2f2-4ef6-a6cd-3c73b5080e12)

### Demo with Clinching
![Dashboard with clinching](https://github.com/user-attachments/assets/9cd33c5d-f2c1-49a4-96da-59d5b2497d52)

---

&copy; 2025 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

