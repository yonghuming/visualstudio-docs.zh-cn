---
title: "版本控制"
description: "使用 Visual Studio for Mac 中的 Git 和 Subversion。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: a63ebdccc2a7cbde18715291a65ada613dc2c00e
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---

# <a name="version-control"></a>版本控制

版本控制系统用于管理各种不同版本中的文件，在软件开发中常常由多位开发者贡献。 任何版本控制系统 (VCS) 的主要目的都是找出一种解决方案，使所有用户都可同时对基本代码进行操作。

而任何版本控制系统的核心都是存储库，它可充当所有不同文件的中央数据存储，与文件服务器类似。 但又不同于文件服务器，存储库包含项目的整个历史记录和所做的所有修订。

如果存储库是中央数据存储，那么每个用户都具备一个可在其上操作的本地数据存储是完全合理的。 这被称为“工作副本”。 在 Visual Studio for Mac 中，工作副本将显示在计算机上，就像任何其他本地目录一样，使用户可以从任意文件读取数据或将数据写入这些文件。 但由于 Visual Studio for Mac 具有版本控制系统集成，因此可利用 Subversion 和 Git 的功能而无需离开 IDE。

Subversion 是一个集中式版本控制系统。 这表示，有一个服务器包含所有文件和修订，用户可从中签出任何文件的任何版本。 从远程 Subversion 存储库中签出文件时，用户将收到该时间点的存储库快照。

Git 是分布式版本控制系统，使团队可以同时在同一文档上工作。 这意味着可能有一个单一服务器包含所有文件，但从此中央源中签出存储库时，整个存储库都会被克隆到本地计算机。

# <a name="basic-concepts"></a>基本概念 

Visual Studio for Mac 支持 Git 和 Subversion 这两种版本控制系统。 以下链接的指南介绍了如何通过 Visual Studio for Mac 设置 Git 和 Subversion 存储库，以及简单的功能（如评审、提交和推送更改）。

* [设置 Git 存储库](~/set-up-git-repository.md) 
* [使用 Git](~/working-with-git.md)
* [设置 Subversion 存储库](~/set-up-subversion-repository.md)
* [使用 Subversion](~/working-with-subversion.md)
