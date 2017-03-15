---
title: "创建源控件 VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理 [Visual Studio SDK]，创建源代码管理包"
  - "源代码管理包"
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 创建源控件 VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本文档包含指向由接口中实现的和将被使用的服务定义的源控件包的结构的概述与集成 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、 API 和阐释一个简单的源代码管理包实现的示例。  
  
 源代码管理 VSPackage，您可以创建源控件的一个集成路径可以与集成 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  它启用包来跳过 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI 承载的默认数据源控件，响应来自项目系统的源代码管理请求，并将 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 元素 \(如\) 交互 **解决方案资源管理器**。  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 授权 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 合作伙伴提供 framework 创建使用服务模型，可以与集成 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的 VSPackage。  
  
## 本节内容  
 [入门](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 讨论源代码管理包，更高级的一种替代方法实现的源代码管理功能源代码管理插件在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [体系结构](../../extensibility/internals/source-control-vspackage-architecture.md)  
 存在关系图并解释源代码管理包中的元素。  
  
 [功能](../../extensibility/internals/source-control-vspackage-features.md)  
 描述源控件包的各种功能。  
  
 [设计元素](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 描述源代码管理包必须为深入的集成实现 VSPackage 的结构。  
  
## 相关章节  
 [创建了源代码管理插件](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 讨论如何创建提供在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 源代码管理用户界面的源代码管理功能的源代码管理插件 \(UI\)。  
  
 [源代码管理](../../extensibility/internals/source-control.md)  
 讨论实现源代码管理的选项作为 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]一个集成功能。