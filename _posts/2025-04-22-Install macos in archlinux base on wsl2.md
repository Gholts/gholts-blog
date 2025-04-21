---
title: 在 WSL2 on Windows 中安裝 MacOS
date: 2025-04-22
---

# ※ [OSX-KVM 專案](https://github.com/kholia/OSX-KVM)

我一直都很想在 Windows 上跑一個 MacOS，但 PC 下透過虛擬機器執行 MacOS 效能不理想。我就想到 WSL2 中虛擬化一個 MacOS 應該會好不少（我沒有指望能效十分完美，但只是能用的程度）。

[OSX-KVM](https://github.com/kholia/OSX-KVM) 正是一個實現專案。

## 準備操作

安裝的第一步我就碰到了問題，專案 readme 提供的 required packages 是 apt 包管理器的包名，而我使用的是 Arch Linux。

```bash
sudo apt-get install qemu-system uml-utilities virt-manager git \
    wget libguestfs-tools p7zip-full make dmg2img tesseract-ocr \
    tesseract-ocr-eng genisoimage vim net-tools screen -y
```

我選擇了使用 ChatGPT 幫我搜尋整理了 pacman 和 aur 版本的對應包。其中遇到了一個坑，genisoimage 來自 cdrkit package。

然後就是跟著 readme 操作。

```bash
cd ~

git clone --depth 1 --recursive https://github.com/kholia/OSX-KVM.git

cd OSX-KVM

sudo modprobe kvm; echo 1 | sudo tee /sys/module/kvm/parameters/ignore_msrs

# CPU 二選一
sudo cp kvm.conf /etc/modprobe.d/kvm.conf  # for intel boxes only 我的 CPU 是 intel，所以執行這一條就好，反之第二條

sudo cp kvm_amd.conf /etc/modprobe.d/kvm.conf  # for amd boxes only
# ---

sudo usermod -aG kvm $(whoami)
sudo usermod -aG libvirt $(whoami)
sudo usermod -aG input $(whoami)
```
## 安裝系統

假設你還在`~/OSX-KVM`目錄下，執行`./fetch-macOS-v2.py`

我選擇的是 Sonoma (14)，但我推薦你選擇 Ventura (13)，因為他的效能更好。

等待下載完成後執行`dmg2img -i BaseSystem.dmg BaseSystem.img`轉換映像格式。

然後執行`qemu-img create -f qcow2 mac_hdd_ng.img 256G`建立一個虛擬硬碟映像。
我的 WSL2 預設對映存貯在 C 盤，所以我要將他移動到 D 盤`mv ~/mac_hdd_ng.img /mnt/d/wsl/`。

好了，readme 告訴我應該執行啟動指令碼了，但由於我移動了映象位置，我需要更改指令碼內容，順便重新分配一下系統資源。

更改系統資源
```sh
ALLOCATED_RAM="6144" # MiB
CPU_SOCKETS="2"
CPU_CORES="2"
CPU_THREADS="4"
```

由於我安裝的是 Sonoma，我還需要將`Penryn`替換為`Haswell-noTSX`

更改映像路徑，將`$REPO_PATH/mac_hdd_ng.img`替換為`/mnt/d/wsl/mac_hdd_ng.img`

大功告成！儲存執行。

然後不出意料你會得到這個錯誤。

```
QEMU 9.2.3 monitor - type 'help' for more information (qemu)
gtk initialization failed
```

逛了一會兒論壇找到了修復的方法。
先註釋掉`/etc/wsl.conf`中的`systemd=true`。但你也許需要 systemd 服務，跟著我做。
在`/etc/systemd/system/wslg.service`新增如下內容
```bash
[Unit]
Description=symlink /tmp/.X11-unix
After=systemd-tmpfiles-setup.service

[Service]
Type=oneshot
ExecStart=rmdir /tmp/.X11-unix
ExecStart=ln -s /mnt/wslg/.X11-unix /tmp/

[Install]
WantedBy=sysinit.target
```
然後執行`systemctl enable wslg`，退出 WSL2，在 PowerShell 執行`wsl --shutdown`。

修復就完成了，進入 WSL2 執行啟動指令碼，就會彈出 WSLg 視窗了。
關於這個錯誤，你可以檢視更多在這個 [Superuser 回帖](https://superuser.com/questions/1617298/wsl-2-running-ubuntu-x-server-cant-open-display/1834709#1834709) 檢視。

WSLg 執行後透過鍵盤選擇 base 系統使用`Disk Utility`工具格式化為`APFS`磁碟（不要選錯盤，是那個 200 多 GB 的！）

返回上一級繼續`install macOS`，等待直到進入 MacOS 的導覽畫面，enjoy！

## 還有更多嗎

推薦透過 [OSX-Optimizer](https://github.com/sickcodes/osx-optimizer) 最佳化 MacOS 系統（按需選擇即可）。

還有更多配置網路和其他可能遇到的問題在這個 [note](https://github.com/kholia/OSX-KVM/blob/master/notes.md) 下。

我還沒研究配置網路搭配`virt-manager`使用，就到這了。