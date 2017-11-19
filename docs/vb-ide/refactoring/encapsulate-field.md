---
title: "封装字段-重构 (Visual Basic 中) |Microsoft 文档"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 39a9ed11-363f-4dda-af3b-0affe6db1d42
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: VB
ms.openlocfilehash: 9575ad83ead4960016ba7814642cacb1db04ea4d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-a-field-in-visual-basic"></a>封装在 Visual Basic 中的字段
**新增功能：** ，可以将字段转换为一个属性，并更新该字段，以便使用新创建的属性的所有使用实例。

**何时：**你想要将字段移到一个属性，并更新对该字段的所有引用。  

**原因：**你想要为其他类访问提供到字段，但不希望能够直接访问这些类。  通过包装属性中的字段，你可以编写代码以验证分配的值，例如。

**如何：**

1. 突出显示，或将文本光标置于要封装的字段的名称：

   ![突出显示的代码](media/encapsulate_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl + R**，然后**Ctrl + E**。  （请注意，键盘快捷方式可能因所选的配置文件而有所不同。）
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**封装字段**预览窗口弹出窗口中的条目。
   * **鼠标**
     * 选择**编辑 > 重构 > 封装字段**。
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**封装字段**预览窗口弹出窗口中的条目。

   选择 | 描述
   --------- | -----------
   **封装字段 （并使用属性）** | 封装具有一个属性的字段，并更新要使用生成的属性的字段的所有使用实例
   **封装字段 （但仍使用字段）** | 封装具有一个属性的字段，但保留该字段的所有使用不变

   将立即创建属性并将更新对字段的引用，如果选择。

   > [!TIP]
   > 使用[**预览更改**](../../ide/preview-changes.md)可看到在提交到它之前，结果将是什么的弹出窗口中的链接。

   ![封装属性结果](media/encapsulate_result.png)

## <a name="see-also"></a>另请参阅  
[重构 (Visual Basic)](../refactoring-vb.md)  
[预览更改](../../ide/preview-changes.md)