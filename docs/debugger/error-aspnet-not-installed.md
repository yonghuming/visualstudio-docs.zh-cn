---
title: "错误：未安装 ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http_not_supported"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, 安装错误信息"
  - "调试器, Web 应用程序错误"
  - "错误信息, ASP.NET"
  - "Web 应用程序, 错误"
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误：未安装 ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当您尝试调试的计算机上未正确安装 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 时，会发生此错误。  此错误可能意味着从未安装 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，或者先安装了 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]，然后又安装了 IIS。  
  
### 重新安装 ASP.NET  
  
1.  从命令提示符窗口中，运行以下命令：  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     其中，*version* 表示安装在您的计算机上的 .NET Framework 的版本号（例如，v1.0.370）。  通过在 `\WINDOWS\Microsoft.NET\Framework` 目录中查找，可以确定 Framework 的版本。  
  
    > [!NOTE]
    >  对于 Windows Server 2003，可以使用控制面板中的**“添加\/删除程序”**来安装 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]。  
  
## 请参阅  
 [调试 Web 应用程序：错误和疑难解答](../debugger/debugging-web-applications-errors-and-troubleshooting.md)