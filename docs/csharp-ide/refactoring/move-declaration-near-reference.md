---
title: "将声明附近参考-重构 (C#) 移动 |Microsoft 文档"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.openlocfilehash: f784ac9fec1dce1f21ba4b9f1f0e83b4b7deb001
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2017
---
# <a name="move-declaration-near-reference-in-c"></a>在 C# 中的引用附近的将声明 #
**新增功能：**使你可以更接近变量声明移动到其使用情况。

**何时：**具有可存在于较窄范围中的变量声明。

**原因：**您无法将保留它，但这样可能导致出现可读性问题或信息隐藏。 这是重构机会提高可读性。

**如何：**

1. 将光标放在变量声明中。

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**将附近引用声明移动**从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**将附近引用声明移动**从预览窗口弹出窗口。

1. 当您满意更改时，请按**Enter**或单击修复菜单中的，所做的更改将提交。

示例:
```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>另请参阅  
[重构 (C#)](../refactoring-csharp.md)  
[预览更改](../../ide/preview-changes.md)