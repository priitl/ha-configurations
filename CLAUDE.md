# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a comprehensive Home Assistant configuration repository for a smart home system with advanced energy management, intelligent climate control, and custom dashboard layouts. The system features dynamic pricing-based automation, room-specific temperature control, and a modern responsive UI.

## Architecture & Structure

### Core Configuration
- `configurations/configuration.yaml`: Main Home Assistant configuration with energy monitoring, template sensors, and input helpers
- `dashboards/2k25.yaml`: Modern responsive dashboard with energy analytics, climate controls, and air quality monitoring
- `dashboards/old_dashboard.yaml`: Legacy dashboard configuration for reference
- `themes/rounded-bubble.yaml`: Custom theme with color variables and styling
- `automations/smart-dynamic-climate-control.yaml`: Advanced climate automation with HVAC modes, fan control, and efficiency cycling
- `automations/dynamic-climate-control.yaml`: Legacy climate control automation

### Key Components
- **Energy Monitoring**: Shelly Pro 3EM whole-home monitoring, Mill heater consumption tracking, Nord Pool price integration
- **Intelligent Climate Control**: Price-based automation with room-specific targets, seasonal detection, HVAC mode management
- **Air Quality Monitoring**: AirGradient sensors for CO2, VOC, NOx, and particulate matter tracking
- **Modern Dashboard**: ApexCharts visualization, interactive price controls, responsive sections layout
- **Theme Integration**: Cyberpunk-inspired rounded-bubble theme with consistent color variables
- **Localization**: Estonian language interface throughout

### Configuration Pattern
Home Assistant uses a modular configuration approach:
- Main configuration references external files with `!include` directives
- Template sensors for derived calculations (energy costs, time-based states)
- Input helpers for user-configurable parameters
- Utility meters for energy consumption tracking cycles

## Custom Cards & Dependencies

The dashboard relies on multiple HACS (Home Assistant Community Store) integrations:
- `apexcharts-card`: Advanced chart visualization for energy data\n- `my-slider-v2`: Interactive sliders for price controls
- `mushroom-cards`: Minimalist UI components for climate and sensors
- `navbar-card`: Navigation interface
- `button-card`: Customizable buttons
- `card-mod`: CSS styling modifications
- `mini-graph-card`: Data visualization
- `auto-entities`: Dynamic entity lists
- `weather-card`: Weather display
- `kiosk-mode`: Fullscreen dashboard mode

## Key Configuration Areas

### Energy Management
- Nord Pool electricity price integration for dynamic pricing
- Mill heater monitoring and control
- Shelly Pro 3EM for whole-home energy monitoring
- Automated calculations for hourly/daily energy costs

### Climate Automation
- **Smart Climate Control**: Room-specific temperature targets with automatic seasonal detection
- **HVAC Mode Management**: Intelligent switching between off/heat/cool/auto modes based on conditions
- **Fan & Swing Control**: Dynamic adjustment of Mitsubishi heat pump fan speeds and air direction
- **Efficiency Cycling**: Automatic on/off cycling with temperature hysteresis to prevent frequent switching
- **Price-Based Logic**: Up to 3°C temperature reduction during expensive electricity periods
- **Away Mode**: Minimal energy consumption with freeze/overheat protection
- **Trigger Optimization**: Immediate response to user changes, 15-minute delays for temperature sensors

### Dashboard Layout
- **Sections-Based Design**: Modern Home Assistant sections layout for desktop optimization
- **Energy Analytics**: ApexCharts with consumption vs price visualization, themed colors
- **Interactive Controls**: My-slider-v2 components for min/max price adjustments
- **Air Quality Dashboard**: Comprehensive monitoring with color-coded status indicators
- **Climate Overview**: Real-time climate device status with temperature controls
- **Responsive Navigation**: User-specific layouts with conditional visibility
- **Button Card Templates**: Reusable slider templates with configurable units and precision

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
- Dashboard changes can be tested live in the Lovelace editor

### Key Files to Monitor
- `configurations/configuration.yaml`: Sensor definitions, template sensors, input helpers
- `dashboards/2k25.yaml`: Main dashboard with energy tab, navigation, and custom templates
- `automations/smart-dynamic-climate-control.yaml`: Advanced climate automation
- `themes/rounded-bubble.yaml`: Color variables and styling definitions\n\n## Latest Features & Implementation Details\n\n### Smart Climate Control System\nThe `smart-dynamic-climate-control.yaml` automation provides:\n- **Room-Specific Targets**: Individual temperature settings for living room (21°C), office (20°C), and attic (19°C)\n- **Automatic Seasonal Detection**: Based on month (June-September) and outdoor temperature (>22°C)\n- **HVAC Mode Intelligence**: Uses Home Assistant standard modes (`off`, `heat`, `cool`, `auto`)\n- **Fan & Swing Control**: Mitsubishi-specific modes (`1 Lowest`, `2 Low`, `3 High` for fan; `Lowest`, `Normal`, `Highest` for swing)\n- **Efficiency Cycling**: 0.5°C hysteresis prevents frequent on/off switching\n- **Price-Based Logic**: Up to 3°C temperature reduction during expensive electricity\n- **Optimized Triggers**: Immediate response to user inputs, 15-minute delays for temperature sensors\n\n### Energy Dashboard\nThe energy tab features:\n- **ApexCharts Integration**: Dual-axis chart showing electricity price vs consumption\n- **Interactive Controls**: My-slider-v2 components for min/max price adjustments\n- **Theme Colors**: Uses rounded-bubble.yaml variables (var(--red), var(--blue), var(--teal))\n- **Button Card Templates**: Reusable `custom_card_slider` template with configurable units and precision\n- **Sections Layout**: Desktop-optimized layout with Overview, Insights, Controls, and Analytics sections\n\n### Air Quality Monitoring\nComprehensive monitoring with AirGradient sensors:\n- Temperature, humidity, CO₂ levels\n- VOC and NOx indices for air quality\n- PM0.3, PM1, PM2.5, PM10 particulate matter tracking\n- Color-coded status indicators with Estonian language labels\n\n### Template System\n- **Energy Price Calculation**: Complex template including transmission fees, renewable fees, excise tax, VAT, and holiday detection\n- **Time-Based Logic**: Automatic night/day rate detection with Estonian holiday calendar\n- **Button Card Templates**: Moved from decluttering_templates to proper button_card_templates section"