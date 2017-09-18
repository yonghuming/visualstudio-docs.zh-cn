---
title: "重新排列参数重构 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.reorder"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "重构 [C#], 重新排列参数"
  - "重新排列参数重构 [C#]"
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 重新排列参数重构 (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Reorder Parameters`是一项 Visual C\# 重构操作，提供了一种对方法、索引器和委托的参数顺序进行更改的简单方法。  `Reorder Parameters`会更改声明，并在调用该成员的所有位置重新排列参数，从而反映新的顺序。  
  
 若要执行 `Reorder Parameters` 操作，请将光标置于方法、索引器或委托之上或旁边。  当光标位于适当的位置后，请通过按键盘快捷键或从快捷菜单中单击相应的命令来调用 `Reorder Parameters` 操作。  
  
> [!NOTE]
>  您无法重新排列扩展方法中的第一个参数。  
  
### 重新排列参数  
  
1.  创建名为 `ReorderParameters` 的类库，然后使用以下代码示例替换 `Class1`。  
  
    ```c#  
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
  
2.  将光标放在方法声明或方法调用中的 `MethodB` 上。  
  
3.  在**“重构”**菜单上单击**“重新排列参数”**。  
  
     即会出现**“重新排列参数”**对话框。  
  
4.  在**“重新排列参数”**对话框的**“参数”**列表中选择 `int i`，再单击向下按钮。  
  
     也可在**“参数”**列表中将 `int i` 拖到 `bool b` 后面。  
  
5.  在**“重新排列参数”**对话框中单击**“确定”**。  
  
     如果在**“重新排列参数”**对话框中选择了**“预览引用更改”**选项，则将显示**“预览更改 \- 重新排列参数”**对话框。  它提供了签名和方法调用中 `MethodB` 的参数列表中的更改预览。  
  
    1.  如果显示**“预览更改 \- 重新排列参数”**对话框，则请单击**“应用”**。  
  
         在此示例中，更新了 `MethodB` 的方法声明和所有方法调用站点。  
  
## 备注  
 可以通过方法声明或方法调用来重新排列参数。  要将光标置于方法声明或委托声明之上或旁边，而不是置于正文中。  
  
## 请参阅  
 [重构 \(C\#\)](../csharp-ide/refactoring-csharp.md)