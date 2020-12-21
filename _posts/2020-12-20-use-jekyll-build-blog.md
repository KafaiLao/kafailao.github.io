---
title:  " 使用Jekyll生成個人網誌 + 部署到Github pages"
header:
  teaser: "/assets/images/500x300.png"
categories: 
  - 前端技術
tags:
  - Jekyll,blog
---



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
   sudo apt-get install git -y
   ```
2. 設置Github
   ```shell
   git config --global user.name "username" #你的Github帳號名字
   git config --global user.email username@gmail.com"
   git config --list
   ```
3. 登入Github網站創建repo並以`username.github.io`命名, 詳細可見[Github的教學](https://guides.github.com/features/pages/)

![new-repo-screen](https://guides.github.com/features/pages/create-new-repo-screen.png)
4. 將Github pages的repo覆制到本地倉庫
   ```shell
   cd ~
   mkdir github
   cd github
   git clone https://github.com/kafailao/kafailao.github.io.git
   ```
5. 安裝Jekyll
- 安裝Ruby及其它必需的包
   ```Shell
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

   ```shell
   gem install jekyll bundler
   ```

6. 安裝中文輸入法

   Ubuntu沒有自帶中文輸入法, 需要自行安裝, 並於`settings` 的 `Region & Language` 的 `Input Sources`設定欄中添加

   ```shell
   sudo apt-get install ibus-cangjie #倉頡/速成
   sudo apt-get install ibus-pinyin #拼音
   ```



## 網誌部署

https://jekyllrb.com/docs/github-pages/

```shell
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

## 使用模版

到這一步就可以用Jekyll去生成網頁了, 但我們不用從頭做起, 有很多現成的模版可以使用, 例如[lanyon](https://github.com/poole/lanyon), 我們可以直接下載整個代碼放到

這裡使用的是[minimal-mistakes](https://github.com/mmistakes/minimal-mistakes), 我們可以把代碼下載

3. 
   - 
   - 
4. 

* upload the _.md_ file under the folder post



```shell
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
```







http://jmcglone.com/guides/github-pages/

https://guides.github.com/features/pages/

https://jekyllthemes.io/theme/minimal-mistakes

https://jamstack.org/generators/