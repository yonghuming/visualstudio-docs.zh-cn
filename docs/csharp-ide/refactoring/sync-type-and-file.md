---
title: "同步类型和文件名的重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48172dd7-24a5-4884-8a73-f92497ad6a0d
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.openlocfilehash: ee37983575aa82abb764d57006cdabd094ea6497
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-c"></a>同步到文件名或 C# 中的类型文件名的类型 #

<!-- VERSIONLESS -->
**此功能是可用在 Visual Studio 2017 及更高版本。此外，.NET 标准项目是尚不支持用于此重构。**

**新增功能：**允许你重命名类型以匹配文件名，或重命名它包含的类型匹配的文件名。

**何时：**已重命名文件或类型和相应的文件或类型以匹配尚未尚未更新。 

**原因：**置于不同的名称或进行相反的转换，因此很难查找你正在寻找的内容的文件类型。  通过重命名该类型或文件名，代码变得更具可读性且更轻松地导航。

**如何：**

1. 突出显示，或将文本光标置于要同步的类型名称：

   ![突出显示的代码](media/synctype_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**重命名文件*TypeName*.cs**从预览窗口弹出窗口中，其中*TypeName*是你选择的类型的名称。
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**重命名类型设置为_Filename_** 从预览窗口弹出窗口中，其中*Filename*是当前文件的名称。
   * **鼠标**
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**重命名文件*TypeName*.cs**从预览窗口弹出窗口中，其中*TypeName*是你选择的类型的名称。
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**重命名类型设置为_Filename_** 从预览窗口弹出窗口中，其中*Filename*是当前文件的名称。

   类型或文件将立即被重命名。  在下面的文件的示例**MyClass.cs**已重命名为**MyNewClass.cs**以匹配的类型名称。

   ![内联结果](media/synctype_result.png)

## <a name="see-also"></a>另请参阅  
[重构 (C#)](../refactoring-csharp.md)
