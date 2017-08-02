---
title: "代码样式和快速操作 | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: BrianPeek
ms.author: brpeek
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
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
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: acc01617fffd7465cee01267482112aac5e352fc
ms.lasthandoff: 03/27/2017

---

# <a name="code-styles-and-quick-actions"></a>代码样式和快速操作
可按如下方法设置 C# 和 Visual Basic 项目的代码样式首选项：打开“工具”>“选项”窗口，然后选择“文本编辑器”>“C#/Basic”>“代码样式”>“常规”。  此窗口中设置的选项适用于本地计算机。  列表中的每一项都会显示所选首选项的预览，如下所示。

![代码样式选项](~/ide/media/code-style-quick-actions-dialog.png)

对于每个项，可使用每行相应的下拉列表设置“首选项”和“严重性”。  可将严重性设置为“无”、“建议”、“警告”或“错误”，Visual Studio 会作出相应反应。  如果要对这些代码样式使用[快速操作](quick-actions.md)以自动将代码重写为首选样式，请务必将其设置为除“无”以外的其他选项，以便在使用非首选样式时显示灯泡图标 ![小灯泡图标](~/ide/media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall")。  然后，通过单击灯泡图标或按“Ctrl+.”即可应用这些首选项， 前提是光标位于相应的代码行上。

也可以通过 [EditorConfig](editorconfig-code-style-settings-reference.md) 文件管理 .NET 的代码样式设置。  在此情况下，将优先采用 EditorConfig 文件中的设置，而“选项”窗口中的所选设置将成为后备设置。  可使用此文件为整个存储库或团队强制执行和配置代码样式。

# <a name="see-also"></a>另请参阅
* [快速操作](quick-actions.md)
