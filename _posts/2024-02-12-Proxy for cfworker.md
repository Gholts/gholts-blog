---
title: CFworker Proxy 免費搭建
date: 2024-02-12
categories: [Tutorial, Proxy]
tags: [proxy]
---

## ※ [EDtunel 項目地址](https://github.com/3Kmfi6HP/EDtunnel)

>CFworker 是 cloudflare 推出的功能強大的容器，EDtunel 項目正是利用了 CFworker 的特性，使其成爲 VLESS 節點。  
>CFworker 節點的特性有:
>
>- 可自訂落地 IP
>- 解鎖 OpenAI
>- 解鎖 Netflix
>- IP 不固定
{: .prompt-info }

## 1.創建 cloudflare 賬號

1. 進入 [cloudflare](https://dash.cloudflare.com/sign-up) 注冊賬戶(有賬戶的跳過這一步)

## 2.創建 Worker

1. 點擊進入側邊欄的 Workers & Pages

2. 點擊 Create application

3. 再點擊 Create Worker

3. 隨便取個名字,最好不要取帶有 proxy 字樣的名字

4. 再次點擊 Deploy

5. 最後點擊 Edit code

6. 這樣就完成了 Worker 的創建

## 3.配置 Worker 内容

1. 打開 [EDtunel Worker.js](https://github.com/3Kmfi6HP/EDtunnel/blob/main/_worker.js) 檔案

2. 複製全選 js 檔案裏的内容

3. 返回你剛才創建的 Worker 編輯界面

4. 刪除默認文檔 Worker.js 中的全部文本,將剛才複製的内容粘貼上去

5. 然後回到頂部,找到 `let userID =` 這行代碼,將等號後面單引號裏的内容替換成新的 [uuid](https://www.uuidgenerator.net/version4) ,複製到記事本備用

6. 最後點擊右上角的 Save and deploy

## 4.導入訂閲鏈接

1. 等待 Save and deploy 按鈕變灰,點擊編輯欄右上角的 workers.dev

2. 打開後在網址後面添加 `/UUID(剛才複製的那個)`

3. 根據你需要的訂閲鏈接導入對應的[代理軟件](https://gholtsmxv.github.io/Application-proxy/)

4. 導入後打開編輯界面,關閉 tls ,把位址一項改爲 `icook.hk` 或 `www.visa.com.sg` ,端口改爲 80 或 8880 ,保存

5. 這時候運行代理,打開 [Google](https://www.google.com/) 測試是否成功.如果失敗,請確保每一步都嚴格按照教程操作.

>CFworker Proxy 的具體速度取決於你的**物理位置**和**運營商**,有些地區的運營商也可能會**阻斷** cloudflare 的服務,具體使用情況取決於**個人使用環境**.
{: .prompt-tip }
