---
title: "扩展自动化模型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自动化对象模型, 扩展"
ms.assetid: f09e1365-6291-41a7-b52b-9398270d9da2
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 扩展自动化模型
本节讨论自动化模型和 VSPackage 模型如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 环境表示两橛方法的扩展性。  扩展性是能引发事件和扩展 IDE 的功能。  自动化，一种，指的是现有环境中自动执行任务和编程驱动 IDE 的用户生成的代码和工具。  Vspackage，另一方面，允许您添加新功能到环境。  
  
 合并自动化和 Vspackage 在扩展性应用程序是可能的。  有关示例，请参见[演练：通过使用自动化来扩展托管 VSPackage](../misc/walkthrough-extending-managed-vspackages-by-using-automation.md)。  
  
 有关支持自动化模型的语言项目系统的端对端示例，请参见 [VSSDK 示例](../misc/vssdk-samples.md)。  
  
## 本节内容  
 [自动化模型](/visual-cpp/misc/automation-model)  
 提供自动化模型的概述并讨论自动化模型如何允许您自定义，调整和自动化环境。  
  
 [导致自动化模型](../extensibility/internals/contributing-to-the-automation-model.md)  
 提供自动化模型的一个更详细的视图并讨论为 VSPackage 提供自动化。  本节还提供了代码示例自动使用者如何获取初始项目自动化对象。  
  
## 相关章节  
 [Visual Studio SDK 和自动化](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 讨论如何使用自动化、 Vspackage 或组合创建 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 扩展性应用程序。