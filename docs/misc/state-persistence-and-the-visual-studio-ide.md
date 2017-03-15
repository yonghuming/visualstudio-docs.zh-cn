---
title: "状态保持和 Visual Studio IDE | Microsoft Docs"
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
  - "IDE 设置, 状态保持"
  - "用户设置 [Visual Studio SDK], 保持"
  - "“工具选项”页 [Visual Studio SDK], 保持设置"
  - "IDE, 状态保持"
  - "保持, 用户设置"
ms.assetid: fdd49bb1-ed3b-4428-b685-de65c3215c1c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# 状态保持和 Visual Studio IDE
在集成开发环境 \(ide\) 的 **工具** 菜单的 **导入\/导出设置** 命令 \(IDE\)导入和导出 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 环境的自定义。  在 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置 API 使 VSPackage 定义 \(状态变量的组\) 将保留的一个或多个设置类别，当用户选择 **导入\/导出设置** 命令时。  
  
 *自定义下落点，*GUID 在其自己的注册表项名称唯一标识每设置类别和定义，称为 "。  
  
> [!NOTE]
>  **工具 选项** 页、 **工具箱**和 `Microsoft.VisualStudio.Shell.DialogPage` 的标准实现自动提供持久性支持。  设置 API 可以重写默认结构。  有关更多信息，请参见[扩展工具箱](../misc/extending-the-toolbox.md)、[选项页](../misc/options-pages.md)和<xref:Microsoft.VisualStudio.Shell.DialogPage>。  
  
## 本节内容  
 [用户设置的的支持](../extensibility/internals/support-for-user-settings.md)  
 描述注册表用于设置 \(自定义下落点\) 和属性指定特定 VSPackage 使用的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置实现。  
  
 [如何：使用互操作程序集导出设置](../misc/how-to-export-settings-by-using-interop-assemblies.md)  
 提供详细说明如何实现用于保存的配置数据支持通过使用互操作程序集基于 Vspackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置结构。  
  
 [如何：使用互操作程序集导入设置](../misc/how-to-use-interop-assemblies-to-import-settings.md)  
 提供详细说明如何实现用于检索配置数据支持通过使用互操作程序集基于 Vspackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置结构。  
  
 [导出设置](../misc/exporting-settings.md)  
 包含详细说明如何实现用于保存的配置数据支持通过使用托管包的结构基于 Vspackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置结构。  
  
 [导入设置](/visual-cpp/misc/importing-settings)  
 提供详细说明如何实现用于检索配置数据支持通过使用托管包的结构基于 Vspackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置结构。  
  
## 相关章节  
 [Working with Settings](http://msdn.microsoft.com/zh-cn/4c0a56ab-6091-4ebc-9dc7-52c40846bacb)  
 介绍如何管理 IDE 中导出\/导入部分。  
  
 [选项页](../misc/options-pages.md)  
 描述 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 用于管理现有或创建的新 **工具选项** 页自动提供的支持。  
  
 [扩展工具箱](../misc/extending-the-toolbox.md)  
 解释 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 用于管理或扩展 **工具箱**自动提供的支持。  
  
 [扩展的用户设置和选项](../extensibility/extending-user-settings-and-options.md)  
 描述如何程序获取并保留用户首选项的 VSPackage。