Here is a **clean + complete + ready-to-run** command script that installs EVERYTHING you need for Flutter Android development **WITHOUT Android Studio**, using ONLY command-line tools.

⚡ Works on Windows CMD or PowerShell  
⚡ Includes Java, SDK, Platform Tools, Build Tools, Emulator, System Images  
⚡ Includes AVD creation + launch

* * *

✅ **FULL INSTALL SCRIPT (COPY–PASTE & RUN STEP BY STEP)**
=========================================================

_(Replace paths only if needed)_

* * *

🔵 **1\. Install Java JDK 17 (with winget)**
============================================

    winget install -e --id Microsoft.OpenJDK.17
    

Set JAVA\_HOME:

    setx JAVA_HOME "C:\Program Files\Microsoft\jdk-17"
    setx PATH "%PATH%;C:\Program Files\Microsoft\jdk-17\bin"
    

Verify:

    java -version
    

* * *

🔵 **2\. Create Android SDK folders**
=====================================

    mkdir C:\Android\Sdk
    mkdir C:\Android\Sdk\cmdline-tools
    mkdir C:\Android\Sdk\cmdline-tools\latest
    

* * *

🔵 **3\. Download Commandline Tools (MANUALLY)**
================================================

Download ZIP here:  
👉 https://developer.android.com/studio#command-tools

Extract ZIP → Put contents into:

    C:\Android\Sdk\cmdline-tools\latest
    

* * *

🔵 **4\. Add Android SDK to PATH**
==================================

    setx PATH "%PATH%;C:\Android\Sdk\cmdline-tools\latest\bin;C:\Android\Sdk\platform-tools;C:\Android\Sdk\emulator"
    

Restart CMD afterwards.

* * *

🔵 **5\. Install SDK components (Platform-tools, Build-tools, Platform 36)**
============================================================================

### Install platform tools:

    sdkmanager --sdk_root="C:\Android\Sdk" --install "platform-tools"
    

### Install build tools:

    sdkmanager --sdk_root="C:\Android\Sdk" --install "build-tools;28.0.3"
    

### Install Android API 36 (Required by Flutter)

    sdkmanager --sdk_root="C:\Android\Sdk" --install "platforms;android-36"
    

* * *

🔵 **6\. Install Emulator + System Image**
==========================================

### Install the emulator:

    sdkmanager --sdk_root="C:\Android\Sdk" --install "emulator"
    

### Install Android System Image (API 34 Google APIs x86\_64)

    sdkmanager --sdk_root="C:\Android\Sdk" --install "system-images;android-34;google_apis;x86_64"
    

You can also use API 36:

    sdkmanager --sdk_root="C:\Android\Sdk" --install "system-images;android-36;google_apis;x86_64"
    

* * *

🔵 **7\. Accept all licenses**
==============================

    yes | sdkmanager --sdk_root="C:\Android\Sdk" --licenses
    

* * *

🔵 **8\. Create a Virtual Device (AVD)**
========================================

List available device models:

    avdmanager list devices
    

Create AVD (Pixel 5 recommended):

    avdmanager create avd -n Pixel5 -k "system-images;android-34;google_apis;x86_64" --device "pixel_5"
    

For API 36:

    avdmanager create avd -n Pixel5 -k "system-images;android-36;google_apis;x86_64" --device "pixel_5"
    

* * *

🔵 **9\. Start Emulator**
=========================

    emulator -avd Pixel5
    

Optional fast mode:

    emulator -avd Pixel5 -gpu auto -netdelay none -netspeed full
    

* * *

🔵 **10\. Configure Flutter to use SDK**
========================================

    flutter config --android-sdk "C:\Android\Sdk"
    

Check:

    flutter doctor
    

* * *

🎉 DONE — Your Android environment is 100% installed

