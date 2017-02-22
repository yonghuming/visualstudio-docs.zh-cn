---
title: "如何：在应用 Visual Basic 开发人员设置后管理生成配置 | Microsoft Docs"
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
  - "高级生成配置"
  - "应用 Visual Basic 开发员设置后生成"
  - "调试版本"
  - "MSBuild, 调试版本"
  - "MSBuild, 发行版本"
  - "发行版本"
  - "Visual Studio, 应用 Visual Basic 设置后生成"
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：在应用 Visual Basic 开发人员设置后管理生成配置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

默认情况下，所有高级生成配置选项隐藏具有 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 在应用开发人员设置。  本主题介绍如何手动启用这些设置。  
  
## 启用高级生成配置  
 默认情况下， [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 开发人员设置隐藏选项卡打开 **配置管理器** 对话框，并 **配置** 和 **平台** 在 [项目设计器](http://msdn.microsoft.com/zh-cn/898dd854-c98d-430c-ba1b-a913ce3c73d7)列表。  
  
#### 启用高级生成配置  
  
1.  在 **工具** 菜单上，单击 **选项**。  
  
2.  外接 **项目和解决方案**，然后单击 **常规**。  
  
    > [!NOTE]
    >  **常规** 节点可见，即使 **显示所有设置** 取消选中选项的。  如果要查看每个可用选项，请单击 **显示所有设置**。  
  
3.  单击 **显示高级生成配置**。  
  
4.  单击 **确定**。  
  
     在 **生成** 菜单上， **配置管理器** 现在可用，并且， **配置** 和 **平台** 列表会显示在 " 项目设计器 "。  
  
## 请参阅  
 [了解生成配置](../ide/understanding-build-configurations.md)   
 [在 Visual Studio 中构建应用程序](../ide/compiling-and-building-in-visual-studio.md)