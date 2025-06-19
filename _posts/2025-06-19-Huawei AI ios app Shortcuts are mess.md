---
title: 華為的智慧生活 App 是一個垃圾
date: 2025-06-19
---

## ※ [HUAWEI AI Life](https://apps.apple.com/us/app/id1266194141)

<img src="https://image.gholts.top/DA3C2A42-FB25-450E-8EAE-246CEC5AC872.png" alt="settings" width="138px" align="right">

幾年前，我入手了一盞 OPPLE 智慧檯燈。作為華為生態鏈的產品，它無法整合進 Home Assistant，只能透過華為自家的「智慧生活」app 來控制。

雖然 app 的操作還算可以接受，但每次調整設定都需點擊兩次才能進入選項介面，稍嫌繁瑣。幸好，app 提供了「一鍵直達」的捷徑功能，算是解決了這個小問題。

## 蛋疼的 Shortcut

但這個捷徑功能形同虛設。它需要兩次跳轉才能進入目標頁面，而且穩定性不佳，有時會卡住。

<img src="https://image.gholts.top/D5E59981-3AEB-41CE-909D-8E6BCE671E3C.png" alt="shortcut" width="138px" align="left">
<img src="https://image.gholts.top/5D43CEB4-98FA-4669-8F87-638864383A95.png" alt="shortcut2" width="138px">

為了最佳化這個過程，我想直接找出 App 的 URL Scheme。

## 找出 URL Scheme

找到建立捷徑的 Web Link：
```
https://smarthome.hicloud.com/device/guide/operation/appdesktop/content.html?dGl0bGU9VGFibGUgTGFtcCZpbWFnZT1odHRwczovL3NtYXJ0aG9tZS1kcmNuLmRiYW5rY2RuLmNvbS9kZXZpY2UvZ3VpZGUvMTM0RC9pY29uQi5wbmcmaGlsaW5rPWhpbGluazovL3VzZXJJZD0zMDA4NjAwMDU3MTUwNjM1MCxob21lSWQ9Y3V2OTQ2Y29qMTZ0M2E1dGpya3FnYW8sZGV2aWNlSWQ9MTc4ZmE1MzMtODMzZS00YjQ5LThkYmMtMjdiZTQwMDZjYWI0JmRvd25sb2FkPWl0bXMtYXBwczovL2l0dW5lcy5hcHBsZS5jb20vY24vYXBwL2lkaWQxMjY2MTk0MTQxP210PTgmYnRuVGl0bGU9U1RBUlQmbGFuZ3VhZ2U9ZW4=
```
透過 base64 解碼「?」後的引數：
<img src="https://image.gholts.top/20250619155630717.png" alt="base64decode" width="750px">

結果為（為方便閱讀經過換行處理）
```
title=Table Lamp
&image=https://smarthome-drcn.dbankcdn.com/device/guide/134D/iconB.png
&hilink=hilink://userId=30086000571506350,homeId=cuv946coj16t3a5tjrkqgao,deviceId=178fa533-833e-4b49-8dbc-27be4006cab4
&download=itms-apps://itunes.apple.com/cn/app/idid1266194141?mt=8
&btnTitle=START
&language=en
```
「hilink」這個 Key 後面就是我們要的 URL Scheme 了。

最終把 URL Scheme 扔進 Apple 自家的 Shortcut 軟體中建立一個捷徑，大功告成。

<img src="https://image.gholts.top/96941E7D-176A-4291-9BA9-277085F90443.png" alt="shortcut" width="138px">

## 效果對比：
<table border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td style="padding-right: 10px;"> <div>
        <div>Before</div>
        <img src="https://image.gholts.top/shortcutsBefore.gif" alt="shortcutsBefore" width="138px">
      </div>
    </td>
    <td>
      <div>
        <div>After</div>
        <img src="https://image.gholts.top/shortcutsAfter.gif" alt="shortcutsAfter" width="138px">
      </div>
    </td>
  </tr>
</table>