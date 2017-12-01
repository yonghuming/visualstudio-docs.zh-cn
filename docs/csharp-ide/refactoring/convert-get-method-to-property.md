---
title: "将 Get 方法转换为属性-重构 (C#) |Microsoft 文档"
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
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.openlocfilehash: d034b8835caf0a5e56a9ef32599cf9197f1e3e16
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2017
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>将 Get 方法转换为属性/将属性转换为 Get 方法
## <a name="convert-get-method-to-property"></a>将 Get 方法转换为属性
**新增功能：**允许你将 Get 方法转换为一个属性 （和 （可选） 你集方法），反之亦然。

**何时：**你有不包含任何逻辑 Get 方法。

**如何：**

1. 将光标置于你 Get 方法的名称。

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**方法替换属性**从预览窗口弹出窗口。 如果你有一个 Set 方法，你还可以将转换 Set 方法此时通过选择**替换 Get 方法和属性的 Set 方法**。
   * **鼠标**
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**方法替换属性**从预览窗口弹出窗口。 如果你有一个 Set 方法，你还可以将转换 Set 方法此时通过选择**替换 Get 方法和属性的 Set 方法**。

1. 如果您满意代码预览中的更改，请按**Enter**或单击修复菜单和所做的更改将提交。

示例:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>将属性转换为 Get 方法
**新增功能：**可以将属性转换为一个 Get 方法

**何时：**具有涉及多个立即设置和获取一个值的属性 

**如何：**

1. 将光标置于你 Get 方法的名称。

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**属性替换方法**从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**属性替换方法**从预览窗口弹出窗口。

1. 如果您满意代码预览中的更改，请按**Enter**或单击修复菜单和所做的更改将提交。

## <a name="see-also"></a>另请参阅  
[重构 (C#)](../refactoring-csharp.md)  
[预览更改](../../ide/preview-changes.md)