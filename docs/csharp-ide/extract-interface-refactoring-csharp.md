---
title: "提取接口重构 (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.extractinterface"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "“提取接口”重构操作 [C#]"
  - "重构 [C#], 提取接口"
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 提取接口重构 (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“提取接口”是一项重构操作，提供了一种使用来自现有类、结构或接口的成员创建新接口的简单方法。  
  
 当几个客户端使用类、结构或接口中成员的同一子集时，或者当多个类、结构或接口具有通用的成员子集时，在接口中嵌入成员子集将很有用。  有关使用接口的更多信息，请参见 [接口](/dotnet/csharp/programming-guide/interfaces/index)。  
  
 “提取接口”在新文件中生成接口，并将光标定位于新文件的开头。  使用**“提取接口”**对话框，可以指定要提取到新接口中的成员、新接口的名称以及所生成的文件的名称。  
  
### 使用“提取接口”  
  
1.  创建名为 `ExtractInterface` 的控制台应用程序，然后使用以下代码替换 `Program`  
  
    ```c#  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  将光标置于 `MethodB` 中后，单击**“重构”**菜单中的**“提取接口”**。  
  
     出现**“提取接口”**对话框。  
  
     您还可以键入键盘快捷键 Ctrl\+R、Ctrl\+I 来显示**“提取接口”**对话框。  
  
     还可以右击鼠标，指向**“重构”**，然后单击**“提取接口”**来显示**“提取接口”**对话框。  
  
3.  单击**“全选”**。  
  
4.  单击**“确定”**。  
  
     您将看到新文件 IProtoA.cs 和下面的代码：  
  
    ```c#  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## 备注  
 仅当将光标定位于包含要提取成员的类、结构或接口中时，才可以访问此功能。  当光标处于此位置时，调用“提取接口”重构操作。  
  
 在类或结构中调用“提取接口”时，将修改基和接口列表，以包括新接口名称。  而在接口中调用“提取接口”时，将不修改基和接口列表。  
  
## 请参阅  
 [重构 \(C\#\)](../csharp-ide/refactoring-csharp.md)