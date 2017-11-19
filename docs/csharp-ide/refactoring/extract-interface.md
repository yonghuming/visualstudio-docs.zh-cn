---
title: "提取接口-重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 55e17f0a-eacb-41ec-b8ca-74f5c6bbd6de
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: csharp
ms.openlocfilehash: 854e341a5c02b3bb4b0a596720a4899410550689
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extract-an-interface-in-c"></a>提取在 C# 中的接口 #
**新增功能：**允许你创建使用从类、 结构或接口的现有成员的接口。

**何时：**你有多个类、 结构或接口使用的常见和所用的其他类、 结构或接口不能建立的方法。

**原因：**接口是针对面向对象的设计出色构造。  假设具有各种动物 （Dog，Cat，注册优惠） 可能都具有常见方法，如 Eat，饮料、 睡眠的类。  使用如 IAnimal 接口，Dog、 Cat，和注册可有公用的"签名"的这些方法。  

**如何：**

1. 突出显示的类上，执行操作的名称，或只是文本将光标放在某个位置中的类名称。

   ![突出显示的代码](media/extractinterface_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl + R**，然后**Ctrl + I**。  （请注意，键盘快捷方式可能因所选的配置文件而有所不同。）
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**提取接口**从预览窗口弹出窗口。
   * **鼠标**
     * 选择**编辑 > 重构 > 提取接口**。
     * 右键单击类，选择的名称**快速操作和重构**菜单，然后选择**提取接口**从预览窗口弹出窗口。

1. 在**提取接口**，弹出的对话框中，输入要求的信息：![提取接口](media/extractinterface_dialog.png)
   | 字段 | 描述 |
   | --- | --- |
   | **新的接口名称** | 要创建的接口名称。 这将默认为我*ClassName*，其中*ClassName*是上面所选的类的名称。 |
   | **新的文件名称** | 将包含的接口将生成的文件的名称。 为具有接口名称，这将默认为我*ClassName*，其中*ClassName*是上面所选的类的名称。 |
   | **选择构成接口的公共成员** | 要提取到接口的项。  你可以选择你希望的任意数量。 |

1. 单击“确定”。

   将指定的名称的文件中立即创建接口。  此外，所选的类现在将实现该接口。

   ![生成的类](media/extractinterface_class.png)
   ![生成接口](media/extractinterface_interface.png)

## <a name="see-also"></a>另请参阅  
[重构 (C#)](../refactoring-csharp.md)