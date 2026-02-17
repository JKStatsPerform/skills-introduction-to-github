# College Basketball Conference Clinching Dashboard

<img src="https://octodex.github.com/images/Professortocat_v2.png" align="right" height="200px" />

A real-time dashboard that displays NCAA Division I Basketball conference standings with automatic clinching detection and highlighting.

## 🏀 Features

- **31 NCAA D1 Conferences** - Displays standings for all Division I conferences
- **Live Data** - Fetches real-time standings from Stats Perform API
- **Clinching Detection** - Automatically highlights teams that have clinched their conference in green
- **Comprehensive Stats** - Shows overall record, conference record, and games back
- **Auto-Refresh** - Updates standings every 5 minutes
- **Responsive Design** - Works on desktop and mobile devices

## 📊 Dashboard Files

- **`index.html`** - Main dashboard that fetches live data from the API
- **`demo.html`** - Demo version with mock data to showcase the clinching logic

## 🎯 Clinching Logic

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

### View the Dashboard

Simply open `index.html` in a web browser. The dashboard will:
1. Automatically fetch the latest standings data
2. Calculate and highlight teams that have clinched
3. Refresh data every 5 minutes

### View the Demo

Open `demo.html` to see the dashboard with mock data demonstrating the clinching logic in action.

## 🔗 API Integration

Data is fetched from the Stats Perform API:
```
https://prod.origin.api.stats.com/v1/stats/basketball/cbk/standings
```

## 🎨 Visual Indicators

- **Green Background** - Team has clinched their conference
- **Games Back** - Shows how many games behind the leader each team is

## 📸 Screenshots

### Main Dashboard
![Dashboard UI](https://github.com/user-attachments/assets/d5ffa251-d2f2-4ef6-a6cd-3c73b5080e12)

### Demo with Clinching
![Dashboard with clinching](https://github.com/user-attachments/assets/9cd33c5d-f2c1-49a4-96da-59d5b2497d52)

---

&copy; 2025 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

