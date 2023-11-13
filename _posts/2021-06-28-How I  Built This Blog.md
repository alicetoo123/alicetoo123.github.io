---
layout:	post
title:	How I Built This Blog (Mac Ver)
subtitle:	create a simple blog using GitHub pages and Jekyll
date:	2021-06-28
author:	Alice
header-img:	img/post-bg-1.jpg
catalog:	true
tags:
    - git
    - jekyll
---

### Preparation

- github pages ：*to hold the webpage files*
- git: *to upload local files to github*
- ruby: *to install jekyll*
- jekyll: *to check website locally*
- theme: *to make your blog pretty*
- some pictures: *to decorate your blog*
- markdown editor: *to write posts*

#### 1. github pages

- Go to [github.com](https://github.com) and create an account.
- Go to your account -> repositories and create a new repository **your username**.github.io

   <img src="/img/blog_20210628_1.png" alt="img_1" style="zoom:50%;" />
   
   <img src="/img/blog_20210628_2.png" alt="img_2" style="zoom:50%;" />

   <img src="/img/blog_20210628_3.png" alt="img_3" style="zoom:50%;" />

#### 2. Install Git

- Go to [git-scm.com](https://git-scm.com) and download the latest version.
I've got Xcode, so it's already there. Check if it is installed using **git --version** on your terminal.
```bash
$ git --version
git version 2.24.3 (Apple Git-128)
```

- Set configrations using **your username** and **your email address for GitHub account**
```bash
$ git config --global user.name "username"
$ git config --global user.email email_address
$ git config --gloval init.defaultBranch main
```

- Go to the directory you want to clone the new github repository you've just made. 
```bash
$ cd blog
```

- Initiate git there.
```bash
$ git init 
Initialized empty Git repository in /Users/alice/blog/.git/
```

Now you've got an invisible directory called **.git** holding the configrations. 

- Let's clone
```bash
$ git clone https://github.com/alicetoo123/alicetoo123.github.io.git
```

Copy the link above and replace the two username to yours. Or find this link from your github repository page.

<img src="/img/blog_20210628_4.png" alt="img_4" style="zoom:50%;" />

Now there is an empty directory "username.github.io" represening the one you have in your GitHub account. We will put all the webpage files here then synchronize it.

#### 3. Install ruby

Mac already have it installed.
check it on the terminal using **ruby -v**.

Install from [Ruby-lang.org](https://www.ruby-lang.org/en/documentation/installation/) if you don't have it.
```bash
$ ruby -v
ruby 2.6.3p62 (2019-04-16 revision 67580) [universal.x86_64-darwin20]
```

#### 4. Install jekyll

```bash
$ gem install jekyll
```

#### 5. Choose a Theme

Mine is from [here](https://github.com/qiubaiying/qiubaiying.github.io).
Find more [here](http://jekyllthemes.org).
Download and unzip all the files in one directory.

---

### Modification

To setup your own blog, please read the **README.md** of the theme and modify accordingly.
Usually all you need to do is:
- modify the file *_config.yml* and other files with extension name **.yml**
- replace the words in the file **about**
- replace **favicon.ico** with your own
- replace the pictures in the **image** directory

Go to the theme directory and run Jekyll, you can preview your modification in realtime.
Some themes require bundle install, some don't. Check **README.md** first.
You may need to enter password of your mac in the process.

This example need bunlde install.
```bash
$ cd /Users/alice/Downloads/jekyltheme-chirpy-master
$ bundle install
$ jekyll serve
```

*jekyll serve* enabled the local preview of the site. 
Now you can go to [http://127.0.0.1:4000](http://127.0.0.1:4000) to preview the theme and revise it.

---


### Upload

After the modifacation copy all the files to the directory we built in step 2: 
**username.github.io** 

On the terminal, go to the local repository and run git to upload the blog

```bash
$ git init
$ git add --all
$ git commit -m "Initial commit of my blog"
$ git push -u origin main
```

Go to github and check if everything is there.

For initial commitment,  use **git add --all**.
For additional update, use **git add updated_file_or_directory**.
Or you can go to github and edit the file online, and upload files via browser as well.

---

### Update a post

Use any markdown editor you feel comfortable to write a post and upload it to *_post* directory.
Remember to begin with **front matter**.

For example:

```markdown
---
layout:     post
title:      How I Built This Blog (Mac Ver)
subtitle:   creat a simple blog using GitHub pages and Jekyll
date:       2021-06-28
author:     Alice
header-img: img/blog-bg-1.jpg
catalog: true
tags:
    - git
    - jekyll
---
```

Refer to the sample post in the  *_post* directory for the format of front matter you need.
Upload your post via terminal using **git** or via **browser**.
Done!

---

### SSH Key

Using an SSH key to avoid entering username and password everytime uploading files via terminal.

Check if you have a file named **something.pub**. 
```bash
$ cd ~/.ssh 
$ ls
id_rsa		id_rsa.pub
```
The ssh key is in **id_rsa.pub** .

Sometimes you don't even have *.ssh* derectory. Let's create one.
```bash
$ ssh-keygen -t rsa -C "your_email_address_to_sign_in_github"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/alice/.ssh/id_rsa):
```
Press enter.
```bash
Enter passphrase (empty for no passphrase): [Type a passphrase] 
Enter same passphrase again: [Type passphrase again]
```
Press enter twice.
Your ssh key is generated. 

Go to **id_rsa.pub** and copy it.
```bash
$ cat ~/.ssh/id_rsa.pub
```
Go to github and add it to your accout.

   <img src="/img/blog_20210628_5.png" alt="img_5" style="zoom:50%;" />

   <img src="/img/blog_20210628_6.png" alt="img_6" style="zoom:50%;" />

   <img src="/img/blog_20210628_7.png" alt="img_7" style="zoom:50%;" />
