---
title: "VS Shell 部署 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 2
---
# VS Shell 部署
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

独立 shell 可确定哪个 Visual Studio 功能需要具有这种域特定语言交互，该解决方案应如何显示。  有关 Visual Studio 的更多信息独立 shell，请参见 [自定义独立的 Shell](../extensibility/customizing-the-isolated-shell.md)。  可以查找有关如何的更多信息来自定义在 [Customizing the Isolated Shell](http://msdn.microsoft.com/zh-cn/d75463cd-1155-42e4-8b7a-046ed6becbbf)独立 shell。  
  
### 若要设置 Visual Studio shell 请为部署目标  
  
1.  在 **DslPackage** 项目中，打开 **source.extension.tt**。  
  
2.  在 `<SupportedProducts>` 插入下:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     使用独立 shell 包的名称替换 *MyIsolatedShell* 。