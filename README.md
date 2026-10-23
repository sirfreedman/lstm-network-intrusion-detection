## 📝 Project Document: Intrusion Detection with Deep LSTM Networks

### Overview
This project implements a state-of-the-art sequential Deep Learning pipeline using **Long Short-Term Memory (LSTM)** neural networks to identify cyberattack vectors from raw network packet flows. Using data from the **CSE-CIC-IDS2018** collection, we compare benign background profiles against simulated malicious intrusions.


> ⚠️ **Dataset File Size Notice:** Since the raw network traffic PCAP-to-CSV dataset files (like `friday.csv`) are extremely large and exceed Git/GitHub's storage limits, they could not be committed directly to the GitHub repository folder. Users should download the source ZIP archives (`friday.csv.zip`), unzip them separately, and place them in the `/content` working directory before running this notebook.

### Pipeline Architectural Engineering
1. **Extraction & Adaptive Ingestion:** Streams structured flows incrementally to preserve memory constraints.
2. **Feature Sanitization:** Drops non-behavioral tracking flags (`Flow ID`, `IPs`, `Timestamps`) and rectifies mathematical float singularities (infinities/null values).
3. **Dimensional Scaling:** Fits features to standard bounded intervals $[0, 1]$ via MinMaxScaler to assure mathematical uniformity.
4. **3D Chronological Window Sequence:** Binds isolated packet signals into coherent time-series tensors representing sequential traffic flows.
5. **Deep Regularized LSTM:** Employs gated units and dropout safety nets to uncover time-dependent patterns without overfitting.