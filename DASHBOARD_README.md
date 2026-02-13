# College Basketball Clinching Dashboard

A responsive web dashboard that displays NCAA College Basketball conference standings and highlights teams that have clinched their conference championship.

## Features

- **Real-time Data**: Fetches standings from Stats API
- **Clinching Logic**: Automatically calculates and highlights teams that have mathematically clinched their conference
- **Multiple Conferences**: Tracks three major conferences:
  - American Athletic Conference (18 conference games)
  - Big Ten Conference (20 conference games)
  - Big East Conference (18 conference games)
- **Visual Highlights**: Teams that have clinched are displayed with:
  - Green background highlighting
  - Green "CLINCHED" badge
  - Green left border accent
- **Responsive Design**: Works on desktop and mobile devices
- **Professional Styling**: Modern gradient background with clean, card-based layout

## Files

### index.html
Main dashboard that fetches live data from the Stats API:
```
https://prod.origin.api.stats.com/v1/stats/basketball/cbk/standings
```

### demo.html
Demo version with mock data that demonstrates the dashboard functionality and clinching logic. Perfect for testing and development without API access.

## How It Works

### Clinching Logic

A team is considered to have clinched their conference championship when:

1. They are currently in first place
2. The second-place team cannot mathematically catch them in wins

The calculation:
- Team's current conference wins > Second place team's maximum possible wins
- Maximum possible wins = Current wins + Games remaining

### Example:
In a conference with 18 games:
- Team A: 15-2 (15 wins, 1 game remaining, max 16 wins)
- Team B: 12-5 (12 wins, 1 game remaining, max 13 wins)
- Result: Team A has clinched (15 current wins > 13 max possible wins for Team B)

## Usage

### Running Locally

1. Clone the repository
2. Open `index.html` in a web browser to see live data
3. Or open `demo.html` to see the demo with mock data

### With a Local Server

```bash
# Using Python 3
python3 -m http.server 8000

# Then navigate to:
# http://localhost:8000/index.html  (for live API data)
# http://localhost:8000/demo.html   (for demo with mock data)
```

## Dashboard Layout

Each conference section displays:
- **Rank**: Team's position in conference standings
- **Team Name**: Full team display name with clinching badge if applicable
- **Conf W-L**: Conference wins and losses
- **Overall W-L**: Season wins and losses
- **Conf PCT**: Conference winning percentage
- **GB**: Games behind the leader

## Browser Compatibility

Works in all modern browsers that support:
- ES6 JavaScript (async/await, arrow functions)
- CSS Grid and Flexbox
- Fetch API

## API Integration

The dashboard expects the Stats API to return data in this format:

```json
{
  "conferences": [
    {
      "name": "Big Ten",
      "standings": [
        {
          "team": {
            "id": 1,
            "name": "Team Name",
            "displayName": "Team Display Name"
          },
          "stats": {
            "conferenceWins": 15,
            "conferenceLosses": 3,
            "wins": 24,
            "losses": 5,
            "gamesBack": "0"
          }
        }
      ]
    }
  ]
}
```

## Screenshots

### Dashboard with Clinched Team
![Dashboard showing Memphis Tigers clinched in American Athletic Conference](https://github.com/user-attachments/assets/dcbfb3df-ae1e-4abb-a666-32c65bf97536)

## License

MIT License - See LICENSE file for details
