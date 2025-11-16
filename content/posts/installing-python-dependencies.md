+++
date = '2025-11-16T17:58:44+08:00'
draft = false
title = 'Installing Python Dependencies'
+++

Recenlty when using conda to create an environment, I used a script that was edited by me about three months ago. At that time, I ran the code to install the python dependencies and it worked fine on the kaggle notbook. But when I tried to run it again yesterday, it reported error after searching a specific package ( in this case it's Cython version mismatch that caused by installing a certain version of murmurhash). 

I copied the code to run on my computer it still reported the error under my linux operation system. So it is obvious that some python packages may change dependencies relations, even the packages are associated with certain earlier python version (python3.6 for example). Same scripts that successfully created and built an environment long time targeting a python version also long time ago may not always work in the long run. So the best practice may be creating an an environment and never recreating it when it finally meets the earlier task requirments. So **Never transplant or gliding the lily**. 
