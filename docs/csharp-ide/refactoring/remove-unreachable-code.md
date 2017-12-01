---
title: "删除无法访问代码的重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.openlocfilehash: d4dfc63000fe6f66135d452b9a64e14dc05101d9
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2017
---
# <a name="remove-unreachable-code-in-c"></a>在 C# 中删除无法访问的代码 #
**新增功能：**删除永远不执行的代码。

**何时：**程序具有到代码段，使该代码段不必要没有路径。

**原因：**消除是多余的代码从而提高可读性和可维护性和永远不执行。

**如何：**

1. 将光标置于出渐变式无法访问的代码中的任意位置：

![淡无法访问的代码](media/unreachablecode_faded.png)  

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**删除无法访问代码**从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**删除无法访问代码**从预览窗口弹出窗口。

1. 当您满意更改时，请按**Enter**或单击修复菜单中的，所做的更改将提交。

示例:
```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>另请参阅  
[重构 (C#)](../refactoring-csharp.md)  
[预览更改](../../ide/preview-changes.md)