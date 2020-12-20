---
title:  " 使用Jekyll生成個人網誌 + 部署到Github pages"
header:
  teaser: "/assets/images/500x300.png"
categories: 
  - Jekyll
tags:
  - update
---

# 使用Jekyll生成個人網誌 + 部署到Github pages



## 背景

較常見使用的靜態網頁生成器有Hugo (Go), Jekyll (Ruby), Pelican (Python), hexo(JavaScript)

基本流程就是使用者可以Markdown編輯文件, 最由生成器生成html

Jekyll

> 靜態網頁 vs 動態網頁
>
> 靜態網頁沒有後台數據庫, 不含在服務器端運行的程序



## 環境架設

以下命俴`Ubuntu`

1. 安裝Git

```shell
sudo apt install git -y
```

2. 設置Github

```shell
git config --global user.name "kafailao"
git config --global user.email "kflao.umac@gmail.com"
git config --list
```

3. 登入Github網站創建repo並以`username.github.io`命名, 詳細可見[Github的教學](https://guides.github.com/features/pages/)

![new-repo-screen](https://guides.github.com/features/pages/create-new-repo-screen.png)

3. 將Github pages的repo覆制到本地倉庫

```shell
cd ~
mkdir github
cd github
git clone https://github.com/kafailao/kafailao.github.io.git
```



4. 安裝Jekyll

- 安裝Ruby及其它必需的包

```shell
sudo apt-get install ruby-full build-essential zlib1g-dev
```

- 根據官方建議, 應將gem包安裝到每個使用者自己的home directory下, 避免以root user安裝gem包, 因此需進行如下的環境變量配置

```shell
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

- 安裝Jekyll及Bundler

```Shell
gem install jekyll bundler
```



## 網誌部署

https://jekyllrb.com/docs/github-pages/

```Shell
cd ~/github/kafailao.github.io.git
gedit Gemfile #或使用 "bundle init"
```

- Create/replace the contents of your `Gemfile` with the following

```shell
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins
gem "minimal-mistakes-jekyll", group: :jekyll_plugins
```

- Fetch and update bundled gems by running the following [Bundler](https://bundler.io/) command:

```shell
bundle #安裝Gemfile裡的package
bundle exec jekyll new blog #create new site
cd blog
bundle 
bundle exec jekyll serve
```

- 訪問http://127.0.0.1:4000/即可看到部署好的網誌

![image-20201220171929654](C:\Users\tsuba\AppData\Roaming\Typora\typora-user-images\image-20201220171929654.png)



- Install Jekyll locally via the command line, create a new boilerplate website using `jekyll new`, build it locally with `jekyll build`, and then serve it. (The [Jekyll website](http://jekyllrb.com/) shows this workflow.)
- Clone a starting point to your local machine, install Jekyll locally via the command line, make updates to your website, build it locally, and then serve it.
- Fork a starting point, make changes, and then serve it.



1. 到這一步就可以用Jekyll去生成網頁了, 但我們不用從頭做起, 有很多現成的
2. 
3. 
   - https://github.com/poole/lanyon
   - 
4. 

* upload the _.md_ file under the folder post



```Shell
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
```







http://jmcglone.com/guides/github-pages/

https://guides.github.com/features/pages/

https://jekyllthemes.io/theme/minimal-mistakes

https://jamstack.org/generators/
