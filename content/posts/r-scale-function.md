+++
date = '2025-10-01T00:14:28+08:00'
title = 'R Scale Function'
+++

The scale function functions as Scaling and centering of matrix-like objects according to the help document. When using it with pipe grouping to scale some group of data, the aggragated column names are not what that has been set in the mutate arguments, but with extra brackets or commas like scale_num[:,]. 

There is a [post](https://stackoverflow.com/questions/35775696/trying-to-use-dplyr-to-group-by-and-apply-scale) about customizing a scale function to use, after that the names of the new named column are not with extra brackets or commas anymore.
