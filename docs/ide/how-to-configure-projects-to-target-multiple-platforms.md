---
title: "如何：将项目配置为面向多个平台 | Microsoft Docs"
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
  - "platforms, 更改目标平台"
  - "项目 [Visual Studio], 针对平台"
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：将项目配置为面向多个平台
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 为解决方案提供一种面向若干不同 CPU 结构或平台，立即。  设置的属性。 **配置管理器** 对话框中访问。  
  
## 目标平台  
 **配置管理器** 对话框用于创建和设置解决方案级别和项目级别的配置和平台。  解决方案级配置和目标平台的每种组合都可以具有单个设置属性与其关联，使您可以方便地切换，例如，若要面向 [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] 平台配置面向 x86 平台和调试配置面向 x86 平台的 " 发布 " 配置。  
  
#### 配置设置为面向不同平台  
  
1.  在 **生成** 菜单上，单击 **配置管理器**。  
  
2.  在 **活动解决方案平台框**，选择希望您的解决方案的目标平台或选择 **新建** 创建新的平台。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将编译应用程序以设置为 **配置管理器** 对话框的活动平台的平台。  
  
## 移除平台  
 如果发现不需要某个平台，使用 " 配置管理器 " 对话框，可以将其移除。  这将移除您为配置和目标平台的相应组合配置的所有解决方案和项目设置。  
  
#### 移除平台  
  
1.  在 **生成** 菜单上，单击 **配置管理器**。  
  
2.  在 **活动解决方案平台框**，选择 **编辑**。  **编辑解决方案平台** 对话框打开。  
  
3.  单击要移除的平台，然后单击 **remove**。  
  
## 面向多个平台在一个解决方案  
 由于可以更改基于配置和平台设置的组合，可以设置一个面向多个平台的解决方案。  
  
#### 面向多个平台  
  
1.  使用 **配置管理器** 为解决方案添加至少两个目标平台。  
  
2.  选择要从 **活动解决方案平台** 针对列表的平台。  
  
3.  生成解决方案。  
  
#### 同时生成多个解决方案配置  
  
1.  使用 **配置管理器** 为解决方案添加至少两个目标平台。  
  
2.  使用 **批生成** 窗口同时生成多个解决方案配置。  
  
 可以使一个解决方案级平台设置为，例如， [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]，并且没有以同一平台该解决方案中的项目。  也可以在解决方案中包含多个项目，每个项目面向不同的平台。  建议，如果您有这些情况之一，则创建新的配置使用一个描述性名称避免混淆。  
  
## 请参阅  
 [如何：创建和编辑配置](../ide/how-to-create-and-edit-configurations.md)   
 [了解生成配置](../ide/understanding-build-configurations.md)   
 [在 Visual Studio 中生成和清理项目和解决方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)