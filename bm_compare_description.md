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

This page describes parameters within the bm_compare.properties file.

### The parameters are:
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

