+++
date = '2025-10-06T15:39:14+08:00'
draft = false
title = 'How to Create a New Hugo Post'
+++

* Creating: using **hugo new**

After a hugo blog is set up on a local computer, to create and publish a new blog, you need to use the *hugo new* command. It generates a new markdown file starting with its creation date, draft status and title. To run this command, first go to the site directory that contains all of the blog files within, e.g., one of them is the *content* folder that we access below.

```bash
cd /my/hugo/site/folder
```

Then in the terminal run:

```bash
hugo new content/posts/how-to-create-a-new-hugo-post.md
```

This will create a markdown file under the folder **content/posts/**, now we can edit.

* Editting: any editor you use

After editing the markdown file we created above, remember to change the *draft: true* to *draft: false* before publish it. Or we could first change its value to *false* at first.


* Publishing: case for using Git

Finally, use the git command to commit and push the blog file to remote server.

```bash
git push -u origin main 
```

* Reference:
  
    - [Host on Cloudflare](https://gohugo.io/host-and-deploy/host-on-cloudflare/)

