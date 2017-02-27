---
title: "禁用 Visual Studio Debugger for Windows Workflow Foundation（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "调试工作流, 禁用调试器"
  - "工作流调试器, 禁用"
  - "工作流, 禁用调试器"
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 禁用 Visual Studio Debugger for Windows Workflow Foundation（旧版）
本主题介绍如何在旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中生成 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序时，使用配置文件禁用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试器。在需要面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 时，请使用旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 默认情况下，为宿主进程启用了 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]。若要禁用工作流调试，必须通过在宿主配置文件的 **\<system.diagnostics\>** 节中添加“DisableWorkflowDebugging”项 **\<switches\>** 元素，来显式禁用工作流调试。  
  
 以下示例显示如何修改宿主配置文件以禁用工作流调试。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="DisableWorkflowDebugging" value="true"/>  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## 请参阅  
 [调用 Visual Studio Debugger for Windows Workflow Foundation（旧版）](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [调试旧版工作流](../workflow-designer/debugging-legacy-workflows.md)