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
  * Open the deploy directory of Genymotion (e.g., `C:\Users\username\AppData\Local\Genymobile\Genymotion\deployed`). The path of the deploy directory can be found via clicking ``Genymotion->Settings->VirtualBox`` of the GUI of Genymotion.
  * Copy the directory of the created AVD to a location other than the deploy directory (e.g., `d:\AVDs\`).
* Download and edit the configuration file [bm_gen.properties](bm_gen.properties) accordingly. The parameters are:
  * `android_sdk_path`=E:\\IDE\\AndroidSDK\\SDK
  * `ant_root_path`=E:\\IDE\\apache-ant-1.10.11
  * `aapt_path`=E:\\IDE\\AndroidSDK\\SDK\\build-tools\\26.0.2\\aapt.exe
  * `genymotion_home` = C:\\Program Files\\Genymobile\\Genymotion\\
  * `vbox_home` = C:\\Program Files\\Oracle\\VirtualBox\\
  * `max_step`=1000
  * `delta_c`=200
  * `delta_l`=0.8
  * `timelimit`=16000
  * `genymotion_delploy_dir`=D:\\deployed\\
  * `avd`=avds/Custom Phone-6.0 320x480
  * `tool_name`=RepDroid
  * `apk_dir`=H:\\DataSet_S1\\FDroid\\
  * `output_dir`=J:\\TestOutPut\\RepDroid_by_Majun\\S1\\FDroid\\
  * `reinstallapk`=true
  * `takescreenshot`=true
  * `max_explore_depth`=2
