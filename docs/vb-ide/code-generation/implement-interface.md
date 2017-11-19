---
title: "实现接口的代码生成 (Visual Basic 中) |Microsoft 文档"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 932cfb092d4106d9afa323aa3689a813ec2dde03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implement-an-interface-in-visual-basic"></a>在 Visual Basic 中实现接口
**新增功能：**便会立即生成所需实现接口的代码。 

**何时：**你想要从接口继承。  

**原因：**但此功能会自动生成所有方法签名，可以手动实现所有接口一个由一。 

**如何：**

1. 将光标放在行上： 有红色的波浪线，该值指示引用接口但未实现了所有必需的成员。

   ![突出显示的代码](media/interface_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**（显式） 实现接口**从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**（显式） 实现接口**从预览窗口弹出窗口。
     * 将鼠标悬停在红色波形曲线和单击 ![灯泡](media/bulb.png) 显示的图标。
     * 单击 ![灯泡](media/bulb.png) 如果文本光标已在行中使用红色波形曲线的左边距中显示的图标。

   ![实现类预览](media/interface_preview.png)

   >[!TIP]
   >使用[**预览更改**](../../ide/preview-changes.md)底部的预览窗口来查看所有将在你的选择之前所做的更改的链接。
   >
   >此外，你可以使用**文档**，**项目**，和**解决方案**跨多个创建正确的方法签名的预览窗口底部的链接实现接口的类。

1. 接口的方法签名将自动创建，并且可以实现。

   ![实现类结果](media/interface_result.png)

## <a name="see-also"></a>另请参阅  
[代码生成 (Visual Basic)](../code-generation-vb.md)  
[预览更改](../../ide/preview-changes.md)