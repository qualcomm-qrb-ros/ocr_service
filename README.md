
### 🚀 ocr_service User Guide

Welcome to the **OCR Service User Guide**!  
This document provides detailed instructions on how to install, configure, run, and build the OCR Service on your device.

---

### 📌 Overview

This guide covers:

- Service definitions, inputs, and outputs  
- Installing the Debian package & dependencies via Ubuntu PPA  
- Running project executables  
- Building the project from source  

---

### 🧩 Service Architecture

#### 📥 Client

| Input                                   | Output                                                         |
| --------------------------------------- | -------------------------------------------------------------- |
| Topic name: Image topic (String)        | Topic name: OCR result (String)<br>OCR request status: Bool    |

#### 🖥️ Server & Process Node

| Input                       | Output                 |
| --------------------------- | ---------------------- |
| Topic: `sensor_msgs/Image`  | Topic: `std_msgs/String` |

#### 🧪 Test Node

| Input                                                         | Output                      |
| ------------------------------------------------------------- | --------------------------- |
| String: image topic name <br> String: picture path            | Topic: `sensor_msgs/Image`  |

---

### 📨 Service Message

#### `ocr_service::ocr_msg::OcrRequest`

```
string image_topic_name
---
string ocr_topic_name
bool success
```

---

### 🛠️ Installation

#### Add Qualcomm IoT PPA for Ubuntu

```bash
sudo add-apt-repository ppa:ubuntu-qcom-iot/qcom-ppa
sudo add-apt-repository ppa:ubuntu-qcom-iot/qirp
sudo apt update
```

#### Install Debian Package

```bash
sudo apt install ros-jazzy-ocr-service
```

#### Install Python Dependencies

```bash
pip3 install pytesseract
```

---

### ▶️ Usage

```bash
# Terminal 1: launch ocr_server
export HOME=/home
source /opt/ros/jazzy/setup.bash
ros2 run ocr_service ocr_server
```

```bash
# Terminal 2: launch ocr_testnode
export HOME=/home
source /opt/ros/jazzy/setup.sh
ros2 run ocr_service ocr_testnode --topic <image_topic> --picture <image_path>
```

```bash
# Terminal 3: launch ocr_client
export HOME=/home
source /opt/ros/jazzy/setup.sh
ros2 run ocr_service ocr_client <image_topic>
```

---

### 🧱 Build From Source

#### Dependencies

```bash
apt install ros-jazzy-example-interfaces ros-jazzy-ocr-msg python3-setuptools
```

#### Build OCR_Service

```bash
git clone https://github.com/qualcomm-qrb-ros/ocr_service.git
colcon build
```

---

### 📄 License

This project is licensed under the **BSD 3-Clause-Clear (“New” or “Revised”) License**.
