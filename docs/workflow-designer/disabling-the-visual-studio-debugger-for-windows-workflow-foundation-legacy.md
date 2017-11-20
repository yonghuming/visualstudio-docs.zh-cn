---
title: "禁用 Visual Studio Debugger for Windows Workflow Foundation （旧版） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 835ca509c86a9be27486ee257839c4e161221e4e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>禁用 Visual Studio Debugger for Windows Workflow Foundation（旧版）
本主题介绍如何在旧 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中生成 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序时，使用配置文件禁用 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 调试器。 在需要面向 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 时，请使用旧 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。  
  
 默认情况下，为宿主进程启用了 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]。 若要禁用工作流调试，你必须显式将其关闭通过添加"DisableWorkflowDebugging"项**\<交换机 >**中的元素 **\<system.diagnostics >**主机配置文件节。  
  
 以下示例显示如何修改主机配置文件以禁用工作流调试。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [调用 Visual Studio Debugger for Windows Workflow Foundation （旧版）](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [调试旧版工作流](../workflow-designer/debugging-legacy-workflows.md)