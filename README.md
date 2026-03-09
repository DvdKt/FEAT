# Werkzeugerkennung

An integrated mobile-to-backend solution for tool recognition using Android (Kotlin), Python (Chaquopy), and PyTorch (FEAT), made by the WZL institute at RWTH Aachen.

-------------------------------------
*****Vision*****

Bridge high-performance deep learning backends with mobile accessibility. This project enables real-time tool recognition by embedding a local Python environment within Android while supporting a remote, robust inference backend.

-------------------------------------
*****Key Features*****

- Hybrid Integration: Kotlin-based Android app with local Python execution via Chaquopy.
- Seamless Connectivity: Direct communication between the mobile client and a Linux-based Python backend.
- Advanced AI Inference: Utilizes OG_FEAT (Few-Shot Embedding Adaptation Transformer) for high-accuracy recognition.
- Flexible Operation: Supports both Semi-Automatic (human-in-the-loop) and Full-Automatic inference modes.
- Customizable Logic: Granular control over confidence thresholds (T_CONF) and prediction margins (T_MARGIN).

-------------------------------------
*****QUICK START*****

Prerequisites:
- Backend: Linux environment with Python 3.x.
- Mobile: Android device or emulator (API level support for Chaquopy).
- Network: Both the server (e.g., Mac/PC) and the tablet must be on the same Wi-Fi network.

Installation:
1. Clone the repository using: git clone <repo_url>
2. Initialize the backend using the install_linux.sh script
3. Run the back end server using the run_backend_linux.sh script

-------------------------------------
*****ANDROID CONFIGURATION*****

Backend connection:
1. Navigate to the session screen in the app.
2. Set the Backend base URL to the address printed during the backend startup.
   Default Emulator URL: https://10.0.2.2:8000

Pro tip: "If the app cannot connect, use ADB in your terminal to route the traffic:
   adb reverse tcp:8000 tcp:8000

-------------------------------------
Configuration and enviroments:
Manage your setup via the backend/.env file.

***Hybrid Integration:*** Kotlin-based Android app with local Python execution via Chaquopy.
***Seamless Connectivity:*** Direct communication between the mobile client and a Linux-based Python backend.
***Advanced AI Inference:*** Utilizes OG_FEAT (Few-Shot Embedding Adaptation Transformer) for high-accuracy recognition.
***Flexible Operation:*** Supports both Semi-Automatic (human-in-the-loop) and Full-Automatic inference modes.
***Customizable Logic:*** Granular control over confidence thresholds (T_CONF) and prediction margins (T_MARGIN).

-------------------------------------
*****OG_FEAT Model Setup*****

The pretrained weights (feat-5-shot.pth) are reqired but not tracked in git.
Download the file from https://github.com/Sha-Lab/FEAT and update OG_FEAT_INIT_WEIGHTS in your .env to the absolute path of the file.

-------------------------------------
*****Inference Modes*****

- Semi-Automatic: Every prediction requires manual confirmation before saving (env_code=PostTraining).
- Full-Automatic: High-confidence predictions save automatically; low-confidence ones prompt for correction.

-------------------------------------
**Troubleshooting:**
- Firewall Issues: Ensure your OS allows incoming connections for Python/Uvicorn.
- 127.0.0.1 Error: If the script prints a loopback address, find your LAN IP manually (e.g., ipconfig getifaddr en0).
- Port Conflicts: If 8000 is in use, modify BACKEND_PORT in .env and restart the backend.
- PyTorch Training: Training via og_feat_trainer.py requires a desktop environment; PyTorch is not bundled for local Android training.
