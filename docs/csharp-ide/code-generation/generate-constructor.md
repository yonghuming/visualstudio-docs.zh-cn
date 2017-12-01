---
title: "生成的构造函数的代码生成 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.openlocfilehash: 668036b5a9c963a48255e8425c0d443fce4b8bb7
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/29/2017
---
# <a name="generate-a-constructor-in-c"></a>在 C# 中生成一个构造函数 #
**新增功能：**便会立即生成新的构造函数的类上的代码。 

**何时：**引入新的构造函数并想要正确地将其声明自动，或修改现有的构造函数。 

**原因：**你无法再使用它，声明构造函数，但此功能将它，并用正确的参数，自动生成。 此外，修改现有的构造函数需要更新所有调用站点，除非您使用此功能来自动更新它们。

**如何：**有几种方法来生成一个构造函数：
- [生成构造函数和选取成员](#pick)
- [从所选的字段生成构造函数](#selection)
- [从新的使用情况生成构造函数](#usage)
- [将参数添加到现有的构造函数](#addparameter)
- [创建和初始化字段/属性从构造函数参数](#create)

## <a id = "pick"></a>生成构造函数和选取成员
1. 将光标放在类中任何空行：

   ![光标位于空的行](media/constructor1_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**生成构造函数...**从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**生成构造函数...**从预览窗口弹出窗口。
     * 单击 ![灯泡](media/bulb.png) 如果文本光标已在类中的空行上将显示在左边距中的图标。

   ![生成构造函数预览](media/constructor1_preview.png)

1. 将显示一个对话框，从而可以挑选和选择你想要使用作为构造函数参数，以及 （使用向上和向下箭头） 对它们进行排序的成员。 按**确定**以提交所做的更改。
  
   ![选取成员对话框](media/constructor1_dialog.png)

   >[!TIP] 
   >你可以检查**添加 null 检查**复选框以自动生成的构造函数参数的 null 检查。

1. 构造函数将创建具有指定的顺序中的所选参数。
   ![生成构造函数结果](media/constructor1_result.png)

## <a id="selection"></a>从所选的字段生成构造函数
1. 突出显示你想让你生成的构造函数中的成员：![突出显示成员](media/constructor2_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**生成构造函数 TypeName(...)**从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**生成构造函数 TypeName(...)**从预览窗口弹出窗口。
     * 单击 ![灯泡](media/bulb.png) 如果文本光标已在行中使用所选内容的左边距中显示的图标。

     ![生成构造函数预览](media/constructor2_preview.png)

1. 构造函数将创建具有所选的参数。
     ![生成构造函数结果](media/constructor2_result.png)

## <a id="usage"></a>从新的使用情况生成构造函数
1. 将光标置于该行上红色的波浪线，该值指示你已使用尚不存在的构造函数的情况。

   ![突出显示的代码](media/constructor_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**生成构造函数中的*TypeName** * 从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**生成构造函数中的*TypeName** * 从预览窗口弹出窗口。
     * 将鼠标悬停在红色波形曲线和单击 ![灯泡](media/bulb.png) 显示的图标。
     * 单击 ![灯泡](media/bulb.png) 如果文本光标已在行中使用红色波形曲线的左边距中显示的图标。

   ![生成构造函数预览](media/constructor_preview.png)

   >[!TIP]
   >使用[**预览更改**](../../ide/preview-changes.md)底部的预览窗口来查看所有将在你的选择之前所做的更改的链接。

1. 构造函数将自动创建包含根据其使用情况推断出任何参数。

   ![生成构造函数结果](media/constructor_result.png)

## <a id="selection"></a>将参数添加到现有的构造函数
1. 将参数添加到现有的对象实例化。

1. 将光标置于该行上红色的波浪线，该值指示你已使用尚不存在的构造函数的情况。
    
    ![生成构造函数突出显示](media/constructor4_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**将参数添加到 TypeName(...)**从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**将参数添加到 TypeName(...)**从预览窗口弹出窗口。
     * 将鼠标悬停在红色波形曲线和单击 ![灯泡](media/bulb.png) 显示的图标。
     * 单击 ![灯泡](media/bulb.png) 如果文本光标已在行中使用红色波形曲线的左边距中显示的图标。

    ![生成构造函数预览](media/constructor4_preview.png)

1. 与从其使用情况推断其类型，将自动添加参数。
   
   ![生成构造函数结果](media/constructor4_result.png)

## <a id="create"></a>创建和初始化字段/属性从构造函数参数
1. 从现有的构造函数，添加参数：

   ![生成构造函数突出显示](media/constructor5_highlight.png)

1. 将光标在新添加的参数。

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**创建并初始化属性 YourProperty**或**创建并初始化字段 YourField**从预览窗口弹出窗口。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**创建并初始化属性 YourProperty**或**创建并初始化字段 YourField**从预览窗口弹出窗口。
     * 单击 ![灯泡](media/bulb.png) 如果文本光标已在行中使用添加的参数的左边距中显示的图标。

   ![生成构造函数预览](media/constructor5_preview.png)

1. 将创建并自动为与你的类型匹配而命名字段/属性。

   ![生成构造函数结果](media/constructor5_result.png)
  
## <a name="see-also"></a>另请参阅  
[代码生成 (C#)](../code-generation-csharp.md)  
[预览更改](../../ide/preview-changes.md)