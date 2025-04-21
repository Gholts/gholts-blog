---
title: 不簡單的 Windows 11 LTSC 安裝和客製化
date: 2025-03-24
---

## 为什么要重灌 Windows

我這臺電腦的系統還是 2022 年安裝的 Windows 11 Pro 22H2。歷經了三年的時光，這部系統被我客製化到盡頭，但是也出過不少意外，當然也和 Windows 的這種 bug 和系統設定扭曲和玄學的地方很多有關就是了。我沒辦法繼續忍受系統中各種不相容和錯誤的存在，比如 Windows player 始終沒辦法安裝被 iCloud 安裝器識別到！！還有 wsl2 一更新就破壞了整個 linux 環境，導致我還要重新安裝和配置環境。諸如此類多到數不過來。

但我終究離不開 Windows，單遊戲的需求就足夠把我鎖在 Windows 了。所以我覺得與其「勉強用」，不如從頭再來一次，把所有的配置都理清，規範各種配置的方式。我認為這是維持一個系統可用性與便利性最好的方式和重建。

## 從選擇系統映象開始

__首先普通的消費者映像先 Pass 掉__。因為就對於我來說，一個系統最重要的就是「幹好自己的事，沒有多餘的東西」，可 Windows 11 消費者版本完全無法做到這一點！各種臃腫的元件，各種完全不必要的軟體，還有一大堆廣告！完全在我心中是不合格的典範。

__其次就是已經過時的系統 — Windows 10（任何版本）__。Windows 11 真的有太多美學是我無法放棄的，相比起它 Windows 10（或更老）根本就是醜到爆。就算有一些好處，比如更穩定的機能，更多的檢索諮詢，對遊戲來說相容性更好。但我沒辦法選擇一個不符合我審美的系統，不然每天使用就是對自己的折磨。

__最終只剩下 Windows 11 LTSC 和 IoT__。確切來說應該是分為 Enterprise LTSC 與 IoT Enterprise LTSC / IoT Enterprise Subscription LTSC（僅限最新發表的 Windows 11 LTSC 2024 系列）。

<details> <!--  Differences between IoT and Non-IoT Windows Enterprise LTSC   -->
<summary><strong>具體差別可以看下表</strong></summary>
<blockquote>
<table>
<thead>
<tr>
<th>Features</th>
<th>Enterprise LTSC</th>
<th>IoT Enterprise LTSC / IoT Enterprise Subscription LTSC</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>TPM / Secure boot / UEFI / 4GB RAM</strong></td>
<td>All required</td>
<td><a href="https://learn.microsoft.com/windows/iot/iot-enterprise/Hardware/System_Requirements?tabs=Windows11LTSC#optional-minimum-requirements">Not Required</a> 🎉 <br>Also not required by <a href="https://massgrave.dev/windows_11_links">IoT Enterprise 24H2 (Non-LTSC)</a></td>
</tr>
<tr>
<td><strong>Automatic Device Encryption</strong></td>
<td>Enabled</td>
<td>Disabled</td>
</tr>
<tr>
<td><strong>Update Support</strong></td>
<td>5 Years</td>
<td>10 Years</td>
</tr>
<tr>
<td><strong>Reserved Storage Feature</strong></td>
<td>Enabled</td>
<td>Disabled</td>
</tr>
<tr>
<td><strong>Digital License (HWID)</strong></td>
<td>Not supported</td>
<td>Supported</td>
</tr>
<tr>
<td><strong>Uninstallable Edge outside of EEA</strong></td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td><strong>2 Simultaneous RDP Sessions</strong></td>
<td>No</td>
<td>Yes</td>
</tr>
</tbody>
</table>
<ul>
<li>The only difference between IoT Enterprise LTSC and IoT Enterprise Subscription LTSC is that the subscription edition supports a subscription license.</li>
<li>You can change the editions to each other (IoT and Non-IoT Windows Enterprise LTSC) only by inserting the corresponding edition key.</li>
<li>IoT LTSC edition ISO&#39;s are available in English language only. You can install Non-IoT LTSC in another language and later install IoT LTSC key &gt; <code>CGK42-GYN6Y-VD22B-BX98W-J8JXD</code> in activation page in Windows settings to change the edition.</li>
</ul>
</blockquote>
</details>

