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

#### 3. Download and edit the configuration file [bm_gen.properties](bm_gen.properties) accordingly. 
    * For description about the parameters within the  bm_gen.properties file, please refer to the [bm_gen.properties Description](bm_gen_description.md) page.

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
