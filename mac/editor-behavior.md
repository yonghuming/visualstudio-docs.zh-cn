---
title: "编辑器行为"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 894bcbe66bd071bff1a6d904759f468b519da0f2
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---

# <a name="editor-behavior"></a>编辑器行为

可将编辑器行为设置为允许代码的格式与写入方式相同。 可在“Visual Studio”>“首选项...”>“文本编辑器”>“行为”下设置这些操作，以下介绍了一些常用的功能：

![编辑器行为选项](media/source-editor-image9.png)

*  创建新的类、方法或属性时，会自动将匹配的右大括号添加到代码。 选中此选项时，键入 `{` 将自动添加 `}`。
* 按下分号或大括号等字符会触发即时生成的代码格式，模拟已设置的格式首选项。
* 也可以选择在保存文件时设置其格式，该方法允许按需写入代码，让 IDE 负责按现有的首选项设置代码格式。
* 可将缩进设置为“无”、“自动”或“智能”。 这些设置会执行以下操作：
 * 无 - 将脱字号设置到下一行的起始位置
 * 自动 - 将脱字号设置到下一行的同一列
 * 智能 - 基于代码在下一行缩进
* 不同 OS 有不同的断字行为，出于导航目的，文本编辑器需要知道字开始或结束的位置。 可以将格式设置为 Unix 或 Windows。

也可以为 XML、CSS、HTML 和 JSON 设置格式规则。
