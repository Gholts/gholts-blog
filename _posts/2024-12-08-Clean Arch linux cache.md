---
title: Arch linux 清理空間
date: 2024-12-08
categories: [Tutorial]
tags: [linux]
---

## ※ [Paru 項目地址](https://github.com/Morganamilo/paru)

以下的操作皆基於 Paru package manager 工作

## 查看目前快取的大小

```bash
du -sh /var/cache/pacman/pkg
```

## 清理已卸載的 Package 快取

```bash
paru -Sc
```

## 清理所有的 Package 快取

```bash
paru -Scc
```

## 清理無用的依賴 Package

```bash
paru -Rns $(paru -Qtdq)
```