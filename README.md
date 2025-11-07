# Smart India Hackathon Workshop
# Date:07/11/2025
## Register Number:212224040027
## Name:
## Problem Title
SIH 1710: Enhancing Navigation for Railway Station Facilities and Locations
## Problem Description
Background: Railway stations are complex environments with numerous facilities and locations such as ticket counters, platforms, restrooms, food courts, and waiting areas. Passengers often face difficulties in navigating these spaces, especially in large or unfamiliar stations. Efficient and user-friendly navigation systems are crucial for improving passenger experience, reducing congestion, and ensuring timely travel connections. Description: The problem involves developing a comprehensive navigation solution for railway stations that assists passengers in locating various facilities and destinations within the station premises. This includes creating detailed maps, providing real-time directions, and integrating features such as accessibility options for individuals with disabilities. The solution should be intuitive, easy to use, and accessible via multiple platforms, including mobile devices and digital kiosks. Key challenges include updating navigation information in real-time, ensuring accuracy, and accommodating the diverse needs of all passengers. Expected Solution: The expected solution is a multi-platform navigation system that provides detailed, real-time directions to all facilities and locations within a railway station. This system should include: A mobile application with 3D interactive maps and step-by-step navigation. Digital kiosks located throughout the station with touch-screen interfaces. Voice-guided navigation for visually impaired passengers. Regular updates to reflect changes in station layout and facility locations. Integration with existing railway apps and services for seamless user experience. The solution should enhance the overall passenger experience by reducing confusion, saving time, and improving accessibility within the station.

## Problem Creater's Organization
Ministry of Railway

## Idea

Provide an integrated navigation experience inside railway stations to: reduce passenger confusion, speed up transfers, lower congestion, and improve accessibility for users with special needs. 

Core features:

1. 3D & 2D interactive maps with floor-by-floor views

2. Indoor positioning (BLE beacons, Wi‑Fi RTT, or visual markers) for real-time localization

3. Turn-by-turn pedestrian navigation (walking routes, escalator/elevator guidance)

4. Voice guidance and high-contrast UI for accessibility

5. Digital kiosks for on-site lookup and printing route receipts/QR codes

6. Admin tools for editing maps, pushing temporary changes (construction, platform changes)

7. Integration with timetable, platform allocation, and ticketing services

## Proposed Solution / Architecture Diagram

High-level Components

1.Client Layer

a. Mobile App (iOS, Android)

b. Web App (progressive web app for kiosks)

c. Digital Kiosks (touchscreen web app)

d. Accessibility Voice Module (TTS & ASR integrated)

2. Location & Sensing Layer

a. Indoor Positioning Service (combines BLE beacons, Wi-Fi RTT, Bluetooth Low Energy, inertial dead-reckoning, and optional computer-vision markers)

b. Map & Geometry Engine (vector tile server containing floorplans, POIs, routing graph)

3. Backend Services

a. Routing Engine (fast pedestrian routing on the station graph)

b. Map CMS & Versioning (admin UI for map edits, scheduled updates)

c. Real-time Events Bus (platform changes, closures, announcements)

d. Integration API Layer (connectors for timetable, platform assignment, ticketing)

e. Analytics & Monitoring (usage, congestion heatmaps)

4. Data Store & Infrastructure

a. Vector tile store and map DB (PostGIS + vector tiles)

b. Time-series DB for sensor telemetry

c. Caching & CDN for tiles and static assets

d. Authentication & Authorization (SSO for staff/admins)

5. Edge & On-prem

a. Local positioning gateway (aggregates beacons/Wi-Fi, provides low-latency location on-premises)

b. On-site kiosk host (optionally runs a local PWA with fallback if internet is down)

6. Security & Privacy

a. Encryption in transit (TLS) and at rest

b. Opt-in location sharing, minimal PII storage
## Use Cases
1. Find nearest restroom — User taps “Restroom” → app shows nearest on current floor, provides step-by-step route.

2. Platform transfer with tight connection — User requests fastest route from arrival platform to departure platform; system recommends fastest path (including elevators/escalators), estimated walking time, and alternate gates.

3. Accessibility mode — Route that avoids stairs and uses elevators/ramps; voice-guided directions and large-text UI.

4. Kiosk quick lookup — Walk-up kiosk prints a QR with route or sends it to user’s phone via SMS/QR code.

5. Temporary closure — Admin marks corridor closed; system recalculates routes and pushes notifications to affected users.

6. Crowd-avoidance routing — Uses live congestion heatmaps to route users through less crowded paths.

7. Integration with timetable — If platform is re-assigned, system sends updates and alternate routes.


## Technology Stack

1. Mobile: React Native or Flutter (single codebase for iOS & Android)

2. Kiosk/Web: Progressive Web App (React) with offline caching

3. Backend: Node.js (Express) or Go for low-latency routing APIs

4. Routing Engine: Custom routing on top of spatial DB (PostGIS) or Valhalla/OSRM adapted for indoor graphs

5. Indoor Positioning: BLE beacon controllers, Wi-Fi RTT, and optional AR/vision SDK (OpenCV/ARCore/ARKit)

6. Map Tiles & Storage: PostGIS + TileServer GL / Mapbox Vector Tiles

7. Real-time: WebSocket / MQTT bus for event propagation

8. Database: PostgreSQL + PostGIS; Redis for caching; InfluxDB/Timescale for telemetry

9.  Hosting: Kubernetes; CDN for static assets

10. Authentication: OAuth2 / SAML for staff; JWT for app clients

11. Accessibility: TTS (Google/Apple) for voice guidance; comply WCAG 2.1 AA


## Dependencies
1. On-site hardware: BLE beacons, Wi-Fi RTT infrastructure, kiosk touchscreens

2. Railway data feeds: timetable, real-time platform allocation, announcement feed

3. 3rd-party services (optional): cloud TTS/ASR, mapping provider, push notification service

4. Regulatory: accessibility compliance and data protection laws
