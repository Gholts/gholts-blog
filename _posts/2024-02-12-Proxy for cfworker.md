---
title: CFworker Proxy免費搭建
date: 2024-02-12
categories: [Tutorial, Proxy]
tags: [proxy]
---

## ※[EDtunel項目地址](https://github.com/3Kmfi6HP/EDtunnel)

>CFworker是cloudflare推出的功能強大的容器，EDtunel項目正是利用了CFworker的特性，使其成爲VLESS節點  
>而該節點的特性有:
>
>- 可自訂落地IP
>- 解鎖OpenAI
>- 解鎖Netflix
>- IP不固定

## 1.創建cloudflare賬號

- 進入[cloudflare](https://dash.cloudflare.com/sign-up)注冊賬戶(有賬戶的跳過這一步)

## 2.創建worker

- 點擊進入側邊欄的 Workers & Pages

- 點擊 Create application

- 再點擊 Create Worker

- 隨便取個名字,最好不要取帶有proxy字樣的名字

- 再次點擊 Deploy

- 最後點擊 Edit code

- 這樣就完成了worker的創建

## 3.配置worker内容

- 打開[EDtunel Worker.js](https://github.com/3Kmfi6HP/EDtunnel/blob/main/_worker.js)檔案

- 複製全選js檔案裏的内容

- 返回你剛才創建的worker編輯界面

- 刪除默認文檔worker.js中的全部文本,將剛才複製的内容粘貼上去

- 然後回到頂部,找到 `let userID =` 這行代碼,將等號後面單引號裏的内容替換成新的[uuid](https://www.uuidgenerator.net/version4),複製到記事本備用

- 最後點擊右上角的 Save and deploy

## 4.導入訂閲鏈接

- 等待Save and deploy按鈕變灰,點擊編輯欄右上角的 workers.dev

- 打開後在網址後面添加 `/UUID(剛才複製的那個)`

- 根據你需要的訂閲鏈接導入對應的[代理軟件](https://gholtsmxv.github.io/Application-proxy/)

- 導入後打開編輯界面,關閉tls,把位址一項改爲japan.com,端口改爲8880,保存

- 這時候運行代理,打開[Google](https://www.google.com/)測試是否成功.如果失敗,請確保每一步都嚴格按照教程操作.

>### tips
>CFworker Proxy的具體速度取決於你的**物理位置**和**運營商**,有些特殊的地方注定是用不了的(西藏),還有些地區的運營商也可能會**阻斷**cloudflare的服務,具體使用情況取決於**個人使用環境**.
