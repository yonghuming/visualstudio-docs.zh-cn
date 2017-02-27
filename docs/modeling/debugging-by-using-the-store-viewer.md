---
title: "使用存储查看器进行调试 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "域特定语言, 存储"
  - "域特定语言, 存储查看器"
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 17
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 17
---
# 使用存储查看器进行调试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

存储浏览器，可以检查 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]使用的 *存储* 状态。  存储浏览器显示在特定单元，与组件属性和指向各个元素之间的所有域模型元素。  
  
## 打开存储区浏览器  
 当您处于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的实验性生成时，将停止代码在存储实例包含模型信息的断点。 然后，通过键入在 **立即**运行以下命令打开存储浏览器:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  必须将存储实例的名称替换 `mystore` 。  此外，，如果您将命名空间添加到代码，您可以键入显示的内存浏览器命令，而无需为完全限定的命名空间:  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `…`  
>   
>  `StoreViewer.Show(mystore);`  
  
 `Show` 方法有若干次重载。  可以指定存储或分区的实例作为参数。  
  
 或者，可以将显示存储浏览器在代码中的任意位置参数传递给 `Show` 方法在范围内的代码行。  代码时，行是作为存储区的内容时，快照此事件显示存储浏览器。  
  
### 使用存储浏览器  
 在存储浏览器打开时，无模式窗口窗体窗口，显示，如下图所示。  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
存储浏览器  
  
 存储浏览器有三个窗格:左窗格、的右上角窗格和底部正确的窗格。  左窗格是类型的树视图中存储的 `DomainDataDirectory` 成员。  如果展开分区节点并单击元素，元素的属性显示在的右上角窗格。  如果组件与其他组件链接，其他元素出现在底部正确的窗格。  如果双击在底部正确的窗格的元素，该元素在左窗格中显示。  
  
## 请参阅  
 [在程序代码中导航和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)