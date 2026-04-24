### **STEP 1: WIN ACTIVATE AND PROGGRAMS**

Click the Start Menu, type PowerShell, and Run as Administrator.
Copy and paste the code below and press Enter:

irm https://get.activated.win | iex

What this can activate:

Windows: All versions (10, 11, Home, Pro, Enterprise, LTSC, and even old ones like 7/8/Server).
Microsoft Office: All versions (365, 2024, 2021, 2019, 2016, etc.).
Visual Studio: Professional and Enterprise editions.
Windows Server: All editions including Server 2025 and RDS CALs.

====================================================

### **STEP 2: CHAD CHRISTITUS TOOL**

## WinUtil (Chris Titus Tech)

This uses WinUtil by Chris Titus Tech.

Original:
https://github.com/ChrisTitusTech/winutil  
https://christitus.com/

All credit goes to Chris Titus Tech

Run in PowerShell (Admin):

irm christitus.com/win | iex

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

OPTIONAL: INSTALL MICROSOFT STORE

Run this in PowerShell (Admin):

wsreset -i

Wait about 2 to 5 minutes, and the Microsoft Store icon will suddenly appear in your Start Menu.

====================================================

### **STEP 3: REGISTRY - KILL ONLINE ACCOUNT NAGS & PASSWORD**

*Run in PowerShell (Admin) to automate the Registry keys:*

New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\CloudContent" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\CloudContent" -Name "DisableCloudOptimizedContent" -Value 1
New-Item -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\UserProfileEngagement" -Force
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\UserProfileEngagement" -Name "ScoobeSystemSettingEnabled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PasswordLess\Device" -Name "DevicePasswordLessBuildVersion" -Value 0

*Manual Action for Autologin:*
1. Press `Win + R`, type `netplwiz`.
2. Uncheck **"Users must enter a user name and password..."**
3. Click Apply, leave password fields blank, and click OK.

====================================================

If you see a gray box outline when moving windows and want it to look normal:

Press Win + R → type sysdm.cpl
Advanced Tab → Performance Settings.
CHECK the box: Show window contents while dragging.

====================================================

**HDD OPTIMIZATIONS (CRITICAL FOR HDDs WINDOWS INSTALL — SKIP IF YOU USE AN SSD)**

Run the following commands in PowerShell (Administrator) to reduce unnecessary disk activity (“thrashing”) on traditional hard drives:


Stop-Service -Name "SysMain"; Set-Service -Name "SysMain" -StartupType Disabled
Stop-Service -Name "DiagTrack"; Set-Service -Name "DiagTrack" -StartupType Disabled
Stop-Service -Name "WSearch"; Set-Service -Name "WSearch" -StartupType Disabled

**SysMain: Stops background disk thrashing.
**DiagTrack: Blocks useless data collection.
**WSearch: Stops continuous disk scanning.

**Sidenote on Wsearch**
	-Just use Everything is just plain better and faster and precise

https://www.voidtools.com/downloads/


====================================================

**OPTIONAL LIGHTWEIGHT DISCORD CLIENTS**

============ Dorion (The "Ultra-Light" Pick) ===================

Built with Rust/Tauri. Extremely small and fast.

Site: https://spikehd.dev/projects/dorion/
Github: https://github.com/SpikeHD/Dorion

on release v6.12.2 (atm screensharing is the heavy part idk if its gonna change in the feature)

Pros: Tiny install size (~10MB). Uses your system's webview to save RAM.
Cons: Can be "heavy" on CPU/GPU specifically during high-quality streaming (Screen Share).

Plugins supported Vencord/Equicord	

Vencord Built-in

============ Legcord (lighter Discord client with added privacy) =================

A solid all-around alternative focused on better performance and built-in enhancements.

Site: https://legcord.app/
Github: https://github.com/Legcord/Legcord

Pros: Uses ~200MB less RAM than standard Discord. Vencord comes pre-installed by default.

Cons: (Current Known Issues on v1.2.4): not global keybinds working + no custom keybinds atm
Default Shortcuts: Currently uses Ctrl + Shift + D for Deafen. (on focused window)

Plugins Vencord Built-in

================= (OPTIONAL) DISCORD RECC PLUGINS FOR BEING LIGHTWEIGHT=========================

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

and lastly use Discord themes not extras

========== (OPTIONAL BUT RECC) ==========

Once your Discord feels fast and perfect:

Go to Settings -> Vencord -> Backup & Restore.

Click Export and save the file. (is backup only for vencord! not disc settings overall)

====================================================

**If u want 2 custom themes**

Go to Settings -> Vencord -> TAB LOCAL THEMES -> SUBTAB FIND THEMES download and move it to the local vencord themes folder

OR use this that is simply dark and u can change fonts links etc colors

dark+theme.css (move it to download folders)

is a profile of other guy that i touched (i just made it a bit darker with red)

--darkplus-bg: #0b0b0b;  main/base background
--darkplus-bg2: #131313; secondary background
--darkplus-sec: #940000; (red) outlines, scrollbars, highlights
--darkplus-links: #940000; (red) link/fonts
