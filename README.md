Real-Time Satellite Tracker - Project Description
Overview
A portable, GPS-enabled satellite tracking system built with an ESP32-C3 microcontroller that displays real-time positions of orbiting satellites on a Nokia 5110 LCD display. The device uses your exact GPS coordinates to calculate which satellites are currently visible above your local horizon, showing their elevation and azimuth angles.
What It Does
The tracker continuously:
Receives your precise location from a NEO-6M GPS module
Calculates satellite positions using SGP4 orbital propagation algorithms
Determines which satellites are currently above your horizon
Displays the highest satellite's name, elevation, and azimuth on a retro Nokia 5110 LCD
Updates every 5 seconds with live orbital data
Technical Specifications
Hardware:
Microcontroller: ESP32-C3 (RISC-V, 160MHz)
Display: Nokia 5110 LCD (PCD8544, 84×48 pixels)
GPS Module: NEO-6M (9600 baud, NMEA protocol)
Power: 3.3V USB or battery
Software:
TinyGPSPlus library for GPS parsing
Adafruit GFX + PCD8544 for display control
Hopperpop SGP4 library for orbital calculations
FreeRTOS task management for memory optimization
Custom coordinate transformation (ECEF to Topocentric)
Tracked Satellites:
ISS (International Space Station)
Hubble Space Telescope
NOAA 19 (Weather satellite)
Easily expandable to track any satellite with TLE data
Key Features
Real-time GPS positioning - Tracks your exact location anywhere on Earth
Accurate orbital mechanics - Uses SGP4 propagation for precise satellite positions
Horizon filtering - Only displays satellites actually visible above your horizon
Memory-optimized - Runs stable on ESP32-C3 with FreeRTOS task management
Portable design - Battery-powered, works anywhere with sky view
Retro display - Classic Nokia 5110 LCD for that authentic feel
How It Works
GPS Lock: The NEO-6M module acquires satellite signals and provides latitude, longitude, altitude, and UTC time
Orbital Calculation: The ESP32 uses SGP4 algorithms to propagate each satellite's orbit to the current time
Coordinate Transformation: Converts satellite positions from Earth-Centered Earth-Fixed (ECEF) to local topocentric coordinates (elevation/azimuth)
Visibility Check: Filters satellites with elevation > 0° (above horizon)
Display: Shows the highest satellite's name and position on the LCD
Technical Challenges Solved
Serial communication debugging - Resolved TX/RX wiring confusion between GPS and ESP32
Memory management - Fixed stack overflow crashes by implementing FreeRTOS tasks with 16KB stack allocation
Coordinate math - Implemented accurate ECEF-to-topocentric transformations for elevation/azimuth calculations
Library compatibility - Adapted code for Hopperpop SGP4 library's specific API requirements
Cold start optimization - GPS acquisition from 0 to 6 satellites in under 15 minutes
Use Cases
Amateur radio operators tracking ISS passes for contacts
Satellite observers planning visual observations
Educational projects demonstrating orbital mechanics
Portable tracking for field work or travel
IoT integration - Can be expanded with WiFi for remote monitoring
Future Enhancements
Add WiFi connectivity to fetch fresh TLE data from Celestrak
Implement pass prediction (next satellite overhead time)
Add buzzer alerts for ISS passes
Expand to track 50+ satellites simultaneously
Integrate compass/magnetometer for directional pointing
Add data logging for pass predictions
Project Significance
This project demonstrates advanced embedded systems programming, combining real-time GPS data acquisition, complex mathematical computations (orbital mechanics, coordinate transformations), and efficient memory management on a resource-constrained microcontroller. It transforms abstract satellite tracking concepts into a tangible, working device that provides real-time information about objects orbiting Earth.
Location: Cape Town, South Africa (-34.1361°, 18.4224°)
Status: Fully operational and tracking satellites in real-time


