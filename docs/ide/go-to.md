---
title: "定位 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3b812629bf0f655f39c35a56eb1b3ca9113303a6
ms.openlocfilehash: 8bf6d49b21d128d15f5312fb230d4a8e7a8195af
ms.lasthandoff: 03/01/2017

---

# <a name="go-to"></a>转到
你可以采用多种方法在 Visual Studio IDE 中轻松定位代码，包括使用键盘和鼠标。

<!-- VERSIONLESS -->
## <a name="go-to-all"></a>转到全部
此功能存在于 Visual Studio 2017 及更高版本。  它使你能够浏览代码以查找正在寻找的特定位。  你可以在简单统一的界面内搜索特定的行、类型、符号、文件等。

### <a name="how-to-use"></a>使用方法
* **键盘**
  * 按 **Ctrl+** 或 **Ctrl+T**。  （请注意，键盘快捷方式可能因所选的配置文件而有所不同。）
* **鼠标**
  * 选择“编辑”>“转到”>“转到全部”。

默认情况下将在 IDE 的右上方显示一个小的窗口。

![转到全部](media/gotoall.png)

可以在此窗口中使用多种方法进行搜索：
* 使用文本框下面所选的[筛选图标](#filtered-searches)输入不带前缀的文本进行搜索。
* 输入[前缀](#filtered-searches)，后跟文本进行搜索。
* 输入一个问号 (?) 来获取更多帮助。
  ![转到全部帮助](media/gotoall_help.png)

### <a name="filtered-searches"></a>经过筛选的搜索
若要将搜索范围缩小到特定类型，可以在键入时使用前缀，或使用搜索窗口下面的图标，如下所示。

前缀 | 图标 | 快捷键 | 说明
:----: | ---- | -------- | ---
#      | ![符号图标](media/gotoall_symbolicon.png) | Ctrl+1、Ctrl+S | 查找匹配的符号
f      | ![文件图标](media/gotoall_fileicon.png)     | Ctrl+1、Ctrl+F | 查找匹配的文件名
m      | ![成员图标](media/gotoall_membericon.png) | Ctrl+1、Ctrl+M | 查找匹配的成员
T      | ![类型图标](media/gotoall_typeicon.png)     | Ctrl+1、Ctrl+T | 查找匹配的类型
:      | ![行图标](media/gotoall_lineicon.png)     | Ctrl+G         | 转到输入的行号

### <a name="search-locations"></a>搜索位置
若要将搜索范围缩小到特定位置，请使用两个文档图标。

图标 | 描述
---- | ---
![当前文档](media/gotoall_currentdocument.png) | 仅搜索当前文档
![外部文档](media/gotoall_external.png) | 除了项目/解决方案中的文档外还搜索外部文档

### <a name="settings"></a>设置
单击齿轮图标 ![齿轮图标](media/gotoall_gear.png) 此图标位于右下方，使用此图标可以更改功能的工作原理。

设置 | 说明
------- | ---
使用预览选项卡 | 在 IDE 的预览选项卡中立即显示所选的项
显示详细信息    | 在窗口的文档注释中显示项目、文件、行和摘要信息
使窗口居中   | 将窗口移到 IDE 的中心而不是右上方
<!-- END VERSIONLESS -->

## <a name="go-to-definition"></a>转到定义
导航到某个类型的源，并在新选项卡中打开结果：

输入        | 函数 
------------ | ---
**键盘** | 将文本游标放置在类型名称内部的某个位置，然后按 **F12**
**鼠标**    | 右键单击类型名称，再选择“转到定义”。

## <a name="peek-definition"></a>查看定义
在弹出式窗口中而不是一个新选项卡中预览类型的定义：

输入        | 函数 
------------ | ---
**键盘** | 将文本游标放置在类型名称内部的某个位置，然后按 **Alt+F12**
**鼠标**    | 右键单击类型名称，再选择“查看定义”。

如果在弹出式窗口中查看另一个定义，则将启动痕迹路径，即使用弹出式窗口上方显示的圆形菜单和箭头进行导航。  有关详细信息，请参阅[如何：使用查看定义 (Alt+F12) 查看和编辑代码](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)。

## <a name="go-to-implementation"></a>转到实现
从一个基类或类型导航到其实现。  如果有多个实现，则可以看到它们在“查找符号结果”窗口中列出：

输入        | 函数 
------------ | ---
**键盘** | 将文本游标放置在类型名称内部的某个位置，然后按 **Ctrl+F12**
**鼠标**    | 右键单击类型名称，再选择“转到实现”。

## <a name="find-all-references"></a>查找所有引用
查找要使用方法/属性/变量的所有位置。  可以使用此操作验证死代码，并检查大型重构可能的副作用。  按 **F8** 可在结果之间跳转。

输入        | 函数 
------------ | ---
**键盘** | 将文本游标放置在类型名称内部的某个位置，然后按 **Ctrl+K、R**
**鼠标**    | 右键单击类型名称，再选择“查找全部引用”。

## <a name="navigating-results"></a>导航结果
使用 Visual Studio 的导航功能时，可以在堆栈中向前和向后导航：

输入        | 函数 
------------ | ---
**Ctrl+-**          | 在堆栈中向后导航
**Ctrl+Shift+-**    | 在堆栈中向前导航

你还可以使用“查看”>“向后导航”和“查看”>“向前导航”菜单项。
