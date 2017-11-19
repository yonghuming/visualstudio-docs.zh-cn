---
title: "重命名-重构 (Visual Basic) |Microsoft 文档"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abf1565b-c7b7-4d45-b3d3-a438a836c70e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: VB
ms.openlocfilehash: 35313f036e1f324d3f8908a4527cd3a2ad64ae52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>重命名 Visual Basic 中的代码符号
**新增功能：**允许你重命名代码符号，如字段、 局部变量、 方法、 命名空间、 属性和类型的标识符。

**何时：**你想要安全地将内容无需查找所有实例，并复制/粘贴新名称重命名。  

**原因：**中复制和粘贴在整个项目的新名称很可能会导致错误。  此重构工具将准确地执行重命名操作。

**如何：**

1. 突出显示，或将文本光标置于要重命名的项：

   ![突出显示的代码](media/rename_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl + R**，然后**Ctrl + R**。  （请注意，键盘快捷方式可能因所选的配置文件而有所不同。）
   * **鼠标**
     * 选择**编辑 > 重构 > 重命名**。
     * 右键单击该代码，然后选择**重命名**。

1. 将该项重命名只需通过键入新名称。

   ![重命名动画](media/rename_rename.png)

   > [!TIP]
   > 你还可以更新注释和其他字符串以使用此新的名称，以及[预览更改](../../ide/preview-changes.md)之前保存，使用中的复选框**重命名**显示在顶部的框右侧的 IDE。

1. 如果你结果感到满意更改，单击**应用**按钮或按**Enter**并且所做的更改将提交。

> [!NOTE]
> 如果你使用的名称已存在将导致冲突，**重命名**IDE 中的框将向您发出警告。
>
> ![重命名冲突](media/rename_conflict.png)

## <a name="see-also"></a>另请参阅  
[重构 (Visual Basic)](../refactoring-vb.md)  
[预览更改](../../ide/preview-changes.md)