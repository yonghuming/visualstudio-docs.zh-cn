---
title: "将类型移动到匹配的文件的重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f58c34-c50f-4297-91b2-2e243380dcc9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9fa5a15f9c8e688c973594309efbfa6cb5d10e8b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="move-a-type-to-a-matching-file-in-c"></a>将一个类型移到 C# 中匹配的文件 #
**新增功能：**使你可以移动到具有相同名称的单独文件的所选的类型。

**何时：**在你想要单独的相同文件中有多个类、 结构、 接口、 等。  

**原因：**将多个类型放置在相同的文件可以使难以查找这些类型。  通过将类型移到具有相同名称的文件，代码变得更具可读性且更轻松地导航。

**如何：**

1. 突出显示，或将文本光标置于要移动的类型名称：

   ![突出显示的代码](media/movetype_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**移动类型设置为*TypeName*.cs**从预览窗口弹出窗口中，其中*TypeName*是你选择的类型的名称。
   * **鼠标**
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**移动类型设置为*TypeName*.cs**从预览窗口弹出窗口中，其中*TypeName*是你选择的类型的名称。

   类型将立即移动到具有该名称在你的解决方案的新文件。

   ![内联结果](media/movetype_result.png)

## <a name="see-also"></a>另请参阅  
[重构 (C#)](../refactoring-csharp.md)