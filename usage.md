<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

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
  * `android_sdk_path`: path ot the android sdk (e.g., E:\\IDE\\AndroidSDK\\SDK)
  * `ant_root_path`: path to the ant root directory (e.g.,E:\\IDE\\apache-ant-1.10.11)
  * `aapt_path`:  path to the aapt.exe (e.g., E:\\IDE\\AndroidSDK\\SDK\\build-tools\\26.0.2\\aapt.exe)
  * `genymotion_home`:  nstall directory of Genymotion (e.g, C:\\Program Files\\Genymobile\\Genymotion\\)
  * `vbox_home`: the install directory of VirtualBox (e.g., C:\\Program Files\\Oracle\\VirtualBox\\)
  * `max_step`: $$r_m$$ max allowed loops for exploring a single apk, default value is 1000.
  * `max_unchange_step`: $$c_m$$ max allowed non-effective action limits, default value is 200
  * `delta_l`=0.8
  * `timelimit`: max allowed time (unit: seconds) for exploring a single apk
  * `genymotion_delploy_dir`: the deploy directory of Genymotion (e.g., D:\\deployed\\)
  * `avd`: path to the backup fresh avd (e.g., avds/Custom Phone-6.0 320x480)
  * `tool_name`: the tool to be used (options including `RepDroid`, `RegionDroid' and `GridDroid')
  * `apk_dir`: the dir containing apks to generate birthmark (e.g., H:\\DataSet_S1\\FDroid\\)
  * `output_dir`: the dir for keeping generation results (e.g., J:\\TestOutPut\\RepDroid_by_Majun\\S1\\FDroid\\)
  * `reinstallapk`: if set `true`, an installed apk would be reinstalled 
  * `takescreenshot`: if set `true', an screenshot would be taken each time a new group is encountered
  * `max_explore_depth`: $$d_m$$ the birthmark depth limit, default value is 2
