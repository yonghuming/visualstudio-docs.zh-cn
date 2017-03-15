---
title: "通过远程计算机调试工作流（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "调试工作流, 远程"
  - "调试, 远程"
  - "远程调试, 工作流"
  - "工作流, 远程调试"
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 通过远程计算机调试工作流（旧版）
本主题介绍如何调试使用旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 生成的旧远程 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序。在应用程序需要面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 时，请使用旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 安装 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 时，一个组件安装选项是为 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 安装 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 调试器。这将安装远程调试组件。必须在将要进行远程工作流调试的目标计算机上安装这些远程调试组件。  
  
 另外，必须在用于调试的本地计算机的全局程序集缓存 \(GAC\) 中安装程序集，该程序集包含将在远程计算机上进行调试的旧工作流的工作流定义。例如，如果远程计算机 A 上运行工作流的旧式且你是调试它从本地计算机 B、工作流定义必须存在于 B 计算机的 GAC 中。这使反序列化和计算机 B 的 A 计算机远程运行的工作流的工作流标记上显示设计器。有关全球程序集缓冲的更多信息，请参阅 MSDN Library。  
  
 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 远程调试的作用方式与其他 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 组件的远程调试相同。有关更多信息，请参见 MSDN Library 中有关“[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 远程调试”的内容。  
  
## 请参阅  
 [调试旧版工作流](../workflow-designer/debugging-legacy-workflows.md)