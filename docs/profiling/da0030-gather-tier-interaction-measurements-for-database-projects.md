---
title: "DA0030：收集数据库项目的层交互测量值 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0030"
  - "vs.performance.rules.DA0030"
  - "vs.performance.30"
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0030：收集数据库项目的层交互测量值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0030|  
|类别|分析工具使用|  
|分析方法|采样|  
|消息|通过收集多层应用程序的交互测量值，可帮助了解数据库使用模式和关键数据访问延迟。  启用层交互分析选项后，尝试重新分析应用程序。|  
|规则类型|信息|  
  
## 原因  
 对 <xref:System.Data> 方法的调用在分析数据中占很大比例，并且您未收集分析运行中的层交互数据。  请考虑重新进行分析并添加层交互数据。  
  
## 规则说明  
 只要位于 System.Data 命名空间（包括 <xref:System.Data.Linq> <xref:System.Data.Linq>）的函数中有重要活动，就会激发此规则。  
  
 多层应用程序对其表示形式和数据层使用分层服务。  通常，数据层是一个运行数据库管理系统（如 Microsoft Sql Server）的单独进程。  数据层甚至可能与应用程序的其余部分在不同的计算机上运行。  采样分析对于了解在进程外运行或远程运行的函数和服务没有什么用处。  
  
 分析工具可以收集通过使用对 ADO.NET 服务的异步调用与 Microsoft Sql Server 数据层交互的多层应用程序的计时信息。  您必须显式启用层交互分析。  默认情况下，它未处于打开状态。  
  
## 如何解决冲突  
 此规则仅供参考，无需进行更正操作。  
  
 有关如何通过 IDE 向分析数据添加层交互数据的信息，请参见[收集层交互数据](../profiling/collecting-tier-interaction-data.md)。  有关如何通过命令行添加层交互数据的信息，请参见[收集层交互数据](../profiling/adding-tier-interaction-data-from-the-command-line.md)。