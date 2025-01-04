---
title: 客製化 Discord [ Android ]
date: 2025-01-04
categories: [Tutorial, Tools]
tags: [discord]
image:
  path: /assets/img/Aliucord.png
  alt: Aliucord logo
---

## 繼上篇

Discord 不止電腦端需要優化，手機端也可以優化，我曾經用過 Vendetta, Bunny, Revenge, Vendroid 都覺得有點說不出的臃腫或者說繁雜，當我上手 Aliucord 的時候，完全被它的簡潔小巧但功能有力的特點深深吸引，下面就是上手。

## 安裝

流程和別的 Client 安裝流程大體相同，我以下就快速過一下流程

  - 進入 [Aliucord](https://github.com/Aliucord/Aliucord/releases/latest) 下載頁面下載 Installer 安裝包並安裝
  - 「可選」可點擊右上角進入設定選擇是否開啓 Aliucord 風格圖標 （左圖）

<img src="https://image.gholts.top/Aliucord-home.png" alt="settings" width="185px" align="left">&nbsp;<img src="https://image.gholts.top/Aliucord-settings.png" alt="home" width="185px">

  - 回到主頁點擊 `Install` 安裝 Aliucord （右圖）

## 更進一步

Aliucord 想要安裝 Plugins 和 Themes 不同於 Vendetta 系，需要在文件管理器中移動 Plugins 和 Themes 到指定文件夾，別受驚，很簡單。  
首先你需要加入 Aliucord 的 [Discord 頻道](https://discord.com/invite/EsNDvBaHVU)才能開始下面的操作

>在選擇 Plugins 和 Themes 的階段不必要切換到手機，可以先在桌面端下載全部需要的 Plugins 和 Themes 再傳送至手機對應文件夾

  - 開啓 Aliucord 頻道的 plugins-list 版塊，挑選你需要的 Plugins，我以這個 FakeStickers 舉例如何下載到 Plugins ![](https://image.gholts.top/20250104175309037.png)
  - 首先找到帖子下方的 Github 連結進入（不同的帖子連結位置大同小異，根據實際情況即可）
  - 在 Readme 中找到對應 Plugin 的超連結 ![](https://image.gholts.top/20250104175524477.png)
  - 下載 `.zip` 形式的 Plugin，即可，這就是你最終要移動到對應文件夾的插件形式
  - 最後把插件移動到手機的 `/storage/emulated/0/Aliucord/plugins/` 目錄下「最終就是一些 `.zip` 壓縮包，不要解壓它」

我最後把我的插件列表放在下面，足夠少也足夠有用

<img src="https://image.gholts.top/Plugins.png" alt="Plugins" width="185px" align="center">

你肯定注意到 list 中有一個插件叫做 `Themer`，這個就是我們用來生效主題的插件

  - 開啓 Aliucord 頻道的 themes 版塊，選擇你最心儀的主題，我以 slate 作爲演示 ![](https://image.gholts.top/20250104180641109.png)
  - 首先找到帖子下方的 Raw 連結進入（不同的帖子連結位置大同小異，根據實際情況即可）
  - 右鍵以 `.json` 文檔儲存 ![](https://image.gholts.top/20250104180858432.png)
  - 移動到 `/storage/emulated/0/Aliucord/themes/` 目錄下，回到 Themer 插件
  - 進入 Themer 插件的 Settings，點擊最上方的 `Load missing themes` 以載入剛剛添加的主題文檔
  - 根據帖子中的 Requirements 開啓對應選項即可，重新啓動 Discord。 

<img src="https://image.gholts.top/Themer-settings.png" alt="Themer-settings" width="185px" align="center">

  - 更多的選項可以點擊主題下方的蠟筆圖示進入，開始你的深層次客製化！「保存後根據提示 restart 即可生效」
  - 享受你的主題！