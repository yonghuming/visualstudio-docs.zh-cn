---
title: "生成等于和 GetHashCode 方法重写的代码生成 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.openlocfilehash: 88ebbeed4af1d0ea79a27ff21f7ae38ec8c252c1
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2017
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>生成等于和 C# 中重写 GetHashCode 方法 #

**新增功能：**允许您生成**等于**和**GetHashCode**方法。

**何时：**时具有表示应进行比较的某些字段，而不是由内存中的对象位置的"值"的类型生成这些重写。

**原因：**如果你要实现的值类型，则应考虑重写 Equals 方法能够提高的性能通过 ValueType 上的 Equals 方法的默认实现。

如果你要实现的引用类型，则应考虑重写 Equals 方法，如果你的类型如下所示的基类型，如点、 字符串、 BigNumber，等等。

重写 GetHashCode 方法，以允许在哈希表中正常工作的类型。 在上阅读更多指南[相等运算符](/dotnet/standard/design-guidelines/equality-operators)。

**如何：**

1. 将光标置于类型声明中。

   ![突出显示的代码](media/overrides_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**生成 Equals(object)**或**生成 Equals 和相等 GetHashCode**从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**生成 Equals(object)**或**生成 Equals 和相等 GetHashCode**从预览窗口弹出窗口。
     * 单击 ![灯泡](media/bulb.png) 如果文本光标已在行中使用的类型声明的左边距中显示的图标。

   ![生成替代预览](media/overrides_preview.png)

1. 选择你想要生成的替代方法的成员：

    ![生成替代对话框](media/overrides_dialog.png)

    > [!TIP]
    > 你还可以选择从该对话框生成运算符，通过使用成员列表下方的复选框。

1. Equals 和 GetHashCode 替代将生成自动默认实现。

   ![生成方法结果](media/overrides_result.png)

## <a name="see-also"></a>请参阅

[代码生成 (C#)](../code-generation-csharp.md)  
[预览更改](../../ide/preview-changes.md)
