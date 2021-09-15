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
The environment settings used in our evaluations are listed as follow:
* Operating System: Window 10 (currently we provide fully automation for only Window OS)
* Java SDK: 1.8.0_281 
* Android SDK :
  * build-tools: 26.0.2
* Apache-ant: 1.10.11 
* Emulator: 
  * Genymotion, version 3.2.0

## Run GridDroid

### **Step-1**: Download and unzip the [GridDroid.jar](https://drive.google.com/file/d/1EJPBuPSFbh6DdeGNRW8ojc5GqgdkDeGb/view?usp=sharing)

### **Step-2**: Birthmark generation
#### 1. Create an AVD via Genymotion.
 The AVD settings used in our evaluation are:
    * Device: Custom Phone
    * Android API: 6.0 API 23
    * Size: 480
    * Density: 160-MDPI
    * Procesors: 4
    * Memeory Size: 2048 MB
    * Network: NAT (some app require internet access)
    * Turn off window animation, transition animation and animation duration in the "Developer options"
    * To run ARM apps, please install [Genymotion-ARM-Translation](https://github.com/m9rco/Genymotion_ARM_Translation)
    
#### 2. Backup fresh AVD
  * Open the deploy directory of Genymotion (e.g., `C:\Users\username\AppData\Local\Genymobile\Genymotion\deployed`). The path of the deploy directory can be found via clicking ``Genymotion->Settings->VirtualBox`` of the GUI of Genymotion.
  * Copy the directory of the created AVD to a location other than the deploy directory (e.g., `d:\AVDs\`).

#### 3. Download and edit the configuration file [bm_gen.properties](bm_gen.properties) accordingly. The parameters are:
  * `android_sdk_path`: path ot the android sdk (e.g., `E:\\IDE\\AndroidSDK\\SDK`).
  * `ant_root_path`: path to the ant root directory (e.g., `E:\\IDE\\apache-ant-1.10.11`).
  * `aapt_path`:  path to the aapt.exe (e.g., `E:\\IDE\\AndroidSDK\\SDK\\build-tools\\26.0.2\\aapt.exe`).
  * `genymotion_home`:  install directory of Genymotion (e.g, `C:\\Program Files\\Genymobile\\Genymotion\\`).
  * `vbox_home`: the install directory of VirtualBox (e.g., `C:\\Program Files\\Oracle\\VirtualBox\\`).
  * `max_step`: max allowed loops for exploring a single apk (i.e., $r_m$), default value is `1000`.
  * `max_unchange_step`:  max allowed non-effective action limit  (i.e., $c_m$), default value is `200`.
  * `delta_l`: the layout similarity threshold (i.e., $\delta_l$), default value is `0.8`
  * `timelimit`: max allowed time (unit: seconds) for exploring a single apk, default value is `16000`.
  * `genymotion_delploy_dir`: the deploy directory of Genymotion (e.g., `D:\\deployed\\`).
  * `avd`: path to the backup fresh avd (e.g., `avds/Custom Phone-6.0 320x480`).
  * `tool_name`: the tool to be used (options including `RepDroid`, `RegionDroid` and `GridDroid`).
  * `apk_dir`: the dir containing apks to generate birthmark (e.g., `H:\\DataSet_S1\\FDroid\\`).
  * `output_dir`: the dir for keeping generation results (e.g., `J:\\TestOutPut\\RepDroid_by_Majun\\S1\\FDroid\\`).
  * `reinstallapk`: if set `true`, an installed apk would be reinstalled.
  * `takescreenshot`: if set `true`, an screenshot would be taken each time a new group is encountered.
  * `max_explore_depth`: $d_m$ the birthmark depth limit, default value is `2`.

#### 4. Execute following command to generate birthmark:
```
java -jar GridDroid.jar -gen bm_gen.properties
```

### **Step-3**: Birthmark comparison
#### 1. Download and edit the configuration file [bm_compare.properties](bm_compare.properties) accordingly. The parameters are:
  * `tool_name`: the tool to be used (options including `RepDroid`, `RegionDroid` and `GridDroid`)
  * `bm_dir1`: the dir1 containing birthmarks to be compared (e.g., `J:\\TestOutPut\\GridDroid_by_Majun\\S1\\FDroid\\strategy_output_FDroid\\`)
  * `bm_dir2`: the dir2 containing birthmarks to be compared (e.g., `J:\\TestOutPut\\GridDroid_by_Majun\\S1\\FDroid\\strategy_output_FDroid\\`)
 
 Birthmarks contained in `bm_dir1` would be compared with those contained in `bm_dir2`.
 
  * `output_file`: the file to store comparison results, (e.g., `J:\\TestOutPut\\GridDroid_by_Majun\\S1\\FDroid\\similarity.txt`).
  * `filteron`:  if set `true`, filters would be turned on.
  * `use_ext_matching_algorithm`:  if set `true`, the extended matching algorithm would be applied.
  * `delta_s`: the app similarity threshold (i.e., $\delta_s$), default value for GridDroid is `0.76`.

The following parameters are only applicable to GridDroid:
  * `delta_f`: Bucket Vector filter threshold (i.e., $\delta_f$), default value is `0.45`.
  * `delta_g`: Union Vector filter threashold (i.e., $\delta_g$), defalut value is `0.65`.
  * `bucket_number`: interval number of Bucket Vector filter (i.e., $k$), defalut value is `8`.
  * `bucket_length`: interval length of Bucket Vector filter (i.e., $\sigma$), defalut value is `25`.

#### 2. Execute following command to compare birthmark:
```
java -jar GridDroid.jar -cmp bm_compare.properties
```
