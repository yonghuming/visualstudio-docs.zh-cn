---
title: "生成的重写的代码生成 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d2972cfe2ea4481ab8f5eab6284277615d1d64a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="generate-an-override-in-c"></a>在 C# 中生成替代 #
**新增功能：**允许您立即从基类中生成的代码可以重写任何方法。 

**何时：**你想要重写基类方法并自动生成的签名。  

**原因：**你可以编写的方法签名你自己，但此功能将自动生成的签名。 

**如何：**

1. 类型**重写**关键字后, 跟一个空格，其中你想要插入的重写的方法签名，IntelliSense 下拉列表中将出现。

   ![重写的 IntelliSense](media/override_intellisense.png)

1. 选择你想要通过使用鼠标，单击该命令或使用键盘和按导航到它从基类重写的方法**Enter**。

   >[!TIP]
   >* 使用属性图标 ![“属性”图标](media/override_property.png) 若要显示或隐藏属性列表中。
   >* 使用方法图标 ![“属性”图标](media/override_method.png) 若要显示或隐藏在列表中的方法。

1. 所选的方法或属性将作为替代，准备好实现添加到类。

   ![重写结果](media/override_result.png)

## <a name="see-also"></a>另请参阅  
[代码生成 (C#)](../code-generation-csharp.md)  
