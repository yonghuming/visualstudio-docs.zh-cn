---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "移除参数重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.remove
dev_langs: CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5e53d813d9b2dcefd2b2d19da2a76b6c0d1f989
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="remove-parameters-refactoring-c"></a>移除参数重构 (C#)
`Remove Parameters`是的重构操作，可以轻松地删除方法、 索引器或委托的参数。 删除参数更改声明;在调用该成员的所有位置，移除的参数以反映新的声明。  
  
 通过第一个定位将光标放在方法、 索引器或委托执行删除参数操作。 光标位于位置，以便调用 Remove`Parameters`操作，单击**重构**菜单上，按键盘快捷方式，或从快捷菜单中选择该命令。  
  
> [!NOTE]
>  不能为扩展方法中删除第一个参数。  
  
### <a name="to-remove-parameters"></a>若要删除参数  
  
1.  创建控制台应用程序名为`RemoveParameters`，然后替换`Program`替换为以下代码。  
  
    ```csharp  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  将光标放在方法`A`，在方法声明或方法调用。  
  
3.  从**重构**菜单上，选择**移除参数**以显示**移除参数**对话框。  
  
     此外可以键入键盘快捷键 CTRL + R、 V 显示**移除参数**对话框。  
  
     此外可以右键单击将光标置于，指向**重构**，然后单击**移除参数**以显示**移除参数**对话框。  
  
4.  使用**参数**字段中，将光标置于`int i`，然后单击**删除**。  
  
5.  单击“确定”。  
  
6.  在**预览更改-删除参数**对话框中，单击**应用**。  
  
## <a name="remarks"></a>备注  
 你可以从方法声明或方法调用中删除参数。 将光标放置在方法声明或委托名称并调用删除参数。  
  
> [!CAUTION]
>  删除参数允许你删除该成员，但它的正文中引用的参数不会在方法正文中删除对该参数的引用。 这会生成错误引入你的代码。 但是，你可以使用**预览更改**对话框中，在执行重构操作之前检查你的代码。  
  
 如果要删除的参数在对方法的调用期间修改的移除参数还将删除修改。 例如，如果方法调用更改从  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 更改为  
  
```csharp  
MyMethod(param2);  
```  
  
 重构操作，`param1`将不会递增。  
  
## <a name="see-also"></a>另请参阅  
 [重构 (C#)](refactoring-csharp.md)