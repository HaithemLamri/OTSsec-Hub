# Lab Assignment Setup Guide

## Summary

To complete the lab assignments, install the following applications on a Windows PC (or VM) with 40GB free space:

### **MATLAB, Simulink & Simulink PLC Coder**
- Download MATLAB from [NYU Software Library](https://www.nyu.edu/life/information-technology/computing-support/software/software/matlab.html).
- Use your NYU email to create an account.
- During installation, select **Simulink** and **Simulink PLC Coder**.

### **CODESYS 3.5.17.0**
- Create an **Individual Customer Account** at [CODESYS Store](https://us.store.codesys.com/).
- Download **32-bit version** of **3.5.17.0** from the **Versions tab**.
- Accept terms and install using the **Complete** setup.

### **Wireshark**
- Download the latest stable version from [Wireshark](https://www.wireshark.org/).

---

## **Automated Installation (Python Script)**
This script downloads and installs **Wireshark** automatically.  
MATLAB and CODESYS require manual login, so follow the instructions above.

```python
import os
import requests

# URLs for downloads
codesys_url = "https://us.store.codesys.com/"
wireshark_url = "https://www.wireshark.org/download.html"

# Download and install CODESYS (manual login required)
print("Please log in and download CODESYS 3.5.17.0 (32-bit) from:", codesys_url)

# Download Wireshark installer
print("Downloading Wireshark...")
wireshark_installer = "Wireshark.exe"
wireshark_download = requests.get("https://www.wireshark.org/download/Wireshark-latest.exe", stream=True)

with open(wireshark_installer, "wb") as f:
    for chunk in wireshark_download.iter_content(chunk_size=1024):
        if chunk:
            f.write(chunk)

# Install Wireshark
print("Installing Wireshark...")
os.system(f"{wireshark_installer} /S")

print("Installation process completed. Ensure MATLAB and CODESYS are installed manually.")
