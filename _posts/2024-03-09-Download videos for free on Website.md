---
title: 利用 YT-DLP 下載幾乎任何影片
date: 2024-03-09
categories: [Tutorial, Tools]
tags: [yt-dlp]
---

## ※ [YT-DLP 項目地址](https://github.com/yt-dlp/yt-dlp)

>YT-dlp 是一個功能強大的影片下載工具，支持解析下載網路上 90% 的影片網站。  
>YT-dlp 主要功能有:
>
>- 解析下載影片
>- 客製化影片格式和碼率
>- 客製化音頻質量
>- 分離影片和音頻下載，同時也支持自動合併
>- 修改影片元數據
>- 可以從串流媒體清單中提取字幕
>- 下載時間範圍
>- More...

## 1.安裝 Python 環境

1. 進入 [Python](https://www.python.org/downloads/) 官網下載安裝包

2. 安裝 Python 時，請確保選擇"新增至 PATH"

## 2.安裝 FFmpeg

1. 進入 [FFmpeg](https://www.ffmpeg.org) 官網下載安裝包

2. 按照提示進行安裝

3. 手動添加環境變數

    1. 打開"計算機"->"内容"->"進階系統設置"->"環境變數"
  
    2. 在系統變數部分找到 "Path"，點擊"編輯"
  
    3. 在“變數值”中添加 `ffmpeg.exe` 所在的文件夾路徑
  
    4. 点击确定，完成环境变量配置

## 3.安裝 yt-dlp

1. 新建一個 AdministratorCMD 窗口任務

2. 執行代碼 `pip install yt-dlp`

## 4.Enjoy

1. 輸入 `yt-dlp` `yt-dlp [影片鏈接]` 即可下載

2. 輸入 `yt-dlp -f ‘bv[ext=mp4]+ba[ext=m4a]’ --embed-metadata --merge-output-format mp4 [影片鏈接]` 即可下載最佳 mp4 影片+最佳 m4a 音頻格式並合成 mp4

## 5.Advanced

- yt-dlp 支持解析下載該[列表](https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md)内的影片鏈接

- 如需指定下載地址,可以使用 `-o` 或 `--output` 參數,例如 `yt-dlp [影片鏈接] -o "F:/%(title)s.mp4"`

- 更多詳細配置可以參考 [YT-DLP 官方文檔](https://github.com/yt-dlp/yt-dlp?tab=readme-ov-file#usage-and-options)
