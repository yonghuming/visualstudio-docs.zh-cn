---
title: "如何： 更改调试单步执行选项 （旧版） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ff11186c82102230ec939c0c9b1c5aba69df7f3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>如何：更改调试单步执行选项（旧版）
本主题介绍如何在旧 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 中，针对具有并发操作的 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 应用程序更改调试单步执行选项。 在需要面向 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 时，请使用旧 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。  
  
 在调试具有并发执行，如的旧活动**ParallelActivity**或**ConditionedActivityGroup**，你可以使用两个选项之一逐句通过代码。  
  
 按照这些步骤在旧工作流项目中更改调试单步执行选项。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-change-the-debug-stepping-option"></a>更改调试单步执行选项  
  
1.  启动 Visual Studio。  
  
2.  打开现有的旧工作流项目，或创建使用并发活动并且面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 的新项目。  
  
3.  上**工作流**在旧菜单[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]，指向**调试**，然后指向**单步执行选项**。  
  
4.  选择**实例**或**分支**。  
  
## <a name="see-also"></a>另请参阅  
 [调试旧版工作流](../workflow-designer/debugging-legacy-workflows.md)   
 [调试单步执行选项（旧版）](../workflow-designer/debug-stepping-options-legacy.md)