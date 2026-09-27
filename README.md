# Sentinel

> An edge-based IoT security service for monitoring device behaviour,
> detecting anomalous network activity, assigning risk, and triggering
> automated security responses.

Sentinel combines Raspberry Pi-based network infrastructure,
DNS-level telemetry, behavioural analysis, machine learning,
and real-time monitoring to provide a security layer for IoT
networks.

## Overview

IoT devices often operate with limited computational resources
and may communicate with external services without providing
users with meaningful visibility into their network behaviour.

Sentinel addresses this problem by moving security monitoring
to the network edge.

Instead of relying only on static blocklists, Sentinel observes
the behavioural patterns of IoT devices and identifies deviations
that may indicate suspicious activity.

##Architecture 

IoT Device
    │
    ▼
Raspberry Pi
    │
    ├── Pi-hole
    │      │
    │      └── DNS filtering
    │
    ├── Unbound
    │      │
    │      └── Recursive DNS
    │
    ▼
Telemetry Collector
    │
    ▼
Feature Extraction
    │
    ▼
ML Detection Engine
    │
    ▼
Risk Engine
    │
    ├───────────────┐
    ▼               ▼
Dashboard       Response Engine
                    │
                    ▼
             Block / Alert /
               Quarantine

## Features

- IoT device discovery and monitoring
- DNS traffic monitoring
- Real-time DNS telemetry collection
- Device behavioural profiling
- Behavioural anomaly detection
- ML-based risk classification
- Risk scoring
- Suspicious-domain detection
- DNS-level blocking
- Real-time security dashboard
- Security event visualization
- Automated security response
- Raspberry Pi edge deployment
- Tailscale-based remote access
- ESP32/Arduino security demonstration

## Detection Engine
  
Raw DNS Events
      ↓
Feature Extraction
      ↓
Behavioural Features
      ↓
ML Model
      ↓
Risk Score
      ↓
Security Decision

## Detection Scenarios

  ### Normal Behaviour
  
  An IoT device communicates with its known services
  at a relatively stable frequency.
  
  Sentinel establishes this as the device's baseline.

  ### Behavioural Deviation
  
  The device suddenly:
  
  - contacts multiple previously unseen domains
  - generates a DNS request burst
  - performs repeated failed lookups
  - communicates during unusual periods
  
  Sentinel detects the deviation and increases the device risk.

  ### Response
  
  Depending on the configured policy:
  
  Normal
    → Allow
  
  Suspicious
    → Alert + Monitor
  
  High Risk
    → Block / Quarantine

 ## Hardware

- Raspberry Pi 4
- ESP32 / Arduino
- Network router
- IoT test devices

The Raspberry Pi acts as the network-edge security node. 

## Technology Stack

| Layer | Technology |
|---|---|
| Edge           | Raspberry Pi 4   |
| DNS Filtering  | Pi-hole          |
| DNS Resolution | Unbound          |
| Remote Access  | Tailscale        |
| Backend        | Python / FastAPI |
| ML             | Scikit-learn     |
| Database       | SQLite           |
| Frontend       | React / Vite     |
| Styling        | Tailwind CSS     |
| IoT            | ESP32 / Arduino  |

##Project Structure

  Sentinel/
  ├── backend/
  ├── dashboard/
  ├── detection/
  ├── collector/
  ├── edge/
  ├── iot/
  ├── models/
  ├── tests/
  ├── docs/
  ├── screenshots/
  ├── requirements.txt
  ├── docker-compose.yml
  └── README.md


## Installation

  ### Clone the repository
  
  git clone <your-repository-url>
  cd Sentinel
  
  ### Create environment
  
  python -m venv venv
  
  ### Activate environment
  
  Windows:
  
  venv\Scripts\activate
  
  Linux/macOS:
  
  source venv/bin/activate
  
  ### Install dependencies
  
  pip install -r requirements.txt
  
  ### Start the backend
  
  ### Start the dashboard
  
  ### Start the edge components


## Limitations

Sentinel primarily operates at the DNS and network-behaviour
layer.

Therefore, visibility can be reduced when devices use:

- Direct IP communication
- Encrypted DNS
- VPN tunnels
- Non-DNS protocols
- Application-layer communication that is not exposed
  through the monitored telemetry

## Future Improvements

- Packet-level traffic analysis
- Encrypted DNS visibility
- More advanced behavioural models
- Federated learning across IoT environments
- Automated device isolation
- Threat-intelligence integration
- Larger IoT behavioural datasets
- Adversarial robustness evaluation
