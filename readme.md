![CPAI Logo](https://physicalai.ca/assets/logo-cpai.png)

# SensorGuardian

_Offline ROS 2 sensor health diagnostics – an open-source project by the  [Canadian Physical AI Institute (CPAI)](https://physicalai.ca)._

---

## 🏛️ About CPAI

The Canadian Physical AI Institute (CPAI) is an open research initiative focused on the critical infrastructure, standards, and tools for robotics and physical AI.

---

## 🔍 Overview

**SensorGuardian** analyzes recorded robot sensor data to catch failures that often go unnoticed — until they cause critical malfunctions. It’s a lightweight ROS 2 tool that inspects your sensor streams (camera, LiDAR, IMU, etc.) for silent degradation, timing issues, and data dropouts.

It outputs reproducible reports with actionable insights — no dashboards, no AI, no guesswork.

---

## ⚙️ Tech Stack

- **Status:** Active Development (v0.1)
- **Languages:** C++17 core, Python 3 bindings 
- **Interface:** CLI + optional ROS 2 live node
- **Platform:** ROS 2 (Humble and later), Ubuntu 22.04+
- **License:** Apache 2.0

---

## ✨ Key Features

- 🧪 **Offline ROS 2 Bag Analysis**  
  Detects staleness, frequency drops, timestamp drift, NaNs, frozen streams, QoS mismatches, and more.

- 📉 **Trend Detection**  
  Flags degrading topics using rolling statistics and regression over time.

- 🧩 **User-Defined Severity & Logic**  
  Supports rules like:  
  - “2 of 3 IMUs must pass”  
  - “Downgrade stale if sensor is expected offline”  
  - Custom severity levels beyond OK/WARN/ERROR/STALE

- 📎 **Deterministic Reports**  
  Reproducible outputs in JSON and Markdown — same bag, same result.

- 🧰 **CLI + Python API**  
  Integrate into CI pipelines, dev notebooks, or incident workflows.

---

## 🚀 Quick Start

```bash
cd ~/ros2_ws/src
git clone https://github.com/physicalaica/sensor_guardian.git
cd ~/ros2_ws
colcon build --packages-select sensor_guardian
source install/setup.bash
```

### Analyze a bag

```bash
ros2 run sensor_guardian analyze --bag path/to/your.bag --output report.yaml
```

### Python API usage

```python
from sensor_guardian import analyze_bag
report = analyze_bag("path/to/bag")
print(report.summary)
report.save_markdown("report.md")
```

---

## 🛣️ Roadmap Highlights

- ✅ v0.1: Offline rosbag diagnostics (frozen, stale, jitter, QoS, trend)  
- 🔜 v0.2: ROS 2 live mode + diagnostics publisher  
- 🚧 vNext: `GuardedSubscriber<T>` contract model with runtime enforcement  

See roadmap: [Read more here](https://docs.google.com/document/d/1huaK7-_Q-QKykYOwJLPNI07FWMGsLoL46xFDk9lEn2s/edit?pli=1&tab=t.qo6tgieepjta#heading=h.2dn7fq2ccu5z)

---

## 🤝 Contributing

We welcome contributors!

- Browse [good first issues](https://github.com/physicalaica/sensor_guardian/issues)
- Follow the setup instructions above
- Ensure CI passes and tests are included

SensorGuardian is maintained under the [CPAI GitHub account](https://github.com/physicalaica).

---

## 📜 License

Apache License 2.0 — see [LICENSE](LICENSE)

---

_Made with ❤️ by the [Canadian Physical AI Institute (CPAI)](https://physicalai.ca)_
