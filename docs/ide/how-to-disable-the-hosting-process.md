---
title: "如何：禁用承载进程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "承载进程, 禁用"
  - "vshost.exe, 禁用承载进程"
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：禁用承载进程
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

承载进程可能会对某些 API 的调用产生影响。  在这些情况下，有必要禁用宿主进程以返回正确的结果。  
  
### 禁用宿主进程  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]打开可执行项目。  不会导致可执行文件的项目 \(例如，选件类库或服务项目\) 没有此选项。  
  
2.  在**“项目”**菜单上，单击**“属性”**。  
  
3.  单击**“调试”**选项卡。  
  
4.  清除**“启用 Visual Studio 宿主进程”**复选框。  
  
 禁用宿主进程后，将无法使用一些调试功能，或者将导致性能下降。  有关详细信息，请参阅[调试和承载进程](../debugger/debugging-and-the-hosting-process.md)。  
  
 一般而言，禁用宿主进程后，将出现以下情况：  
  
-   开始调试 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 应用程序所需的时间增加。  
  
-   设计时表达式计算不可用。  
  
-   部分信任调试不可用。  
  
## 请参阅  
 [调试和承载进程](../debugger/debugging-and-the-hosting-process.md)   
 [承载进程 \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Builds During Application Development](http://msdn.microsoft.com/zh-cn/c9497d62-3b7b-4449-88e8-cf27acc9efe6)