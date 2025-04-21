---
title: 利用 SpotDL 下載 Spotify 音樂
date: 2024-03-05
---

## ※ [SpotDL 項目地址](https://github.com/spotDL/spotify-downloader)

>SpotDL 是一個功能強大的 Spotify 音樂下載工具，支持解析下載 Spotify 上 99% 的音樂。  
>SpotDL 的功能有：
>
>- 解析下載 Spotify 音樂
>- 僅保存 Spotify 的元數據，而不下載任何內容
>- 更新所提供歌曲檔案的元資料
{: .prompt-info }

## 1. 安裝 Python 環境

1. 進入 [Python](https://www.python.org/downloads/) 官網下載安裝包

2. 安裝 Python 時，請確保選擇"新增至 PATH"

## 2. 安裝 SpotDL

1. 新建一個 AdministratorCMD 窗口任務

2. 依次執行代碼 `pip install spotdl` `spotdl --download-ffmpeg`

## 3.Enjoy

1. 輸入代碼 `spotdl` `spotdl download [spotify 單曲鏈接]` 或者 `spotdl download [spotify 歌單鏈接]` 即可下載

2. 預設下載地址在 ```C:\Users\[你的 Windows 賬戶名]```

## 4.Advanced

- 預設設定檔在 `C:\Users\[你的 Windows 賬戶名]\.spotdl\config.json`

- `output` 是配置預設下載地址

- `format`是配置下載音頻格式，例如 MP3,M4A 和 OPUSS

- 你可以透過執行 `spotdl web` 命令來啓動 Web UI，不過要把 `web_use_output_dir` 項設定為 true

- 更多詳細配置可以參考 [SpotDL 官方文檔](https://github.com/spotDL/spotify-downloader/blob/master/docs/usage.md)

>SpotDL 使用 YouTube 作為音樂下載來源，此方法用於避免與從 Spotify 下載音樂相關的任何問題。
>使用者應對自己的行為和潛在的法律後果負責。SpotDL 不支援未經授權下載受版權保護的資料，並且對使用者行為不承擔任何責任。
{: .prompt-warning }
