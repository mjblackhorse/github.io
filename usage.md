This page describes how to deploy and run GridDroid

## Environment requirement

* Operating System: Window 10 (evaluated)
* Java SDK: 1.8.0_281 (evaluated)
* Android SDK (evaluated):
  * build-tools: 26.0.2
* Apache-ant: 1.10.11 (evaluated)
* Emulator: 
  * Genymotion, version 3.2.0 (evaluated)
  


## Run GridDroid

### **Step-1**: Download and unzip the [GridDroid.jar](https://drive.google.com/file/d/136mLy5osarexJYg-Jln-RaB5TEvPBvfw/view?usp=sharing)

### **Step-2**: Generate birthmark
* Create an AVD via Genymotion
  * AVD Settings (evaluated)
    * Custom Phone
    * Android API: 6.0 API 23
    * Size: 480
    * Density: 160-MDPI
    * Procesors: 4
    * Memeory Size: 2048 MB
    * Network: NAT (some app require internet access)
    * Turn off window animation, transition animation and animation duration in the "Developer options"
    * To run ARM apps, please install [Genymotion-ARM-Translation](https://github.com/m9rco/Genymotion_ARM_Translation)
* Backup fresh AVD
  * Open the deploy directory of Genymotion (e.g., `C:\Users\username\AppData\Local\Genymobile\Genymotion\deployed`)
  * 
