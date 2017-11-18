---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "重新排列参数重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.reorder
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3469e9ae7101c9e180fba5558fce389c6dfcc72d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="reorder-parameters-refactoring-c"></a>重新排列参数重构 (C#)
`Reorder Parameters`一个 Visual C# 重构操作，提供了一种简单的方法来更改方法、 索引器和委托的参数的顺序。 `Reorder Parameters`更改的声明，并在调用该成员的所有位置，重新排列参数，以反映新的顺序。  
  
 若要执行`Reorder Parameters`操作，将光标置于或旁边方法、 索引器或委托。 当光标位于位置时，调用`Reorder Parameters`操作通过按键盘快捷方式，或通过单击快捷菜单中的命令。  
  
> [!NOTE]
>  不能对扩展方法中的第一个参数重新排序。  
  
### <a name="to-reorder-parameters"></a>对参数重新排序  
  
1.  创建一个名为类库`ReorderParameters`，然后替换`Class1`用下面的示例代码。  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  将光标放在`MethodB`，在方法声明或方法调用。  
  
3.  上**重构**菜单上，单击**重新排列参数**。  
  
     **重新排列参数**对话框随即出现。  
  
4.  在**重新排列参数**对话框中，选择`int i`中**参数**列表，，然后单击向下按钮。  
  
     或者，可以拖动`int i`后`bool b`中**参数**列表。  
  
5.  在**重新排列参数**对话框中，单击**确定**。  
  
     如果**预览引用更改**中选择选项**重新排列参数**对话框中，**预览更改-重新排列参数**对话框将出现。 它提供的参数列表中的更改的预览`MethodB`在签名和方法调用。  
  
    1.  如果**预览更改-重新排列参数**显示对话框，请单击**应用**。  
  
         在此示例中，方法声明和所有方法调用站点`MethodB`更新。  
  
## <a name="remarks"></a>备注  
 你可以重新排列从方法声明或方法调用的参数。 将光标上或旁边方法或委托声明但不是在正文中的位置。  
  
## <a name="see-also"></a>另请参阅  
 [重构 (C#)](refactoring-csharp.md)