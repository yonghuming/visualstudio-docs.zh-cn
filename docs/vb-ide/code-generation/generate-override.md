---
title: "生成的重写的代码生成 (Visual Basic 中) |Microsoft 文档"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8a7658ff8e2f573f2da6ff3197b6a11f3b3a0a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="generate-an-override-in-visual-basic"></a>在 Visual Basic 中生成替代
**新增功能：**允许您立即从基类中生成的代码可以重写任何方法。 

**何时：**你想要重写基类方法并自动生成的签名。  

**原因：**你可以编写的方法签名你自己，但此功能将自动生成的签名。 

**如何：**

1. 类型**重写**关键字后, 跟一个空格，其中你想要插入的重写的方法签名，IntelliSense 下拉列表中将出现。

   ![重写的 IntelliSense](media/override_intellisense.png)

1. 选择你想要通过使用鼠标，单击该命令或使用键盘和按导航到它从基类重写的方法**Enter**。

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override_property.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override_method.png) to show or hide Methods in the list.
-->

1. 所选的方法或属性将作为替代，准备好实现添加到类。

   ![重写结果](media/override_result.png)

## <a name="see-also"></a>另请参阅  
[代码生成 (Visual Basic)](../code-generation-vb.md) 