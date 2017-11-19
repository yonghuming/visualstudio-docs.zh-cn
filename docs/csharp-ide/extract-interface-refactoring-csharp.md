---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-interface
title: "提取接口重构 (C#) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4ed81f6f0fbcc2e72fd57d7706b051dcdf7bea75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extract-interface-refactoring-c"></a>提取接口重构 (C#)
提取接口是的重构操作，可以轻松地使用来自现有类、 结构或接口的成员创建的新接口。  
  
 当多个客户端使用相同成员组成的子集从类、 结构或接口，或者当多个类、 结构或接口的共同点成员组成的子集，它可用于体现了接口中的成员的子集。 有关使用接口的详细信息，请参阅[接口](/dotnet/csharp/programming-guide/interfaces/index)。  
  
 提取接口在新的文件中生成一个接口，并将光标置于新文件的开头。 你可以指定要提取到新接口，新接口，名称和生成的文件使用的名称的成员**提取接口**对话框。  
  
### <a name="to-use-extract-interface"></a>若要使用提取接口  
  
1.  创建控制台应用程序名为`ExtractInterface`，然后替换`Program`替换为以下代码  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  将光标置于与`MethodB`，然后单击**提取接口**上**重构**菜单。  
  
     **提取接口**对话框随即出现。  
  
     你也可以键入的键盘快捷方式 CTRL + R，我显示**提取接口**对话框。  
  
     此外可以右键单击鼠标，指向**重构**，然后单击**提取接口**以显示**提取接口**对话框。  
  
3.  单击**选择所有**。  
  
4.  单击“确定”。  
  
     你看到新的文件、 IProtoA.cs，并添加以下代码：  
  
    ```csharp  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## <a name="remarks"></a>备注  
 当光标定位在类、 结构或接口包含你想要提取的成员，此功能才可访问。 当光标位于此位置时，调用提取接口重构操作。  
  
 调用提取接口的类或结构时，将修改基类和接口列表，以包括新的接口名称。 提取接口在接口上的调用时，不修改基类和接口列表。  
  
## <a name="see-also"></a>另请参阅  
 [重构 (C#)](refactoring-csharp.md)