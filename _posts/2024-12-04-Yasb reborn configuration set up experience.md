---
title: Yasb reborn configuration set up experience
date: 2024-12-04
categories: [Software Share]
tags: [yasb]
---

## ※ [Yasb reborn repository](https://github.com/amnweb/yasb)

>Yasb is a windows status bar like Linux gnome bar, *Foss* and configurable almost everthing
>There are all configurable files:
>- config.yaml
>- styles.css
>- theme.json
>and a log file:
>- yasb.log
>all files are in `C:/Users/{username}/.config/yasb/`
{: .prompt-info }

## 1.Installation

### Requirements

- Nerd Fonts. Install [Nerd Fonts](https://www.nerdfonts.com/font-downloads) (JetBrainsMono recommended)
- Windows 10 & 11

### Installer

- Download `.msi` file in github repo [relesases page](https://github.com/amnweb/yasb/releases/latest)
- Just run it

## 2.Configuration

- Visit [official wiki](https://github.com/amnweb/yasb/wiki/Configuration) and browse the page
- You can choose to use a theme files shared by others

I choose to use a theme file and configure of that when I started, named Yasb 001 Theme.

Oh you can find theme files on [yasb theme repo](https://github.com/amnweb/yasb-themes)

### Install theme

- Download theme files then unzip
- Selecte `config.yaml styles.css theme.json` copy and overwrite to `C:/Users/{username}/.config/yasb/`
- enjoy theme!

There is my [config.yaml](https://gist.github.com/Gholts/e9e55f2dfcc277db6af19bd8af377449)
>My configuration require this [styles.css](https://gist.github.com/Gholts/45cf5dd3e958292f9d7906a93389ec08)

There are screen settings in cofiguration line 12 and 56

`screens: ['H24T09P']`

![](https://image.gholts.top/2024-12-04_21-07-51.png)

`screens: ['DISPLAY2']`

![](https://image.gholts.top/2024-12-04_23-10-48.png)

If you have only one screen, you shoud delete *line 54 ~ line 92*

## 3.Enjoy

第一次嘗試寫英文 blog，有什麽不太對的地方可以在評論指出来