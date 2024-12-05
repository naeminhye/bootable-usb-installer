# Install macOS by Bootable USB Installer
Here’s a step-by-step guide to install macOS using a bootable USB

---

### **1. Prepare the Bootable USB Installer**
1. **Download macOS Installer**:
   - Open the **App Store** or visit [Apple's support page](https://support.apple.com/downloads) to download the macOS version you want to install.
   - Ensure the installer is in the **Applications** folder.

2. **Format the USB Drive**:
   - Connect a USB drive (16GB or larger) to your Mac.
   - Open **Disk Utility** (Applications > Utilities).
   - **View All Devices**:
     - Click **View** in the top-left corner of Disk Utility and select **Show All Devices**.
     - Select the **entire USB device** (not just a partition under it).
   - Click **Erase**, then set:
     - **Name**: Any name, e.g., `USBInstaller`.
     - **Format**: `Mac OS Extended (Journaled)` or `APFS`.
     - **Scheme**: `GUID Partition Map`.
   - Click **Erase** to confirm.

3. **Create the Bootable USB**:
   - Open **Terminal** and enter the following command, depending on your macOS version (replace `<macOSVersion>` with the specific version, e.g., `Ventura`):
     ```bash
     sudo /Applications/Install\ macOS\ <macOSVersion>.app/Contents/Resources/createinstallmedia --volume /Volumes/USBInstaller
     ```
   - Enter your admin password when prompted and press `Y` to confirm.
   - Wait for the process to complete.

---

### **2. Boot from the USB**
1. **Restart Your Mac**:
   - **Intel Mac**: Hold **Option (⌥)** as it starts.
   - **Apple Silicon Mac (M1/M2)**: Hold the **Power button** until the “Options” screen appears.

2. **Select the USB Drive**:
   - Choose the USB installer from the list of startup disks and press **Enter**.

---

### **3. Erase the Existing macOS Installation (Optional for a Clean Install)**
1. In the **macOS Utilities** screen, open **Disk Utility**.
2. **View All Devices** again:
   - Click **View** > **Show All Devices** to display all connected drives.
   - Select the **internal drive** (usually labeled as the device name, not the partition).
3. **Erase the Disk**:
   - Click **Erase** and set:
     - **Name**: `Macintosh HD`.
     - **Format**: `APFS` (for modern macOS) or `Mac OS Extended (Journaled)` (for older macOS).
   - Click **Erase** to confirm.

4. Close **Disk Utility** and return to the macOS Utilities screen.

---

### **4. Install macOS**
1. Select **Install macOS** from the macOS Utilities menu.
2. Follow the on-screen instructions to install macOS on your internal drive.
3. Wait for the installation to complete. Your Mac will restart automatically.

---

### **5. Restore Data (Optional)**
- If you have a **Time Machine backup**, you can restore your data during the macOS setup process.

---

### **Troubleshooting Tips**
1. **If the USB doesn’t appear in the boot menu**:
   - Ensure the USB was created correctly.
   - Try recreating the USB following the steps above.

2. **If you see "This copy of the macOS installer is damaged"**:
   - Set your Mac’s date to a past time using Terminal:
     ```bash
     date MMDDHHmmYY
     ```
     Example: To set August 1, 2023, use:
     ```bash
     date 0801000023
     ```

3. **Firmware Incompatibility**:
   - Ensure the macOS version is compatible with your Mac.
   - You cannot install a version older than the one originally shipped with your Mac.
