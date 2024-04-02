---
title: 客製化Spotify [Ⅰ]
date: 2024-03-27
categories: [Tutorial, Tools]
tags: [spotx, spotify]
---

## ※[SpotX項目地址](https://github.com/SpotX-Official/SpotX)

>SpotX是一個功能強大的Spotify客製化工具，同時還兼容安裝Spicetify用於客製化Spotify界面和功能，SpotX就是這一類軟體中的最優解。  
>而SpotX有以下功能:
>
>- 去除廣告(非Premium用戶)
>- 解鎖Premium功能(極高音質除外)
>- 阻止Spotify自動更新(可選)
>- 從主頁隱藏播客、劇集和有聲讀物(可選)
>- 啟動更多實驗性功能
>- 消除從右到左的 CSS 規則以進行簡化，並執行程式碼精簡
>- 向 Spotify 開發人員停用哨兵的控制台日誌/錯誤/警告訊息，停止使用者互動日誌記錄

## 1.安裝Spotify

- 下載[Spotify安裝包](https://download.scdn.co/SpotifySetup.exe)安裝即可

>千萬不要安裝Microsoft store的版本!!!

## 2.安裝SpotX

- 運行一個 Windows PowerShell

- 非Premium用戶執行 `iex "& { $(iwr -useb 'https://raw.githubusercontent.com/SpotX-Official/spotx-official.github.io/main/run.ps1') } -new_theme -language zh-TW"`

- Premium用戶執行 `iex "& { $(iwr -useb 'https://raw.githubusercontent.com/SpotX-Official/spotx-official.github.io/main/run.ps1') } -new_theme -premium -language zh-TW"`

- 根據個人需求選擇 [Y/N] 即可

>Y即Yes，N即No

>建議阻止 Spotify 自動更新，因爲Spotify官方的更新只是簡單的覆蓋，會導致你的SpotX失效，想要恢復很簡單，重新安裝SpotX即可

## 3.Enjoy

- 等待Spotify重啓即可

## 4.解除安裝

- 只需在Spotify檔案文件夾運行[Uninstall.bat](https://raw.githack.com/amd64fox/SpotX/main/Uninstall.bat)即可

>Spotify預設檔案資料夾在 `%appdata%/spotify`

- 或者重新安裝 Spotify(建議[完全卸載 Spotify](https://github.com/amd64fox/Uninstall-Spotify))

## 5.Advanced
- 一些相關[SpotX FAQ](https://telegra.ph/SpotX-FAQ-09-19)

- 更多[安裝參數](https://github.com/SpotX-Official/SpotX/discussions/60)

