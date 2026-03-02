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

### NBA Standings Dashboard
- **`nba-standings.html`** - Comprehensive NBA standings dashboard organized by conference and division with email notifications
  - **Features:**
    - Real-time NBA standings from Stats Perform API
    - Conference and Division organization (Eastern: Atlantic, Central, Southeast | Western: Northwest, Pacific, Southwest)
    - Statistics: Conference Rank, Wins, Losses, Games Behind, Magic Number, Elimination Number
    - Color-coded teams: Green (playoff clinch), Blue (division clinch), Red (eliminated)
    - Email notification system for clinch/elimination events
    - Email distribution list management (add/remove)
    - Auto-refresh every 20 minutes
    - Last Checked timestamp
  - **`nba-standings-demo.html`** - Demo version with sample data

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

### NBA Standings Dashboard
A team's status is determined by multiple factors:

**Playoff Clinch (Green):**
1. Ranked in top 10 of conference
2. Current wins > maximum possible wins of 11th place team

**Division Clinch (Blue):**
1. First place in division
2. Current wins > maximum possible wins of 2nd place team in division

**Eliminated (Red):**
- Maximum possible wins < current wins of 10th place team

**Statistics Calculations:**
- **Games Behind**: `((leader_wins - team_wins) + (team_losses - leader_losses)) / 2`
- **Magic Number**: `(2nd_place_max_wins - division_leader_wins + 1)` (for division leaders)
- **Elimination Number**: `(10th_place_wins + 1 - team_max_wins)` (for teams outside playoff spots)

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

### NBA Standings Dashboard

1. **Open the Dashboard**: Open `nba-standings.html` in a web browser
2. **View Standings**: The dashboard automatically loads and displays:
   - Teams organized by conference (Eastern/Western) and division
   - Color-coded status indicators
   - Comprehensive statistics (W, L, GB, Magic #, Elim #)
3. **Manage Email Notifications**:
   - Add email addresses to receive notifications when teams clinch or are eliminated
   - Default recipient: sportsnews@stats.com
   - Remove emails by clicking the × button
4. **Auto-Refresh**: Dashboard automatically refreshes every 20 minutes
5. **View Demo**: Open `nba-standings-demo.html` to see sample data with all features

**Email Notifications:**
- Sent when a team clinches a playoff berth
- Sent when a team clinches their division
- Sent when a team is eliminated from playoff contention
- Note: Actual email sending requires backend integration; current implementation logs to console/localStorage

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

**⚠️ CORS Note for Production Deployment:**
When running the service from a local file or simple web server, you may encounter CORS (Cross-Origin Resource Sharing) errors when fetching from the Stats API. For production use, deploy the service on:
- A web server with a backend proxy that fetches the API data server-side
- A serverless function (Azure Functions, AWS Lambda, etc.) that handles API calls
- Or configure CORS headers if you control the API endpoint

The service includes robust error handling and will automatically retry failed requests every 5 minutes.

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

## 🚀 Production Deployment Recommendations

### For NBA Playoff Alert Service

The service is designed as a production-lean MVP. For optimal production deployment:

**Option 1: Serverless Function (Recommended)**
- Deploy as an Azure Function, AWS Lambda, or Google Cloud Function
- Schedule to run every 5 minutes using cron triggers
- Eliminates CORS issues and provides reliable execution
- Minimal infrastructure costs

**Option 2: Backend Proxy**
- Host the HTML on a web server
- Create a backend endpoint (Node.js, Python, etc.) to proxy API requests
- Avoids CORS restrictions

**Option 3: Dedicated Server**
- Deploy on a VM or container
- Use a task scheduler (cron, Windows Task Scheduler) to run checks
- Ideal for on-premises deployments

**Key Features for Production:**
- ✅ Automatic retry on API failures (every 5 minutes)
- ✅ Persistent state tracking (uses localStorage)
- ✅ Duplicate alert prevention
- ✅ Professional Teams message formatting
- ✅ Alert history logging

## 🎨 Visual Indicators

### NBA Standings Dashboard
- **Blue Background** - Team has clinched their division
- **Green Background** - Team has clinched a playoff spot (but not division)
- **Red Background** - Team has been eliminated from playoff contention
- **Legend** - Color key displayed at top of dashboard
- **Last Checked** - Timestamp showing when data was last fetched from API

### NBA Playoff Alert Service
- **Green Background** - Team has clinched a playoff spot
- **Alert Log** - Shows history of all playoff clinch alerts sent to Teams
- **Status Indicator** - Shows if the monitoring service is running or stopped

### College Basketball Dashboard
- **Green Background** - Team has clinched their conference
- **Games Back** - Shows how many games behind the leader each team is

## 📸 Screenshots

### NBA Standings Dashboard
![NBA Standings Dashboard](https://github.com/user-attachments/assets/39e8567f-49af-4c2b-9119-49c11b4455dc)
*Comprehensive standings organized by conference and division with color-coded status indicators*

![Email Management](https://github.com/user-attachments/assets/dc16af62-2ce4-4910-8733-6e12b66ef974)
*Email distribution list management for notifications*

### NBA Playoff Clinch Alert Service
![NBA Service Initial State](https://github.com/user-attachments/assets/b5778827-da46-4747-bdc4-d5ebf919497b)

![NBA Service Running](https://github.com/user-attachments/assets/76515dd6-69eb-41fc-8e3b-1fabf68d967d)

### College Basketball Dashboard
![Dashboard UI](https://github.com/user-attachments/assets/d5ffa251-d2f2-4ef6-a6cd-3c73b5080e12)

### Demo with Clinching
![Dashboard with clinching](https://github.com/user-attachments/assets/9cd33c5d-f2c1-49a4-96da-59d5b2497d52)

---

&copy; 2025 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

