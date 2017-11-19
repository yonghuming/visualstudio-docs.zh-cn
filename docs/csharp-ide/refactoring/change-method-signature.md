---
title: "更改方法签名的重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: b4f45f9d-9c8f-46ae-99f7-7705c6d90b6e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: csharp
ms.openlocfilehash: 9ed72704c37fcfc5d0c48ba17937f5b06097ce0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="change-a-method-signature-in-c"></a>更改 C# 中的方法签名 #
**新增功能：**允许您删除或更改该方法的参数的顺序。

**何时：**你想要移动或删除当前正在使用中的不同位置的方法参数。  

**原因：**但你无法手动删除和重新排序参数，然后查找到该方法的所有调用和更改它们一个由一，可能导致错误。  此重构工具将自动执行任务。

**如何：**

1. 突出显示，或将文本光标置于要修改的方法或其用法之一的名称：

   ![突出显示的代码](media/changesignature_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl + R**，然后**Ctrl + V**。  （请注意，键盘快捷方式可能因所选的配置文件而有所不同。）
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**更改签名**从预览窗口弹出窗口。
   * **鼠标**
     * 选择**编辑 > 重构 > 删除参数**。
     * 选择**编辑 > 重构 > 重新排列参数**。
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**更改签名**从预览窗口弹出窗口。

1. 在**更改签名**对话框弹出，你可以使用右侧按钮更改方法签名：

   ![更改签名对话框](media/changesignature_dialog.png)

   | Button | 描述
   | ------ | ---
   | **启动/关闭** | 将所选的参数在列表中上下移动
   | **移除**  | 从列表中删除所选的参数
   | **还原** | 将所选的超过扩展参数还原到列表

   > [!TIP]
   > 使用[**预览引用更改**](../../ide/preview-changes.md)复选框可看到在提交到它之前，结果将是什么。

1. 当完成后时，按**确定**按钮进行的更改。

   ![更改签名结果](media/changesignature_result.png)

## <a name="see-also"></a>另请参阅  
[重构 (C#)](../refactoring-csharp.md)  
[预览更改](../../ide/preview-changes.md)