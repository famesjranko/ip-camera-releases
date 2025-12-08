# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [1.4.0] - 2025-12-09 (Zero-Copy Pipeline & Power Optimization)

### Added
- **Camera Selector Dropdown**
  - Replace front/back toggle with dropdown showing all available cameras
  - Support for devices with multiple cameras (wide, telephoto, macro, etc.)
- **Zero-Copy H.264 Surface Mode**
  - Camera outputs directly to encoder's input Surface (eliminates buffer copies)
  - ~50% CPU reduction for H.264 encoding when preview is disabled
  - Auto-switches to ByteBuffer mode when preview is active
- **CPU Auto-Throttling**
  - Auto-reduce fps when CPU usage high (30→20→15→10→5fps)
  - Auto-recover fps when CPU normalizes
  - Dashboard shows throttle status in System Info panel
- **Thermal Throttling**
  - Battery temperature monitoring
  - Thresholds: 38°C warn, 42°C high, 48°C critical
- **Per-Client Frame Distribution**
  - Dedicated queue per viewer prevents slow clients blocking others
  - Smart drop policy maintains video sync
- **Resolution Error Persistence**
  - Failed resolutions remembered across restarts
  - Prevents re-selecting broken resolutions
- **Dashboard Auto-Reconnect**
  - Instant reconnection when browser tab becomes active
- **Preview Power Optimization**
  - Preview stops when app backgrounded or screen off
  - Streaming continues unaffected
- **Camera Standby Mode**
  - Camera pauses when no viewers connected
  - Auto-starts when first viewer connects
  - Reduces idle CPU significantly
- **Service Recovery**
  - Properly recovers when killed by system (e.g., OnePlus devices)

### Changed
- H.264 is now default when browser supports WebCodecs
- Improved auto-start handling for all Android devices

### Fixed
- Throttled frame rate no longer persists across restarts
- Auto-start now works on OnePlus 3 and older OEM devices
- Dashboard reconnects properly when device comes back online

---

## [1.3.0] - 2025-12-07 (Authentication & UI Refresh)

### Added
- **Dashboard Authentication**
  - Password protection for web dashboard
  - Session tokens with 7-day expiry
  - Rate limiting (5 failed attempts = 30s lockout)
- **OEM Auto-Start Detection**
  - Supports OPPO, Xiaomi, Huawei, Vivo, Samsung, OnePlus, ASUS
  - Guides users to enable auto-start permission
- **Close App Button** for clean shutdown
- **UI Enhancements**
  - Control bar labels above buttons
  - Improved visual consistency

### Changed
- Dark theme refined throughout
- Stream URLs include auth token when enabled

### Fixed
- Start on boot now works on Chinese OEM devices
- Settings dialog matches app theme

---

## [1.2.1] - 2025-12-06 (High-Res Snapshots)

### Added
- High-resolution still capture (up to 4K)
- Snapshot button in dashboard

### Fixed
- Lag accumulation in video feed
- Stream hang during resolution change
- Gray/corrupted frames after resolution change

---

## [1.2.0] - 2025-12-06 (Hardware Preview)

### Added
- Hardware-accelerated preview (~35% CPU savings)
- Quality slider controls H.264 bitrate
- H.264 auto-reconnection

### Changed
- Resolution selector shows native aspect ratios only

### Fixed
- Front/back camera rotation in dashboard

---

## [1.1.0] - 2025-12-05 (Stability)

### Added
- Preview toggle (~35% CPU savings when disabled)

### Fixed
- Color flickering at high resolutions
- App freeze on rapid button taps

---

## [1.0.0] - 2025-12-05

### Added
- Custom app icons
- Mobile-friendly dashboard layout

---

## [0.9.0] - 2025-12-05

### Added
- Remote start/stop from dashboard
- Viewer count overlay

---

## [0.6.0] - 2025-12-04

### Added
- H.264 hardware encoding
- WebCodecs decoder for browsers

---

## [0.1.0] - 2025-12-04 (Initial Release)

### Added
- MJPEG streaming over HTTP
- Web dashboard with dark theme
- Two-way audio
- Text-to-speech
- Settings sync between app and web
- HTTPS support
- Background streaming
