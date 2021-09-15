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

This page describes parameters within the configuration file bm_gen.properties.

####  The parameters contained in bm_gen.properties are:
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

