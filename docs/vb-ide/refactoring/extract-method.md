---
title: "提取方法重构 (Visual Basic 中) |Microsoft 文档"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 8ad16c15-432b-4b8c-86fd-5f31ad652d24
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: VB
ms.openlocfilehash: 56e83e6410093467349e4a45a01042133cc53555
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extract-a-method-in-visual-basic"></a>提取 Visual Basic 中的方法
**新增功能：**允许你的代码片段将转换为其自己的方法。

**何时：**某些需要从另一种方法调用的方法中具有的现有代码片段。  

**原因：**你无法复制/粘贴该代码，但这会导致重复。  更好的解决方案是重构到其自己的方法可以通过其他方法自由地调用该该片段。

**如何：**

1. 突出显示要提取的代码：

   ![突出显示的代码](media/extractmethod_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl + R**，然后**Ctrl + M**。  （请注意，键盘快捷方式可能因所选的配置文件而有所不同。）
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**提取方法**从预览窗口弹出窗口。
   * **鼠标**
     * 选择**编辑 > 重构 > 提取方法**。
     * 右键单击该代码，然后选择**重构 > 提取 > 提取方法**。
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**提取方法**从预览窗口弹出窗口。

   将立即创建方法。  从这里，你可以现在重命名方法只需通过键入新名称。

   > [!TIP]
   > 你还可以更新注释和其他字符串以使用此新的名称，以及[预览更改](../../ide/preview-changes.md)之前保存，使用中的复选框**重命名**显示在顶部的框右侧的 IDE。

   ![重命名方法](media/extractmethod_rename.png)

1. 如果你结果感到满意更改，单击**应用**按钮或按**Enter**并且所做的更改将提交。

## <a name="see-also"></a>另请参阅  
[重构 (Visual Basic)](../refactoring-vb.md)  
[预览更改](../../ide/preview-changes.md)