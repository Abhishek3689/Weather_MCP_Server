# Weather MCP Server 🌤️

A Model Context Protocol (MCP) server that provides weather information tools. This server enables AI assistants like Claude to fetch real-time weather data, forecasts, and compare weather across different cities.

## Features

- **Current Weather**: Get real-time weather information for any city
- **Weather Forecast**: Get weather predictions for up to 10 days (based on API plan)
- **Weather Comparison**: Compare weather conditions between two cities
- Supports both Celsius (metric) and Fahrenheit (imperial) units

## Prerequisites

- Python 3.8 or higher
- WeatherAPI.com API key (free tier available)

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Abhishek3689/Weather_MCP_Server.git
   cd weather-mcp-server
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   
   Create a `.env` file in the project root:
   ```bash
   WEATHER_API_KEY=your_api_key_here
   ```

   Get your free API key from [WeatherAPI.com](https://www.weatherapi.com/)

## Usage

🚀 Running The Server (Important!)
👉 If you double-click or run the file, you will NOT see results.

MCP servers do not show output directly.

They wait for Claude to connect to them.

But you can still start the server manually to ensure it’s working:
```
python weather_server_mcp.py
```
You would see somthing like this it means server is running correclty


              ╭──────────────────────────────────────────────────────────────────────────────╮
              │                                                                              │
              │                         ▄▀▀ ▄▀█ █▀▀ ▀█▀ █▀▄▀█ █▀▀ █▀█                        │
              │                         █▀  █▀█ ▄▄█  █  █ ▀ █ █▄▄ █▀▀                        │
              │                                                                              │
              │                                FastMCP 2.13.1                                │
              │                                                                              │
              │                                                                              │
              │                    🖥  Server name: Weather Server                            │
              │                                                                              │
              │                    📦 Transport:   STDIO                                     │
              │                                                                              │
              │                    📚 Docs:        https://gofastmcp.com                     │
              │                    🚀 Hosting:     https://fastmcp.cloud                     │
              │                                                                              │
              ╰──────────────────────────────────────────────────────────────────────────────╯

              
## Integration with Claude Desktop

To use this server with Claude Desktop, add the following to your Claude Desktop configuration:

**On macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`

**On Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "weather": {
      "command": "python",
      "args": [
        "weather_server_mcp.py"
      ],
      "env": {
        "WEATHER_API_KEY": "your_api_key_here"
      }
    }
  }
}
```
**Note :**
for 'command' write absolute location instead of only "python" by checking using in command prompt
```
where python
```
you will see somthing like this

```
C:\Users\YourName\AppData\Local\Programs\Python\Python312\python.exe
```
After updating the config, restart Claude Desktop.
### Available Tools

#### 1. Get Current Weather
```python
get_current_weather(city: str, units: str = "metric")
```
- **city**: City name (e.g., 'London', 'New York', 'Tokyo')
- **units**: 'metric' for Celsius or 'imperial' for Fahrenheit

**Example:**
```
get_current_weather("London", "metric")
```

#### 2. Get Weather Forecast
```python
get_forecast(city: str, days: int = 3, units: str = "metric")
```
- **city**: City name
- **days**: Number of forecast days (1-10)
- **units**: Temperature units

**Example:**
```
get_forecast("Paris", days=5, units="metric")
```

#### 3. Compare Weather
```python
compare_weather(city1: str, city2: str, units: str = "metric")
```
- **city1**: First city name
- **city2**: Second city name
- **units**: Temperature units

**Example:**
```
compare_weather("Tokyo", "New York", "metric")
```



## Project Structure

```
weather-mcp-server/
├── weather_server_mcp.py   # Main MCP server implementation
├── requirements.txt        # Python dependencies
├── .env                    # Environment variables (not committed)
├── .gitignore             # Git ignore file
└── README.md              # This file
```

## API Information

This project uses the [WeatherAPI.com](https://www.weatherapi.com/) service:
- Free tier: 1,000,000 calls/month
- 3-day forecast on free plan
- Real-time weather data
- Historical weather data

## Example Output

```
Current Weather in London, United Kingdom

📍 Location: 51.52, -0.11
🌡️  Temperature: 15°C
🤔 Feels Like: 14°C
☁️  Condition: Partly cloudy
💧 Humidity: 72%
🔽 Pressure: 1013.0 hPa
💨 Wind Speed: 15.1 kph
☁️  Cloudiness: 25%
👁️  Visibility: 10.0 km
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Troubleshooting

### "WEATHER_API_KEY environment variable not set"
- Make sure you've created a `.env` file with your API key
- Or set the environment variable in your system/Claude config

### "HTTP Error: 401"
- Check that your API key is valid
- Ensure the API key is correctly set in your `.env` file

### "Only X days available"
- Free tier of WeatherAPI.com provides 3-day forecasts
- Upgrade to a paid plan for extended forecasts

## Support

If you encounter any issues or have questions:
- Open an issue on GitHub
- Check the [WeatherAPI.com documentation](https://www.weatherapi.com/docs/)
- Review the [MCP documentation](https://modelcontextprotocol.io/)

## Author


Project Link: [https://github.com/Abhishek3689/Weather_MCP_Server](https://github.com/Abhishek3689/Weather_MCP_Server.git)

## Acknowledgments

- [FastMCP](https://github.com/jlowin/fastmcp) - Framework for building MCP servers
- [WeatherAPI.com](https://www.weatherapi.com/) - Weather data provider
- [Anthropic](https://www.anthropic.com/) - Claude AI and MCP protocol
