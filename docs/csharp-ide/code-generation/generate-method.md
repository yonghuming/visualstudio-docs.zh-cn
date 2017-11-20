---
title: "生成的方法的代码生成 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 626db0d9c62fc606539fc9d72fc14c3651dca7ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-method-in-c"></a>在 C# 中生成方法 #
**新增功能：**允许您立即向类添加方法。 

**何时：**你引入一个新方法并想要正确地将其，自动声明。  

**原因：**可以声明的方法和参数然后再使用它，但此功能会自动生成的声明。 

**如何：**

1. 将光标放在行上： 有红色的波浪线，该值指示你已使用尚不存在的方法。

   ![突出显示的代码](media/method_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**生成方法**从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**生成方法**从预览窗口弹出窗口。
     * 将鼠标悬停在红色波形曲线和单击 ![灯泡](media/bulb.png) 显示的图标。
     * 单击 ![灯泡](media/bulb.png) 如果文本光标已在行中使用红色波形曲线的左边距中显示的图标。

   ![生成方法预览](media/method_preview.png)

   >[!TIP]
   >使用[**预览更改**](../../ide/preview-changes.md)底部的预览窗口来查看所有将在你的选择之前所做的更改的链接。

1. 与从其使用情况推断任何参数，将自动创建方法。

   ![生成方法结果](media/method_result.png)

## <a name="see-also"></a>另请参阅  
[代码生成 (C#)](../code-generation-csharp.md)  
[预览更改](../../ide/preview-changes.md)
