+++
date = '2025-11-01T12:07:01+08:00'
draft = false
title = 'Nginx Beginning Basics on Windows'
+++

## Nginx beginner's Guide on Windows



### Configuration File



On Windows System, the configuration file is located in the conf folder of the unzipped application file. You can double click the exe file to run
Nginx. Then it will show you message box to allow it to run on Windows. After confirmation it will run in the background as a service. We can use *.\\nginx.exe -s **signal*** to control its behavior where **signal** can be *stop*, *quit*, *reopen* or *reload*.



After executing **.\\nginx.exe -s stop**, it prints nothing in the Windows Terminal. But it actually stopped after that command. If run the command again, the terminal will tell you "The system cannot find the file specified" error. More controlling options to use in the nginx command can be found by running **.\\nginx.exe -h** .



In the .conf file you will see many **contexts**. A **context** is a block in the configuration file that surrounds other block or directives(consisting of words, spaces and ending with a semicolon) inside its braces. A main context is located outside any other contexts. There are also many lines that commented by **#**.



### Simple Serving Configuration

Commenting all the remaining server context in the default .conf file, and adding the configuration as the [guide](https://nginx.org/en/docs/beginners_guide.html) described. Then in the Windows Terminal run **.\\nginx.exe -s reload**. It will show the newly created localhost webpage on the browser. In my case, I just changed the last sentence in the index.html from "*Thank you for using nginx.*" to "*Using Customized conf file.*" and copy it to the newly created *data/www* folder.

Now all the configuration excepting the commented line are as follows (I removed the first forward dash before folder name **data** that the guide uses after encountering error opening localhost. In the guide, the directory is **/data/www**, but on my window machine it leads to error when opening locahost on the browser.):
```
worker_processes  1;

events {
    worker_connections  1024;
}

http {
	include       mime.types;
	default_type  application/octet-stream;
	sendfile        on;

  	keepalive_timeout  65;
    	server {
    		location / {
        		root data/www;
    		}
    	location /images/ {
        	root data;
    		}
    	}
}
```

### Setting Up a Proxy Server


* Configuration file:

```
worker_processes  1;

events {
worker_connections  1024;
}

http {
	include       mime.types;
	default_type  application/octet-stream;
	sendfile        on;

  	keepalive_timeout  65;

    	server {
    	location / {
        	proxy_pass http://localhost:8080;
    	}

    	location ~\.(gif|jpg|png)$ {
        	root data/images;
    	}
       }

      server {
        listen 8080;
         root data/up1;

         location / {
        }
   }
}

```

reference:

* [Beginner’s Guide](https://nginx.org/en/docs/beginners_guide.html)

To learn more:

- [zhihu](https://zhuanlan.zhihu.com/p/362315737)
- [normal solutions](https://www.msn.cn/zh-cn/%E9%80%9A%E7%94%A8/%E9%80%9A%E7%94%A8/%E8%BF%90%E7%BB%B4%E5%B9%B2%E8%B4%A7-nginx-%E5%B8%B8%E7%94%A8%E9%85%8D%E7%BD%AE%E4%B8%8E%E9%97%AE%E9%A2%98%E6%8E%92%E6%9F%A5%E6%8C%87%E5%8D%97/ar-AA1OCITb)
- [configuration](https://www.runoob.com/w3cnote/nginx-setup-intro.html)
- [from zero to one](https://developer.baidu.com/article/detail.html?id=3588926)

