---
title: "使用Jekyll生成網誌 + 部署到Guthub Pages"
comments: true
categories: 
  - Software Engineering
tags:
  - Jekyll
  - Blog
excerpt_separator: <!--more-->
---

測試用
<!--more-->

## 背景

較常見使用的靜態網頁生成器有Hugo (Go)，Jekyll (Ruby)，Pelican (Python)，hexo(JavaScript)

基本流程就是使用者可以Markdown編輯文件，最由生成器生成html

Jekyll

> 靜態網頁 vs 動態網頁
>
> 靜態網頁沒有後台數據庫，不含在服務器端運行的程序



## 環境架設

由於在Windows下，`Ubuntu`

1. 安裝Git
   ```shell
   sudo apt-get install git -y
   ```
2. 設定Git使用者名稱及電郵
   ```shell
   git config --global user.name "username"
   git config --global user.email "username@gmail.com"
   git config --list
   ```
3. 登入Github創建一個新的repo，並以`username.github.io`命名，詳細可見[Github官方的教學](https://guides.github.com/features/pages/)

![new-repo-screen](https://guides.github.com/features/pages/create-new-repo-screen.png)
4. 將`username.github.io`的repo覆制到本地倉庫
   ```shell
   # 於根目錄下創建一個Github路徑
   cd ~
   mkdir github
   cd github
   git clone https://github.com/kafailao/kafailao.github.io.git
   ```
5. 安裝Jekyll
- 安裝Ruby及其它必需的包
   ```shell
   sudo apt-get install ruby-full build-essential zlib1g-dev
   ```

- 根據官方建議，應將gem包安裝到每個使用者自己的home directory下，避免以root user安裝gem包，因此需進行如下的環境變量配置

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

   Ubuntu沒有自帶中文輸入法，需要自行安裝，並於`settings` 的 `Region & Language` 的 `Input Sources`設定欄中添加

   ```shell
   sudo apt-get install ibus-cangjie #倉頡/速成
   sudo apt-get install ibus-pinyin #拼音
   ```
7. 安裝Markdown編輯軟件
接下來我們主要會以Markdown來編寫網誌，編寫後將`.md`檔案放置到Jekyll指定的資料夾後，就可運行Jekyll將生成HTML，推薦使用Typora，安裝方式如下：
   ```shell
   wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
   
   #add Typora's repository
   sudo add-apt-repository 'deb https://typora.io/linux ./'
   sudo apt-get update
   
   sudo apt-get install typora
   ```

## 使用網誌模版

到這一步我們就準備好用Jekyll去生成網頁了，Jekyll有很多免費的主題模版可以使用，可以在[GitHub.com #jekyll-theme repos](https://github.com/topics/jekyll-theme)、[jekyllthemes.io](https://jekyllthemes.io/)等找到這些模版

這裡使用的是[minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)，我們可以直接下載模版代碼放到`username.github.io`下

![image-20201221134323117](C:\Users\tsuba\AppData\Roaming\Typora\typora-user-images\image-20201221134323117.png)

- 其中`/docs`、`/test`、`changelog.md`、`minimal-mistakes-jekyll.gemspec`、`READNE.md`、`screenshot-layouts.png`、`screenshot.png`等檔案都可刪除，這些都是原本用來測試或展示的相關檔案，我們架設的網誌中不會用到
- 下載回來的文件裡還包含了一個`Gemfile`檔案，用途為定義了所需的依賴，我們需將以下內容替換到`Gemfile`中

   ```shell
   source 'https://rubygems.org'
   gem 'github-pages'，group: :jekyll_plugins
   gem "minimal-mistakes-jekyll"
   ```

- 修改`Gemfile`後儲存退出，再在命令行執行下面的指令更新gems

   ```shell
   cd ~/github/username.github.io.git
   bundle update
   ```
- 到這一步，整個網誌的框架可說是準備好，就只差我們的文章了！
- 
- 接下來我們可以在`username.github.io`目錄下新建一個`_posts`資料夾，並將


- 訪問http://127.0.0.1:4000/即可看到於本地部署好的網誌



```shell
bundle #安裝Gemfile裡的package
bundle exec jekyll new docs #create new site
cd docs
bundle 
bundle exec jekyll serve
```

- 訪問http://127.0.0.1:4000/即可看到於本地部署好的網誌

3. 
   - 
   - 
4. 

* upload the _.md_ file under the folder post



```shell
source "https://rubygems.org"
gem "github-pages"，group: :jekyll_plugins
```







http://jmcglone.com/guides/github-pages/

https://guides.github.com/features/pages/

https://jekyllthemes.io/theme/minimal-mistakes

https://jamstack.org/generators/