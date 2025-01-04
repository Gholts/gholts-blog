---
title: 客製化 Discord [ Desktop ]
date: 2025-01-04
categories: [Tutorial, Tools]
tags: [discord]
image:
  path: /assets/img/cute-logo.avif
  alt: Vencord cute-logo
---

## 寫在前面

Discord 作爲日常要高頻使用的軟體，滿屏飛的 Nitro 推廣和各種對非 Nitro 用戶的操作限制，還是要最大程度的優化一下。  
曾經用過 **better discord** 但是常常遇到 discord 更新就要重新 patch，甚煩直到我發現了這個項目 - [Vencord](https://vencord.dev/)。

Vencord 不但安裝時就內置了大多數最流行的 Plugins，還支持 Vencord Cloud 配置雲備份，最重要的事可以自動更新 Vencord 版本，Discord 更新也不會被取消 patched 狀態，讓我省心了超級多。

## 安裝 Vencord

  - 進入 [Vencord download page](https://vencord.dev/download/) 下載你對應系統鏡像的安裝器版本，我這邊以 Windows 版本舉例 ![](https://image.gholts.top/20250104114954837.png)
  - 打開安裝程序安裝即可，默認會識別到你的 Discord 路徑的，如果是 Mircosoft store 版本的話可能會出現無法找到路徑的情況，卸載後安裝官網版本即可。 「或者你可以訪問 windowsapp 目錄手動添加路徑（不推薦）」 ![](https://image.gholts.top/20250104115454648.png)
  - 這時候你的 Discord 應該會重新啓動，他應該就成功安裝了。

## 開始你的客製化之旅

  - 進入 Discord 使用者設定，就會看到多出了 Vencord 一欄，接下來你的大部分操作都會在這裏工作 <img src="https://image.gholts.top/20250104115730561.png" alt="Vencord" align="left">&nbsp;<img src="https://image.gholts.top/20250104120040321.png" alt="Plugins" width="85px">

先進入 Plugins 板塊，這裏預裝了超級多的 Plugins，你可以選擇你需要的選擇開啓並配置，我把我啓用的放在上面吧。  
我最常用的就是 Slient Typing 和 FakeNitro。 Slient Typing 顧名思義就是可以控制你的「正在輸入」狀態他人是否可見，開啓了這個 Plugin 就可以在 ~~別人眼中實現一秒10條訊息~~ 別人不知道時突然插入幾句。而 FakeNitro 一看名字就知道不怎麼 ~~合法~~ 了，我主要是用來發一些 stickers 和頻道 emojis。

>免責聲明： 不推薦任何違反 discord tos 的行爲，只是分享軟件工具內容，僅提供交流和學習爲目的的使用，違反 tos 的後果自行承擔

## 進一步的美化它

進入 Themes 板塊，你會發現什麼都沒有，這是因爲主題文件需要你在 [BetterDiscord Themes](https://betterdiscord.app/themes) 或者 [Github](https://github.com/search?q=discord+theme&type=repositories) 網站內下載，別受驚，很簡單。

#### 我先用前者舉例如何安裝

  - 以這個 [Theme](https://betterdiscord.app/theme/midnight) 舉例，進入頁面後點擊下載 ![](https://image.gholts.top/20250104124402670.png)，你會得到一個 `.css` 文件
  - 進入 Discord 使用者設定中的 Themes 板塊，點擊 Open Themes Folder ![](https://image.gholts.top/20250104124659339.png)
  - 進入 themes 文件夾，將剛剛下載到的 `.css` 文件移動到這裡
  - 回到 Discord，你就會發現多出了一個主題，啓用！
  - 享受你的主題

#### Github 內尋找主題

  - 以這個 [Theme](https://github.com/Comfy-Themes/Discord) 舉例，拷貝 readme 中提供的 vencord 導入連結 `https://comfy-themes.github.io/Discord/betterdiscord/comfy.theme.css`
  - 進入 Discord 使用者設定中的 Themes 板塊，點擊上方的 Online Themes 分頁，將連結粘貼入文本框 ![](https://image.gholts.top/20250104125507279.png)
  - 重新啓動 Discord
  - 享受你的主題

## 啓用 Vencord Cloud 配置雲備份

這個算是最能提升使用安全感的選項了，開啓後你的 Plugins 配置和 Themes 再也不會因 Discord 數據丟失導致配置一同消失

#### 開啓方法

  - 進入 Cloud 板塊
  - 開啓 Enable Cloud Integrations 選項和 Settings Sync 選項，不必擔心泄漏隱私，因爲它只會儲存上傳你的 Discord 使用者 ID 的 sha1 哈希值 - 這是唯一標識您的資料所必需的，和您的 Vencord 設置，儲存為 JSON 純文字。更多 [Privacy Policy](https://vencord.dev/cloud/privacy/) 你可以仔細閱讀後再自行判斷是否有必要開啓
  - 點擊 `Sync to Cloud` 即可同步本地配置到雲端 ![](https://image.gholts.top/20250104130408955.png)

## 最後

Vencord 是一個強大的配置增強工具，它不僅僅只有桌面端，還有對應的移動端（Android），下一篇 Blog 會詳細說明。  
提前說一下移動端（Android）安裝即可用，無需 root 設備或使用 shizuku 等工具提權，如果想要自己研究下載安裝，可以前往 [Github](https://github.com/Aliucord/Aliucord) 倉庫自行探索