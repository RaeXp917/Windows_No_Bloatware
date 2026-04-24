### **STEP 0 OS AND RUFUS INSTALLATION (SKIP IF U HAVE THEM) **

1. ISO Preparation
 
    [Massgrave Windows LTSC Links](https://massgrave.dev/windows_ltsc_links.html#win11-iot-enterprise-ltsc-2024)

    Target File: en-us_windows_11_iot_enterprise_ltsc_2024_x64_dvd_f6b14814.iso

    Verification: This ISO contains 3 editions. Select **Index 2 during Installation** For details go **3. OS Installation**

2. Rufus Setup

   [Rufus Official Site](https://rufus.ie/en/)

    Select USB and ISO in Rufus.

	Leave settings at default and click START.

    START POPUP check these boxes in the popup:

        Remove requirement for 4GB+ RAM, Secure Boot and TPM 2.0

        Remove requirement for an online Microsoft account

        Disable data collection (Skip privacy questions)

        Disable BitLocker automatic device encryption (if you dont need it)

3. OS Installation

    BIOS: Set your USB Flash Drive as Priority 1 in Boot Order.
   
   Edition Selection: When the list of versions appears, select:
   **Windows 11 IoT Enterprise LTSC (This is Index 2)**

    No Internet: Do not connect to Wi-Fi/Ethernet during setup. This ensures a clean Local Account creation.

---

### **STEP 1: WIN ACTIVATE AND PROGGRAMS**

Click the Start Menu, type PowerShell, and Run as Administrator.
Copy and paste the code below and press Enter:
```
irm https://get.activated.win | iex
```
What this can activate:

Windows: All versions (10, 11, Home, Pro, Enterprise, LTSC, and even old ones like 7/8/Server).
Microsoft Office: All versions (365, 2024, 2021, 2019, 2016, etc.).
Visual Studio: Professional and Enterprise editions.
Windows Server: All editions including Server 2025 and RDS CALs.

---

### **STEP 2: CHAD CHRISTITUS TOOL**

## WinUtil (Chris Titus Tech)

**This uses WinUtil by Chris Titus Tech.**

[Chris Titus Official Site](https://christitus.com/)
[Chris Titus Repo](https://github.com/ChrisTitusTech/winutil) 

**All credit for the tool goes to Chris Titus Tech**

Run in PowerShell (Admin):
```
irm christitus.com/win | iex
```
TWEAKS TAB:

Click "Standard" button.

    In "Essential Tweaks", make sure "Disable Hibernation" is ON.

    In "Advanced Tweaks", turn these ON:

        Remove OneDrive
        Remove Microsoft Edge
        Remove Microsoft Copilot
        Disable Background App
        Remove Xbox & Gaming Components

    Click "Run Tweaks".

CONFIG TAB:

	Fixes SUBTAB
	
    Click "Set Up Autologin" (Username: your name, Password: leave blank).
    Click "System Corruption Scan".

UPDATES TAB:

    Click "Security (Recommended)".

---

## **STEP 3: REGISTRY - KILL ONLINE ACCOUNT NAGS & PASSWORD**

*Run in PowerShell (Admin) to automate the Registry keys:*

```
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\CloudContent" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\CloudContent" -Name "DisableCloudOptimizedContent" -Value 1
New-Item -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\UserProfileEngagement" -Force
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\UserProfileEngagement" -Name "ScoobeSystemSettingEnabled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PasswordLess\Device" -Name "DevicePasswordLessBuildVersion" -Value 0
```

*Manual Action for Autologin:*
1. Press `Win + R`, type `netplwiz`.
2. Uncheck **"Users must enter a user name and password..."**
3. Click Apply, leave password fields blank, and click OK.


If you see a gray box outline when moving windows and want it to look normal:

Press Win + R → type sysdm.cpl
Advanced Tab → Performance Settings.
CHECK the box: Show window contents while dragging.

---

## **OPTIONAL: INSTALL MICROSOFT STORE**

Run this in PowerShell (Admin):
```
wsreset -i
```
Wait about 2 to 5 minutes, and the Microsoft Store icon will suddenly appear in your Start Menu.

---

## ** (OPTIONAL) REMOVE XBOX OVERLAY & "MS-GAMINGOVERLAY" POPUP**

If you used the "Remove Xbox & Gaming Components" tweak in WinUtil, you might start getting an annoying popup saying: *"You'll need a new app to open this ms-gamingoverlay link"* every time you launch a game. 

WinUtil deletes the Xbox app but forgets to delete the registry triggers. To permanently kill the popup, run this in PowerShell (Admin):

```
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\GameDVR" /v "AppCaptureEnabled" /t REG_DWORD /d 0 /f
reg add "HKCU\System\GameConfigStore" /v "GameDVR_Enabled" /t REG_DWORD /d 0 /f
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\GameDVR" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\GameDVR" -Name "AllowGameDVR" -Value 0
```

**Why this happened:** Windows 11 treats the "Xbox Game Bar" as a system protocol.

---

## **HDD OPTIMIZATIONS (CRITICAL FOR HDDs WINDOWS INSTALL — SKIP IF YOU USE AN SSD)**

Run the following commands in PowerShell (Administrator) to reduce unnecessary disk activity (“thrashing”) on traditional hard drives:

```
Stop-Service -Name "SysMain"; Set-Service -Name "SysMain" -StartupType Disabled
Stop-Service -Name "DiagTrack"; Set-Service -Name "DiagTrack" -StartupType Disabled
Stop-Service -Name "WSearch"; Set-Service -Name "WSearch" -StartupType Disabled
```

**SysMain: Stops background disk thrashing.
**DiagTrack: Blocks useless data collection.
**WSearch: Stops continuous disk scanning.

**Sidenote on WSearch:**
Just use **Everything**. It is plain better, faster, and more precise than the built-in Windows Search.

---

## ** (OPTIONAL) SEARCH REPLACEMENT EVERYTHING**

* [Official Site Everything](https://www.voidtools.com/)

-cons a simple exe instead of build in searchbar

---

### ** (OPTIONAL) BULK PROGRAM INSTALLER NINITE**

If there are any essential programs you need that weren't included in the WinUtil tool, you can easily install them all at once using Ninite.

* [Ninite's Official Website](https://ninite.com/)

---

### **OPTIONAL LIGHTWEIGHT DISCORD CLIENTS**

## **Dorion (The "Ultra-Light" Pick)**

* [Visit Dorion's Website](https://spikehd.dev/projects/dorion/)
* [View Dorion on GitHub](https://github.com/SpikeHD/Dorion)

Built with Rust/Tauri. Extremely small and fast.

on release v6.12.2 (atm screensharing is the heavy part idk if its gonna change in the feature)

Pros: Tiny install size (~10MB). Uses your system's webview to save RAM.
Cons: Can be "heavy" on CPU/GPU specifically during high-quality streaming (Screen Share).

Plugins supported Vencord/Equicord	

Vencord Built-in

**Vencord**
	[GitHub](https://github.com/Vendicated/Vencord)
	[Support Vendicated](https://ko-fi.com/vendicated)

**Equicord**
	[GitHub](https://github.com/Equicord/Equicord) 
	[Website](https://equicord.org/)

## Legcord **(lighter Discord client with added privacy)**

* [Visit Legcord's Website](https://legcord.app/)
* [View Legcord on GitHub](https://github.com/Legcord/Legcord)
  

A solid all-around alternative focused on better performance and built-in enhancements.

Pros: Uses ~200MB less RAM than standard Discord. Vencord comes pre-installed by default.

Cons: (Current Known Issues on v1.2.4): not global keybinds working + no custom keybinds atm
Default Shortcuts: Currently uses Ctrl + Shift + D for Deafen. (on focused window)

Plugins Vencord Built-in

**Vencord**
	[GitHub](https://github.com/Vendicated/Vencord)
	[Support Vendicated](https://ko-fi.com/vendicated)

---

##  **(OPTIONAL) DISCORD RECC PLUGINS FOR BEING LIGHTWEIGHT**

PLUGINS TO ENABLE:

    NoTypingAnimation: Stops CPU-heavy dots.
    NoProfileThemes: Saves RAM, loads faster.
    NoOnboardingDelay: Skips slow intro animations.
    NoMosaic: Simplifies image rendering layout.
    YoutubeAdblock: Stops heavy video ads. (questionable)
    BetterSettings: Instant menus, zero lag.
    IgnoreActivities: Stops background UI updates.
    ConsoleJanitor: Saves RAM from waste.
    NoPendingCount: Reduces UI redraw work.
    NoSystemBadge: Saves CPU, less updates.
    NoDevtoolsWarning: Removes useless screen clutter.
    NoBlockedMessages: Fewer items to render.

APP SETTINGS:
    Hardware Acceleration: ON. Keeps CPU usage low.

and lastly use Discord official themes (for performance)

---

## **DISCLAIMER**
This repository is for **documentation purposes only**. I do not own any of the tools mentioned in this guide, nor do I take any responsibility for their use, potential system instability, or how you choose to apply these tweaks. Use them at your own risk.

---

### **CREDITS & SUPPORT**

This guide utilizes several amazing open-source projects. Please consider supporting the original creators:

* **Microsoft Activation Scripts (MAS)**
    * [GitHub](https://github.com/massgravel/Microsoft-Activation-Scripts) | [Official Website / Credits](https://massgrave.dev/)
* **Chris Titus Tech (WinUtil)**
    *  [Oficial Site](https://christitus.com) | [GitHub](https://github.com/ChrisTitusTech/winutil) | [Patreon](https://www.patreon.com/christitustech)
* **Ninite**
    * [Official Website](https://ninite.com/)
* **Everything**

	*[Official Site](https://www.voidtools.com/) | [Support](https://www.voidtools.com/donate)
* **Equicord**
    * [GitHub](https://github.com/Equicord/Equicord) | [Official Website](https://equicord.org/)
* **Dorion (by SpikeHD)**
    * [GitHub](https://github.com/SpikeHD/Dorion)
* **Legcord**
    * [GitHub](https://github.com/Legcord/Legcord) | [Sponsor on GitHub](https://github.com/sponsors/smartfrigde)
* **Vencord**
    * [GitHub](https://github.com/Vendicated/Vencord) | [Support Vendicated (Ko-fi)](https://ko-fi.com/vendicated)


**All credit goes to the talented developers linked above.**
