---
title: "代码段"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 1f2ee1d440ad1c7d8cd75ae9194c651f2fc16a41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="code-snippets"></a>代码片段 

代码片段通常被称为“代码模板”，对高效编程很有帮助，因为它们支持插入和编辑预编写的代码块。 使用代码片段，可以非常方便地快速添加常用模式，甚至还可在使用不熟悉的语法进行开发时非常方便地学习新模式。 针对 C#、F#、HTML、XML、Python 和 Razor 提供了模板。

本部分介绍如何创建、插入和使用代码片段。

## <a name="inserting-a-snippet"></a>插入代码片段

可通过不同的方法添加代码片段，下面介绍了其中一些方法：
 
* **Tab 展开** - 开始键入模板名，从列表中选择它并按“TAB TAB”添加：
 
  ![代码中的 Tab 展开](media/source-editor-image13.png)

* **工具箱** - 使用工具箱面板列出所有代码片段。 将任意模板从工具箱拖动到源代码中的正确位置：

 ![工具箱中的代码片段](media/source-editor-image14.png)

* **插入模板命令** - 目前没有为插入模板设置默认的键绑定。 要创建一个键绑定，请浏览到“Visual Studio”>“首选项...”>“键绑定”，并搜索 `template`。 这会将所需键绑定添加到“编辑绑定”字段中，然后单击“应用”：

 ![插入模板命令](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>创建新模板

虽然有多种语言的许多模板可供使用和编辑，但也可通过导航到“Visual Studio”>“首选项”>“文本编辑器”>“代码片段”来添加新模板：

![插入新模板](media/source-editor-image12.png)
