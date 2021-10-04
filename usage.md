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

### **Step-1**: Download and unzip the [GridDroid.zip](https://drive.google.com/file/d/1wgqlp2Mz_qkgt68XZq5WTU_ofzGQfhB7/view?usp=sharing)

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
  * Copy the directory of the above created AVD to a location other than the deploy directory (e.g., `d:\AVDs\`).

#### 3. Edit the configuration file bm_gen.properties accordingly. 
  * For description about the parameters, please refer to the [Description page of bm_gen.properties](bm_gen_description.md).

#### 4. Execute following command to generate birthmark:
```
java -jar GridDroid.jar -gen bm_gen.properties
```

### **Step-3**: Birthmark comparison
#### 1.Edit the configuration file bm_compare.properties accordingly. 
  * For description about the parameters, please refer to the [Description page of bm_compare.properties](bm_compare_description.md).

 
#### 2. Execute following command to compare birthmark:
```
java -jar GridDroid.jar -cmp bm_compare.properties
```