對於我來說，能過透過認證到 EEA 區域解鎖刪除 edge 的功能是十分重要的，所以我最後選擇了 Windows 11 Enterprise LTSC 2024 EN_US 版本。

要注意的是，LTSC 版本缺少了一些功能，例如 Microsoft Store，。
可以透過以管理員啟動的 PowerShell 執行`wsreset -i`安裝。
還可以透過安裝 [App Installer](https://apps.microsoft.com/detail/9nblggh4nns1) 以更加方便的直接使用 Winget 和支援 .appx 格式的安裝包。

>如果以上安裝方法出錯，可以嘗試透過手動安裝這個 [安裝包](https://github.com/stdin82/htfx/releases/tag/v0.0.24), 它的提供者是 abbodi1406。

## 0. 備份資料

以下是我的備份列表

<details><summary><strong>備份系統客製化配置</strong></summary>
<ol>
<li>(^///^)<ul>
<li><a href="https://github.com/microsoft/terminal/releases/latest">Terminal</a><ul>
<li><a href="https://draculatheme.com/windows-terminal">Profile Schemes</a><ul>
<li><a href="https://github.com/SpaceTimee/Fusion-JetBrainsMapleMono/releases/latest/download/JetBrainsMapleMono-NF-XX-HT.zip">JetBrains Maple Mono</a> - <a href="https://github.com/SpaceTimee/Fusion-JetBrainsMapleMono">注意事項</a></li>
</ul>
</li>
<li><a href="https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows">Powershell</a></li>
<li><a href="https://git-scm.com/downloads/win">Git</a></li>
<li><a href="https://www.python.org/downloads/">Python</a></li>
<li><a href="https://github.com/nikhil-swamix/TerminalProfileManager">Terminal Profile Manager</a></li>
<li><a href="https://github.com/fastfetch-cli/fastfetch">Fastfetch</a> - <code>winget install fastfetch</code></li>
<li><a href="https://starship.rs/zh-TW/guide/">Starship</a> - <code>winget install --id Starship.Starship</code></li>
</ul>
</li>
<li><a href="https://windhawk.net/download">Windhawk 模組及配置</a></li>
<li><a href="https://winaerotweaker.com/">WinaeroTweaker 設定</a></li>
<li><a href="https://github.com/zhongyang219/TrafficMonitor/releases/latest">TrafficMonitor</a></li>
<li><a href="https://github.com/xanderfrangos/twinkle-tray/releases/latest">Twinkle Tray</a></li>
<li><a href="https://github.com/File-New-Project/EarTrumpet">EarTrumpet</a> - <code>winget install File-New-Project.EarTrumpet</code></li>
<li><a href="https://www.flowlauncher.com/">Flow.Launcher</a></li>
<li><a href="https://getsharex.com/">ShareX</a></li>
<li><a href="https://github.com/RamonUnch/AltSnap/releases/latest">AltSnap</a></li>
<li><a href="https://github.com/amir1376/ab-download-manager/releases/latest">AB Download Manager</a></li>
<li><a href="https://github.com/microsoft/PowerToys/releases/latest">PowerToyz</a></li>
<li><a href="https://github.com/MrBeanCpp/AltTaber/releases/latest">AltTaber</a></li>
<li><a href="https://store.steampowered.com/about/">Wallpaper Engine</a></li>
</ul>
</li>
</ol>

</details><details><summary><strong>備份常用軟體和配置</strong></summary>
<ol>
<li>(∪.∪ )...zzz<ul>
<li><a href="https://github.com/Alex313031/Thorium-Win/releases/latest">Thorium</a></li>
<li><a href="https://github.com/rime/weasel/releases/latest">Rime</a></li>
<li><a href="https://www.bandisoft.com/bandizip/old/6/">Bandizip</a></li>
<li><a href="https://github.com/Klocman/Bulk-Crap-Uninstaller/releases/latest">Bulk Crap Uninstaller</a></li>
<li><a href="https://diskanalyzer.com/download">Wiztree</a></li>
<li><a href="https://github.com/d2phap/ImageGlass/releases/latest">ImageGlass</a></li>
<li><a href="https://www.videolan.org/vlc/">Vlc</a></li>
<li>[Spotify] - <code>iex &quot;&amp; { $(iwr -useb &#39;https://raw.githubusercontent.com/SpotX-Official/spotx-official.github.io/main/run.ps1&#39;) } -new_theme&quot;</code><ul>
<li><a href="https://spicetify.app/docs/getting-started">Spicetify</a> - <code>iwr -useb https://raw.githubusercontent.com/spicetify/cli/main/install.ps1 | iex</code></li>
</ul>
</li>
<li><a href="https://discord.com/download">Discord</a><ul>
<li><a href="https://vencord.dev/download">Vencord</a></li>
</ul>
</li>
<li><a href="https://github.com/AyuGram/AyuGramDesktop/releases/latest">Ayugram</a></li>
<li><a href="https://github.com/localsend/localsend/releases/latest">LocalSend</a></li>
<li><a href="https://code.visualstudio.com/docs/?dv=win64">Visual Studio Code</a></li>
<li><a href="https://github.com/Molunerfinn/PicGo/releases/latest">PicGo</a></li>
<li><a href="https://pc.weixin.qq.com/?lang=en_US">Wechat</a><ul>
<li><a href="https://github.com/zetaloop/BetterWX">BetterWX</a></li>
</ul>
</li>
<li><a href="https://im.qq.com/pcqq/index.shtml">QQ</a><ul>
<li><a href="https://t.me/bqqnt/63">Better-qqnt</a> - <a href="https://t.me/bqqnt/4">注意事項</a></li>
</ul>
</li>
<li><a href="https://gravesoft.dev/office_c2r_links#chinese-traditional-zh-tw">Office</a></li>
<li><a href="https://www.audacityteam.org/download/windows/">Audacity</a></li>
<li><a href="https://kdenlive.org/zh/download-zh/">Kdenlive</a></li>
<li><a href="https://www.gimp.org/downloads/">GIMP</a></li>
<li><a href="https://github.com/Tichau/FileConverter/releases/latest">File Converter</a></li>
<li><a href="https://obsproject.com/download">OBS</a></li>
<li><a href="https://www.virtualbox.org/wiki/Downloads">Oracle VirtualBox</a></li>
<li><a href="https://github.com/LizardByte/Sunshine/releases/latest">Sunshine</a></li>
</ul>
</li>
</ol>

</details><details><summary><strong>其他檔案</strong></summary>
<ol>
<li><p>這個分類就是專門放所有的相片，影片等其他檔案。</p>
<ul>
<li><a href="https://prismlauncher.org/download/windows/">PrismLauncher</a></li>
<li><a href="https://www.lunarclient.com/download">Lunar</a></li>
<li>Library 庫檔案夾</li>
</ul>
</li>
</ol>

</details>

## 1. 安裝系統

我選擇了用 Rufus 寫入系統映象到隨身碟內，寫入時勾選了以下客製化配置。

![](https://image.gholts.top/rufus-4.6p_FAJ667c6HP.png)

進入 OOBE 階段後，Region 選擇 [EEA 特區](https://wikipedia.org/wiki/European_Economic_Area)（例如我選擇 Belgium）

![](https://image.gholts.top/20250324083305154.png)

然後無腦下一步進入系統，就會發現 Edge 瀏覽器可以解除安裝了。（在刪除之前記得先下載一個瀏覽器安裝包，不然你沒瀏覽器可用了）

![](https://image.gholts.top/20250324084851811.png)

然後就是開啟 Powershell 執行`wsreset -i`等待 Microsoft Store 下載完成，安裝 [App Installer](https://apps.microsoft.com/detail/9nblggh4nns1)。

接著執行`irm https://get.activated.win | iex`啟用 Windows 許可。

接著安裝以下的擴充套件 ~~（我好奇為什麼安裝時間會變成 9/10/2023）~~

![](https://image.gholts.top/So0gBQerA4.png)

最後透過 [NVCleanstall](https://www.techpowerup.com/download/techpowerup-nvcleanstall/) 安裝 NVIDIA 驅動程式，這個軟體允許你客製化驅動程式安裝內容，你可以隨意選擇要安裝什麼。比如可以安裝不帶有 [NVIDIA App](https://www.nvidia.com/en-us/software/nvidia-app/) 的驅動程式。

## 2. 客製化系統

0. 主題模式為深色

1. 系統字型我選用的是 [JetBrains Maple Mono](https://github.com/SpaceTimee/Fusion-JetBrainsMapleMono/releases/latest/download/JetBrainsMapleMono-NF-XX-HT.zip) - [配置方法](https://www.elevenforum.com/t/change-default-system-font-in-windows-11.8590/)

2. 系統主題使用了 [pi11z for Windows 11](https://www.deviantart.com/niivu/art/pi11z-for-Windows-11-1084568949) - [配置方法](https://www.deviantart.com/niivu/art/How-to-install-Windows-10-or-11-Themes-708835586)
	- 我選擇透過 [SecureUxTheme](https://www.deviantart.com/users/outgoing?https://github.com/namazso/SecureUxTheme) 安裝主題
	- 我選擇的是 pi11z round - Night
	- 另外使用 [OldNewExplorer](https://www.deviantart.com/users/outgoing?https://msfn.org/board/topic/170375-oldnewexplorer-119/) 修補一些外觀問題 ![](https://image.gholts.top/20250324091414142.png)

3. 透過使用 [Mica for Everyone v1.3.1.2](https://github.com/MicaForEveryone/MicaForEveryone/releases/tag/v1.3.1.2) 讓所有視窗標題欄變為深色
>我不選擇最新的 WinUI 3 版本是因為，它目前還無法以管理員自啟動，我不得不選擇 v1 版本。

我只更改了以下配置，刪除了多餘的 Rules ![](https://image.gholts.top/20250324092008584.png)

4. 系統游標是 [macOS cursors for Windows](https://www.deviantart.com/antiden/art/macOS-cursors-for-Windows-701736062)

5. [Windhawk](https://windhawk.net/download)
	- [Winhawk 配置檔案](https://github.com/Gholts/dotfiles)

6. 桌布 - [Wallpaper Engine](https://store.steampowered.com/app/431960/Wallpaper_Engine/)
	- [Apple MacOs Mojave Day/Night](https://steamcommunity.com/sharedfiles/filedetails/?id=1869208500)
		- 主熒幕配置 
		![](https://image.gholts.top/20250324095743399.png)
		- 第二塊熒幕
		![](https://image.gholts.top/20250324095832374.png)

7. [AltSnap](https://github.com/RamonUnch/AltSnap/releases/latest) - 視窗便捷拖動

8. [Flow.Launcher](https://www.flowlauncher.com/) - [onsetGlaze](https://github.com/abhidahal/onsetGlaze.flow) - 類似 MacOS 中的 Spotlight

9. [AltTaber](https://github.com/MrBeanCpp/AltTaber/releases/latest) - MacOS 風格的多工切換器

10. [Vencord](https://vencord.dev/download) - Discord 客製化

11. [Spicetify](https://spicetify.app/docs/getting-started) - `iwr -useb https://raw.githubusercontent.com/spicetify/cli/main/install.ps1 | iex` - Spotify 客製化

12. [TrafficMonitor](https://github.com/zhongyang219/TrafficMonitor/releases/latest) - 網速指示器

13. [Nilesoft Shell](https://github.com/moudey/Shell) - 更好的右鍵選單

14. [Twinkle Tray](https://github.com/xanderfrangos/twinkle-tray/releases/latest) - 快捷調整熒幕亮度

15. [EarTrumpet](https://github.com/File-New-Project/EarTrumpet) - `winget install File-New-Project.EarTrumpet`

## 3. The End

最後放一下效果圖：

![](https://image.gholts.top/explorer_iqs7T29Ok5.jpg)
![](https://image.gholts.top/20250324104327747.png)
![](https://image.gholts.top/20250324104728200.png)
![](https://image.gholts.top/20250408090138266.png)
![](https://image.gholts.top/20250324104400532.png)
![](https://image.gholts.top/20250324104435026.png)
