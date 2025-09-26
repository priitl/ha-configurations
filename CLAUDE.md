# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a comprehensive Home Assistant configuration repository for a smart home system with advanced energy management, intelligent climate control, and custom dashboard layouts. The system features dynamic pricing-based automation, humidity-aware climate control, presence-based lighting, and a modern responsive UI with consistent theme integration.

## Architecture & Structure

### Core Configuration
- `configurations/configuration.yaml`: Main Home Assistant configuration with energy monitoring, template sensors, and input helpers
- `dashboards/2k25.yaml`: Modern responsive dashboard with energy analytics, climate controls, air quality monitoring, and optimized mobile layouts
- `themes/rounded-bubble.yaml`: Custom theme with comprehensive color variables and styling
- `automations/smart-dynamic-climate-control.yaml`: Advanced climate automation with humidity-aware HVAC modes, separate sensor integration, and efficiency cycling
- `automations/pooningutuba-presence-lighting.yaml`: Presence-based lighting automation for attic room with luminance consideration

### Key Components
- **Energy Monitoring**: Shelly Pro 3EM whole-home monitoring, Mill heater consumption tracking, Nord Pool price integration
- **Intelligent Climate Control**: Humidity-aware automation with room-specific targets, seasonal detection, and dedicated sensor integration
- **Presence-Based Lighting**: Automated lighting control with luminance detection and away mode integration
- **Air Quality Monitoring**: AirGradient sensors for CO2, VOC, NOx, and particulate matter tracking
- **Modern Dashboard**: ApexCharts visualization, interactive price controls, responsive sections layout with theme consistency
- **Theme Integration**: Consistent color variables throughout all UI components
- **Localization**: Estonian language interface throughout

### Configuration Pattern
Home Assistant uses a modular configuration approach:
- Main configuration references external files with `!include` directives
- Template sensors for derived calculations (energy costs, time-based states)
- Input helpers for user-configurable parameters with descriptive naming
- Utility meters for energy consumption tracking cycles

## Custom Cards & Dependencies

The dashboard relies on multiple HACS (Home Assistant Community Store) integrations:
- `apexcharts-card`: Advanced chart visualization for energy data
- `button-card`: Customizable buttons with extensive templating
- `mushroom-cards`: Minimalist UI components for climate and sensors
- `navbar-card`: Navigation interface
- `card-mod`: CSS styling modifications
- `mini-graph-card`: Data visualization
- `auto-entities`: Dynamic entity lists
- `weather-card`: Weather display
- `kiosk-mode`: Fullscreen dashboard mode

## Key Configuration Areas

### Energy Management
- Nord Pool electricity price integration for dynamic pricing
- Mill heater monitoring and control with efficiency cycling
- Shelly Pro 3EM for whole-home energy monitoring
- Automated calculations for hourly/daily energy costs
- Unified color coding using theme variables for price/consumption insights

### Climate Automation
- **Smart Climate Control**: Room-specific temperature targets using dedicated sensors
- **Humidity-Aware HVAC**: Prioritizes heating over drying - dry mode only when temperature target is met
- **Separate Sensor Integration**: Uses room-specific temperature and humidity sensors instead of climate device sensors
- **Device Safety**: Temperature constraints (16-30°C for Mitsubishi pump) to prevent device errors
- **Fan & Swing Control**: Dynamic adjustment of Mitsubishi heat pump fan speeds and air direction
- **Efficiency Cycling**: 0.5°C hysteresis prevents frequent on/off switching
- **Price-Based Logic**: Up to 3°C temperature reduction during expensive electricity periods
- **Away Mode**: Minimal energy consumption with freeze/overheat protection
- **Optimized Triggers**: Immediate response to user changes, 15-minute delays for sensor readings

### Presence-Based Lighting
- **Luminance Integration**: Lights only activate when presence detected AND illuminance below threshold
- **Away Mode Respect**: No lighting activation when away mode is enabled
- **Efficient Triggering**: Periodic checks every 30 minutes for illuminance changes
- **Room-Specific Control**: Tailored light selection based on room usage patterns

### Dashboard Layout
- **Sections-Based Design**: Modern Home Assistant sections layout optimized for desktop and mobile
- **Energy Analytics**: ApexCharts with consumption vs price visualization using theme colors
- **Interactive Controls**: Temperature and price adjustment controls with consistent styling
- **Air Quality Dashboard**: Comprehensive monitoring with color-coded status indicators
- **Climate Overview**: Real-time climate device status with temperature controls
- **Responsive Navigation**: User-specific layouts with conditional visibility
- **Mobile Optimization**: Room card layouts that prevent UI crowding on small screens
- **Theme Consistency**: All UI elements use theme variables instead of hardcoded colors

