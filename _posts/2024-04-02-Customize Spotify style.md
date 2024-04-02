---
title: 客製化Spotify [Ⅱ]
date: 2024-04-02
categories: [Tutorial, Tools]
tags: [spotx, spicetify, rollback-spotify, spotify]
---

## ※[Rollback-Spotify項目地址](https://github.com/amd64fox/Rollback-Spotify)

>Rollback-Spotify是一個強大的Spotify版本退回工具，可以方便快捷的把Spotify退回到特定版本  
>而Rollback-Spotify有以下功能:
>
>- 退回Spotify版本
>- 阻止Spotify自動更新

## ※[Spicetify項目地址](https://github.com/spicetify/spicetify-cli)

>Spicetify是一個功能終極強大的Spotify客製化工具,可以高度客製化Spotify的界面，功能  
>而Spicetify有以下功能:
>
>- 客製化Spotify theme
>- 客製化Spotify功能
>- 增加更多擴充
>- 增加MarketPlace -更多的擴充和客製化應用程式

## 1.事前準備

- 更改版本爲1.2.30.1135

  - 運行Powershell，執行 `[Net.ServicePointManager]::SecurityProtocol = 3072; iex "& { $(iwr -useb 'https://amd64fox.github.io/Rollback-Spotify/run.ps1') } -version 1.2.30.1135-x64"`

  - 在下面的選項 `Found version 1.2.30.1135 installed on your system. Remove it?
[Y] Yes  [N] No  [?] Help (default is "Y"):` 中填寫 `Y`

  - 等待出現 `Updates blocked` 提示出現，回退Spotify版本就成功了

- 再次[安裝SpotX](https://blog.gholts.top/posts/Customize-Spotify/)

## 2.安裝Spicetify

- 運行Powershell，執行 `iwr -useb https://raw.githubusercontent.com/spicetify/spicetify-cli/master/install.ps1 | iex`

- 在下面的選項 `Do you want to install Spicetify Marketplace?
[Y] Yes  [N] No  [?] Help (default is "Y"):` 中填寫 `Y`

- 等待安裝完畢後，執行 `spicetify -config-dir` ，查看配置文件地址

## 3.安裝Spicetify主題

- 主題倉庫:

  - [Spicetify官方主題](https://github.com/spicetify/spicetify-themes) -更好的兼容性和更多的高級配置

  - [Comfy主題](https://github.com/Comfy-Themes/Spicetify) -更簡單的操作和更多種類的預設skins

>我個人使用的就是Comfy主題，簡單上手，有圖形化的客製化界面，定製實時生效

### 安裝Spicetify官方主題

- 下載[官方主題倉庫](https://github.com/spicetify/spicetify-themes/archive/refs/heads/master.zip)

- 你可以從[Themes.md](https://github.com/spicetify/spicetify-themes/blob/master/THEMES.md)預覽主題

- 從下載到的官方主題倉庫中挑選想要的主題文件夾複製到 `%appdata%\spicetify\Themes`

- 打開上級目錄的 `config-xpui.ini`

- 編輯 `current_theme` 爲主題文件夾名稱

- 編輯 `color_scheme` 爲Skin名稱

>Skin名稱可以在[Themes.md](https://github.com/spicetify/spicetify-themes/blob/master/THEMES.md)查看

- 在PowerShell執行 `spicetify apply` 等待執行完成後再次重啓Spotify即可生效

### 安裝Comfy主題

- 在PowerShell執行 `iwr -useb https://raw.githubusercontent.com/NYRI4/Comfy-spicetify/main/install.ps1 | iex`

- 等待執行完成後再次重啓Spotify即可生效

## 4.安裝Spicetify客製化應用程式

- [官方客製化應用程式](https://spicetify.app/docs/advanced-usage/custom-apps)

  - [Reddit](https://spicetify.app/docs/advanced-usage/custom-apps#reddit) -在Reddit上抓取Spotify分享鏈接
  ![Reddit](https://i.imgur.com/MC3tpNZ.png)

  - [New Releases(新發布歌曲)](https://spicetify.app/docs/advanced-usage/custom-apps#new-releases) -總結最喜愛的藝術家、播客的所有新發佈內容
  ![New Releases](https://i.imgur.com/MP9dTjt.png)

  - [Lyrics Plus(歌詞PLUS)](https://spicetify.app/docs/advanced-usage/custom-apps#lyrics-plus) -從各個歌詞提供者（Musixmatch、Netease、Genius）取得目前曲目的歌詞
  ![Lyrics Plus](https://i.imgur.com/WtD080A.png)

### 安裝Reddit

- 在PowerShell執行 `spicetify config custom_apps reddit` `spicetify apply`

- 等待執行完成後再次重啓Spotify即可生效

### 安裝New Releases(新發布歌曲)

- 在PowerShell執行 `spicetify config custom_apps new-releases` `spicetify apply`

-等待執行完成後再次重啓Spotify即可生效

### 安裝Lyrics Plus(歌詞PLUS)

- 在PowerShell執行 `spicetify config custom_apps lyrics-plus` `spicetify apply`

- 等待執行完成後再次重啓Spotify即可生效

## 5.解除安裝

- 在PowerShell執行

```
spicetify restore
rmdir -r -fo $env:APPDATA\spicetify
rmdir -r -fo $env:LOCALAPPDATA\spicetify
```

## Advanced

- 更多擴充和客製化應用程式可以在側邊欄 `MarketPlace` 中找到

- 如果你是開發者，想要編寫更多擴充和客製化應用程式，可以在[Spicetify Development](https://spicetify.app/docs/development)中找到更多
