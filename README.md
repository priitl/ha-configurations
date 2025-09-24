# 🏠 Smart Home Assistant Configuration

A comprehensive Home Assistant configuration featuring advanced energy management, intelligent climate control, and modern dashboard layouts with Estonian localization.

## 🌟 Key Features

### Energy Management & Automation
- ⚡ **Dynamic Pricing Integration**: Nord Pool electricity price automation with price-based climate control
- 📊 **Comprehensive Energy Monitoring**: Shelly Pro 3EM whole-home monitoring with ApexCharts visualization
- 💰 **Smart Cost Optimization**: Up to 3°C temperature reduction during expensive electricity periods
- 🔥 **Mill Heater Integration**: Automated consumption tracking and control

### Intelligent Climate Control
- 🌡️ **Room-Specific Temperature Targets**: Individual settings for living room (21°C), office (20°C), attic (19°C)
- 🔄 **Automatic Seasonal Detection**: Smart switching between heating/cooling based on month and outdoor temperature
- 🌊 **HVAC Mode Intelligence**: Full support for off/heat/cool/auto modes with Mitsubishi heat pump integration
- 💨 **Advanced Fan & Swing Control**: Dynamic adjustment of fan speeds and air direction
- ⚖️ **Efficiency Cycling**: Temperature hysteresis prevents frequent on/off switching
- 🏃 **Away Mode**: Minimal energy consumption with freeze/overheat protection

### Air Quality Monitoring
- 🌬️ **Comprehensive Sensors**: AirGradient integration for CO₂, VOC, NOx, and particulate matter
- 📈 **Real-time Tracking**: Temperature, humidity, PM0.3/PM1/PM2.5/PM10 monitoring
- 🚦 **Color-coded Status**: Visual indicators with Estonian language labels

### Modern Dashboard Design
- 📱 **Sections-Based Layout**: Desktop-optimized responsive design
- 📊 **Interactive Energy Analytics**: Dual-axis charts showing consumption vs pricing
- 🎛️ **Dynamic Controls**: Interactive sliders for price thresholds and climate settings
- 🎨 **Cyberpunk Theme**: Custom rounded-bubble theme with consistent color variables
- 🌐 **Estonian Localization**: Complete interface in Estonian language

## 🧩 Custom Cards & Dependencies

### Core Dashboard Components
- [`apexcharts-card`](https://github.com/RomRider/apexcharts-card) - Advanced chart visualization for energy data
- [`my-slider-v2`](https://github.com/AnthonMS/my-slider-v2) - Interactive sliders for price controls
- [`mushroom-cards`](https://github.com/piitaya/lovelace-mushroom) - Minimalist UI components
- [`navbar-card`](https://github.com/joseluis9595/lovelace-navbar-card) - Navigation interface
- [`button-card`](https://github.com/custom-cards/button-card) - Customizable buttons with templates
- [`card-mod`](https://github.com/thomasloven/lovelace-card-mod) - CSS styling modifications

### Additional Components
- [`mini-graph-card`](https://github.com/kalkih/mini-graph-card) - Compact data visualization
- [`auto-entities`](https://github.com/thomasloven/lovelace-auto-entities) - Dynamic entity lists
- [`weather-card`](https://github.com/bramkragten/weather-card) - Weather display
- [`kiosk-mode`](https://github.com/NemesisRE/kiosk-mode) - Fullscreen dashboard mode

## 📁 Repository Structure

```
├── configurations/
│   └── configuration.yaml          # Main HA config with sensors & input helpers
├── dashboards/
│   ├── 2k25.yaml                  # Modern responsive dashboard
│   └── old_dashboard.yaml         # Legacy dashboard reference
├── automations/
│   ├── smart-dynamic-climate-control.yaml  # Advanced climate automation
│   └── dynamic-climate-control.yaml        # Legacy climate control
└── themes/
    └── rounded-bubble.yaml        # Custom cyberpunk theme

```

## 🚀 Installation & Setup

1. Install required HACS integrations listed above
2. Copy configuration files to your Home Assistant config directory
3. Restart Home Assistant and check configuration
4. Import the dashboard configuration via Lovelace editor
5. Configure your device entities to match the configuration

## ⚙️ Key Integrations

- **Nord Pool**: Dynamic electricity pricing
- **Shelly Pro 3EM**: Whole-home energy monitoring
- **Mill Heaters**: Individual room heating control
- **AirGradient**: Comprehensive air quality monitoring
- **Mitsubishi Heat Pumps**: Advanced HVAC control
- **Estonian Holiday Calendar**: Local holiday detection for pricing

## 🎯 Advanced Features

### Template System
- Complex energy price calculations including all Estonian fees and taxes
- Automatic night/day rate detection with holiday calendar
- Dynamic seasonal and time-based automation triggers

### Button Card Templates
- Reusable slider templates with configurable units and precision
- Consistent styling across all dashboard components
- Theme-aware color variables

### Optimization Features
- Immediate response to user inputs with 15-minute sensor delays
- Trigger optimization to prevent automation conflicts
- Efficient sections layout for desktop usage