## Working with This Repository

### Configuration Validation
Home Assistant provides built-in configuration checking. After making changes:
1. Use Home Assistant's "Check Configuration" tool in the UI
2. Monitor logs for syntax errors in YAML files
3. Test dashboard changes in the Lovelace UI editor

### File Editing
- Always validate YAML syntax before committing changes
- Use consistent indentation (2 spaces)
- Test configuration changes in a development environment when possible
- Dashboard changes can be tested live in the Lovelace UI editor
- Use theme variables instead of hardcoded colors for consistency

### Key Files to Monitor
- `configurations/configuration.yaml`: Sensor definitions, template sensors, input helpers
- `dashboards/2k25.yaml`: Main dashboard with energy analytics, room controls, and custom templates
- `automations/smart-dynamic-climate-control.yaml`: Advanced climate automation with humidity logic
- `automations/pooningutuba-presence-lighting.yaml`: Presence-based lighting control
- `themes/rounded-bubble.yaml`: Color variables and styling definitions

## Latest Implementation Details

### Smart Climate Control System
The `smart-dynamic-climate-control.yaml` automation provides:
- **Room-Specific Targets**: Individual temperature settings using input helpers (input_number.living_room_target_temp, etc.)
- **Dedicated Sensor Integration**: Uses separate room sensors for accurate readings:
  - Living room: sensor.suur_tuba_esp32_temperature/humidity (controls climate.mitsubishi_pump)
  - Office: sensor.kontor_esp32_temperature/humidity (controls climate.mill_heatergen3panel)
  - Attic: sensor.ag_one_temperature/humidity (controls climate.mill_heatergen3panel_2)
- **Humidity-Based HVAC Logic**: Prioritizes heating over drying - only uses dry mode when temperature is at target AND humidity exceeds thresholds
- **Device Temperature Limits**: Mitsubishi pump constrained to 16-30°C range to prevent device errors
- **Automatic Seasonal Detection**: Based on month (June-September) and outdoor temperature (>22°C)
- **Intelligent Mode Selection**: Living room prefers auto/fan_only over off for better air circulation
- **Fan & Swing Control**: Mitsubishi-specific modes for optimal air distribution
- **Efficiency Cycling**: Hysteresis prevents frequent on/off switching
- **Price-Based Logic**: Dynamic temperature reduction during expensive electricity periods
- **Optimized Triggers**: Immediate response to user inputs, delayed response to sensor changes

### Energy Dashboard
The energy tab features:
- **ApexCharts Integration**: Dual-axis chart showing electricity price vs consumption
- **Interactive Controls**: Price adjustment controls with consistent styling
- **Theme Color Integration**: Uses theme variables (var(--red), var(--orange), var(--green)) consistently
- **Unified Color Scheme**: Energy insights cards use consistent red/orange/green color progression
- **Sections Layout**: Desktop-optimized layout with Overview, Insights, Controls, and Analytics sections
- **Responsive Design**: Optimized for both desktop and mobile viewing

### Room Cards & UI Components
- **Custom Button Card Templates**: Comprehensive room sensor cards with temperature controls and light management
- **Mobile-Optimized Layout**: Grid template prevents light controls from being pushed off-screen
- **Theme Integration**: Light icons use var(--orange) when turned on, consistent with overall theme
- **Sensor Display**: Shows temperature, humidity, and CO2 data with proper formatting
- **Interactive Elements**: Temperature adjustment controls and light toggles with visual feedback

### Air Quality Monitoring
Comprehensive monitoring with AirGradient sensors:
- Temperature, humidity, CO₂ levels with proper unit display
- VOC and NOx indices for air quality assessment
- PM0.3, PM1, PM2.5, PM10 particulate matter tracking
- Color-coded status indicators with Estonian language labels
- Integration with room cards for unified display

### Template System
- **Energy Price Calculation**: Complex template including transmission fees, renewable fees, excise tax, VAT, and holiday detection
- **Time-Based Logic**: Automatic night/day rate detection with Estonian holiday calendar
- **Button Card Templates**: Proper template structure for reusable UI components
- **Variable Naming**: Descriptive variable names with clear purpose indication
- **Theme Variable Usage**: Consistent use of CSS custom properties for styling