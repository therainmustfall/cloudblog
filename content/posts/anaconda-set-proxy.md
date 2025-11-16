+++
date = '2025-11-16T17:37:28+08:00'
draft = false
title = 'Anaconda proxy setting'
+++

This is what recently has been searched several times. For future reference, it could be noted here.


```bash
conda config --set proxy_servers.http http://localhost:XXXXX
conda ocnfig --set proxy_servers.https http://localhost:XXXXX
```

**other basic conda commands**

```bash
# creating new environment
conda create -n new_envrionment_name python=3.XX --yes

# list environments
conda env list

# delete an environment
conda remove -n environment_name --all

# activate an environment 
conda activate new_envrionment_name

# or using path to create and activate new environments
conda create -p path/to/new/environment
conda activate path/to/new/environment

```


