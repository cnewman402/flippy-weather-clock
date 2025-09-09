# 🌤️ Flippy Weather Clock

A modern, animated flip clock weather card for Home Assistant. Features beautiful flip animations and weather forecasting with no jQuery dependency.

![Flippy Weather Clock](https://img.shields.io/badge/Home%20Assistant-Compatible-blue) ![Version](https://img.shields.io/badge/Version-1.4.1-green) ![No Dependencies](https://img.shields.io/badge/jQuery-Free-red)

## ✨ Features

- 🕐 **Animated Flip Clock** - Smooth digit animations every minute
- 🌤️ **Weather Integration** - Real-time weather data and forecasts
- 🎨 **Multiple Themes** - Default (blue) and Dusk (dark) themes
- 🌍 **Multi-language Support** - 9 languages supported
- 📱 **Responsive Design** - Works on desktop and mobile
- ⚡ **Modern Performance** - No jQuery, vanilla JavaScript only

## 🚀 Installation

### Step 1: Download Files
Place these files in `/config/www/flippy-weather/`:
- `flippy-flipclock-weather.js` (main file)
- `themes.js` (theme definitions)
- `regional.js` (language support)
- `themes/` folder (images and assets)

### Step 2: Required Sensors
Add to your `configuration.yaml`:
```yaml
sensor:
  - platform: time_date
    display_options:
      - 'time'
      - 'date'
      - 'date_time'
      - 'date_time_utc'
      - 'date_time_iso'
      - 'time_date'
      - 'time_utc'
```

### Step 3: Register Resource
Go to **Settings** → **Dashboards** → **Resources** → **Add Resource**:
- **URL**: `/local/flippy-weather/flippy-flipclock-weather.js`
- **Type**: JavaScript Module

### Step 4: Add Card
```yaml
type: custom:flippyweather-card
entity: weather.your_weather_provider
```

## 🎮 Configuration

### Basic Example
```yaml
type: custom:flippyweather-card
entity: weather.openweathermap
```

### Advanced Example
```yaml
type: custom:flippyweather-card
entity: weather.openweathermap
title: "Living Room Weather"
lang: en
am_pm: true
renderForecast: true
renderDetails: true
theme:
  name: default
  weather_icon_set: default
high_low_entity:
  entity_id: sensor.outdoor_temperature
  name: "Outdoor Temp"
```

## ⚙️ Configuration Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `entity` | string | **required** | Weather entity ID |
| `title` | string | optional | Card title |
| `lang` | string | `en` | Language code |
| `am_pm` | boolean | `false` | 12-hour time format |
| `renderForecast` | boolean | `true` | Show weather forecast |
| `renderDetails` | boolean | `true` | Show sun/wind details |
| `svrOffset` | number | `0` | Server time offset (seconds) |
| `theme.name` | string | `default` | Theme (default, dusk) |
| `theme.weather_icon_set` | string | `default` | Icon set name |
| `high_low_entity` | object | optional | Custom temperature entity |
| `widgetPath` | string | `/local/flippy-weather/` | Base asset path |

## 🎨 Themes

### Default Theme (Blue Gradient)
```yaml
theme:
  name: default
  weather_icon_set: default
```

### Dusk Theme (Dark)
```yaml
theme:
  name: dusk
  weather_icon_set: default
```

## 🌍 Supported Languages

- `en` - English
- `es` - Spanish
- `fr` - French
- `de` - German
- `it` - Italian
- `pt` - Portuguese
- `nl` - Dutch
- `ro` - Romanian
- `cz` - Czech

## 📁 File Structure

```
flippy-weather/
├── flippy-flipclock-weather.js
├── themes.js
├── regional.js
└── themes/
    ├── default/
    │   ├── clock/
    │   │   ├── clockbg1.png → clockbg6.png
    │   │   ├── 0.png → 9.png
    │   │   ├── 01-1.png → 91-3.png (animation frames)
    │   │   └── am.png, pm.png
    │   └── weather/
    │       └── default/
    │           ├── sunny.png
    │           ├── cloudy.png
    │           ├── night.png
    │           └── [weather icons...]
    └── dusk/
        ├── clock/
        └── weather/
```

## 🛠️ Troubleshooting

### Card doesn't appear
- Check resource registration
- Verify file paths
- Clear browser cache (Ctrl+F5)
- Check browser console for errors

### Images not loading
- Verify themes folder structure
- Check image file names
- Ensure correct file paths

### Weather not updating
- Verify weather entity exists
- Check `sensor.date_time_iso` sensor
- Verify internet connectivity

### Time not animating
- Check time_date sensors configured
- Verify clock images exist
- Clear browser cache

## 🔧 Development

### Key Improvements from Original
- ✅ **No jQuery dependency** - 85KB smaller bundle
- ✅ **Modern vanilla JavaScript** - Better performance
- ✅ **Error handling** - Null checks for DOM elements
- ✅ **Modern CSS** - Flexbox, gradients, backdrop-filter
- ✅ **Responsive design** - Mobile-friendly

### Performance Benefits
- **Faster DOM queries** - `querySelector()` vs jQuery
- **No library overhead** - Direct browser APIs
- **Better memory usage** - No jQuery object wrapping
- **Modern animations** - CSS transitions and transforms

## 📄 License

This project is licensed under the MIT License.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 🙏 Credits

- Original HTC Flip Clock concept
- Weather icons and animations
- Home Assistant community

## 📞 Support

If you have issues:
1. Check the troubleshooting section
2. Open an issue on GitHub
3. Check Home Assistant logs
4. Verify browser console for errors

---

**Enjoy your new Flippy Weather Clock! 🌤️**