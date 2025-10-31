# Autonomous C-UAS Drone Defense: 
Real-Time Multi-Target Tracking & Proximity-Optimized Interceptor Command

## 🎯 Project Overview
This project presents a **Counter-Unmanned Aerial System (C-UAS)** simulation written in Python, focusing on **real-time state estimation** and **optimized resource allocation** to defend a high-value asset.

The simulation models hostile drones (UAS/drones) attempting to penetrate a No-Engagement Zone (NEZ). The defense system employs multiple sensors and **Kalman Filters (KF)** for multi-target tracking, deploying high-speed interceptors based on a critical **proximity-prioritized** targeting logic.

### Key Technical Features
* **Kalman Filter (KF) Tracking:** Implements a Constant Velocity (CV) KF for robust, low-latency tracking and prediction of hostile drone positions.
* **Multi-Sensor Data Fusion:** Simulates detections from multiple, dispersed radar and camera nodes.
* **Proximity-Prioritized Interception:** Interceptors are dynamically assigned to the hostile track posing the **greatest and most imminent threat** (i.e., the drone closest to the Protected Area/NEZ center).
* **Target Kill-Chain Closure:** Includes logic for interceptor movement, target elimination, and subsequent recycling of interceptors and KF resources.
* **Detailed Visualization:** Real-time plot showing true targets (red dots), KF tracks (green crosses), interceptors (yellow triangles), and assignment links.

## 🛠️ Technology Stack
* **Language:** Python  
* **Libraries:** `numpy` (for vector math/matrices), `matplotlib` (for visualization), `filterpy` (for Kalman Filter implementation).

## 🚀 Getting Started

### Prerequisites
You need Python installed, along with the required libraries.

```bash
pip install numpy matplotlib filterpy
```

### Execution
1. Save the provided code into a file named `cuas_simulation.py`.
2. Run the simulation from your terminal:

```bash
python cuas_simulation.py
```

The simulation window will open, displaying the targets, trackers, and interceptors in real-time. The final performance statistics will be printed to the console upon completion or successful elimination of all threats.

## ⚙️ Simulation Parameters
You can adjust the parameters at the beginning of the script to test the system's resilience under different conditions:

| Parameter | Description | Default Value | Impact on Simulation |
| :--- | :--- | :--- | :--- |
| `SIM_TIME` | Total simulation duration (seconds). | `50` | Duration of the threat window. |
| `NUM_TARGETS_START`| Initial number of hostile drones. | `5` | Defines the initial threat level. |
| `INTERCEPTOR_SPEED`| Speed of the interceptors (m/s). | `150` | Crucial for mission success rate. |
| `KF.P` | Initial position covariance in `create_kf`. | `500` | Controls how quickly the KF locks onto a target. |
| `NEZ_CENTER` | The coordinate array for the center of the protected area. | `[500, 500]` | Defines the area targets are prioritized against. |

## 📊 Final Results Report
The simulation concludes with a detailed performance analysis:

```
==================================================
             🎯 SIMULATION RESULTS 🎯
==================================================
Total Hostile Targets: 5
Targets Eliminated (Killed): 5
Targets Survived (Remaining): 0

Defense Success Rate: 100.00%
==================================================
STATUS: 100% SUCCESS! All hostile targets were successfully eliminated! 🎉
```

## ⚠️ Penetration Warning
The system actively checks if a hostile target breaches the immediate **Protected Zone** (defined as a radius of 100m around `NEZ_CENTER`):

```
!!! WARNING: Hostile Target [ID] penetrated the Protected Area at time [t.s]s !!!
```

This ensures the simulation accurately accounts for mission failure even if the target is later killed.

---

## 🧾 License
This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

Created by **Khushi**  
© 2025
