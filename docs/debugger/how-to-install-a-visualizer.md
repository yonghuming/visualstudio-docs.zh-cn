---
title: "如何：安装可视化工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试器, 可视化工具"
  - "可视化工具, 安装"
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何：安装可视化工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

创建了可视化工具后，您还必须安装该可视化工具，这样您才可在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用它。  安装可视化工具是个简单的过程。  
  
> [!NOTE]
>  **存储**应用仅支持标准文本、HTML、XML 和 JSON 可视化工具。  不支持自定义（用户创建的）可视化工具。  
  
### 安装可视化工具  
  
1.  查找包含已创建的可视化工具的 DLL。  
  
2.  将 DLL 复制到下列位置之一：  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  若要使用托管可视化工具进行远程调试，请将 DLL 复制到远程计算机上的同一路径。  
  
4.  重新启动调试会话。  
  
## 请参阅  
 [可视化工具](../debugger/create-custom-visualizers-of-data.md)   
 [如何：编写可视化工具](../debugger/how-to-write-a-visualizer.md)