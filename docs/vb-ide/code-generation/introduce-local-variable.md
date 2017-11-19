---
title: "引入本地变量的代码生成 (Visual Basic 中) |Microsoft 文档"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67302893dbebb65316b9c2aab09f70ddaa3e6567
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="introduce-a-local-variable-in-visual-basic"></a>介绍在 Visual Basic 中的本地变量
**新增功能：**便会立即生成一个本地变量来替换现有表达式。

**何时：**具有无法轻松地重用更高版本就好像在本地变量的代码。  

**原因：**可以复制并粘贴代码多次才能将它用于不同的位置，但它会执行一次该操作，将结果存储在本地变量中，并使用本地变量 throughought 好一些。 

**如何：**

1. 突出显示你想要分配给一个新的本地变量的表达式。

   ![突出显示的代码](media/local_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**引入本地 （的所有匹配项）*表达式** * 从预览窗口弹出窗口中，其中*表达式*是具有突出显示的代码。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**引入本地 （的所有匹配项）*表达式** * 从预览窗口弹出窗口中，其中*表达式*是具有突出显示的代码。
     * 单击 ![灯泡](media/bulb.png) 如果文本光标已在行中使用红色波形曲线的左边距中显示的图标。

   ![引入本地预览](media/local_preview.png)

   >[!TIP]
   >使用[**预览更改**](../../ide/preview-changes.md)底部的预览窗口来查看所有将在你的选择之前所做的更改的链接。

1. 局部变量将自动创建具有从其用法推断类型。  通过键入它为新的本地变量提供新名称。

   ![引入本地结果](media/local_result.png)

   >[!NOTE]
   >你可以使用**..所有匹配项...**菜单选项，以将替换所选表达式找到，而不仅仅是一个专门突出显示的每个实例。

## <a name="see-also"></a>另请参阅  
[代码生成 (Visual Basic)](../code-generation-vb.md)  
[预览更改](../../ide/preview-changes.md) 