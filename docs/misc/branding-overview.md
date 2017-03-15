---
title: "外观方案概述 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“关于”对话框"
  - "VSPackage, 初始屏幕"
  - "VSPackage, 外观方案"
ms.assetid: a47b3645-574c-41c7-8a97-d071cd6b1e82
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# 外观方案概述
若要显示产品信息。屏幕或 **帮助** 对话框， VSPackage 必须:  
  
-   可以通过产品详细信息。 InstalledProducts 注册表项下。  
  
     \- 或 \-  
  
-   实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>。  
  
 托管包框架 \(MPF\)提供 <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> 属性对控件注册在 InstalledProducts 注册表项下。  有关更多信息，请参见 [如何：设置 VSPackage 的外观方案（C\# 和 Visual Basic）](../misc/how-to-brand-a-vspackage-csharp-and-visual-basic.md)。  
  
 Visual Studio 库提供 `IVsInstalledProductImpl` 模板类创建 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>的实现。  有关更多信息，请参见 [如何：设置 VSPackage \(C\+\+\) 外观方案](../misc/how-to-brand-a-vspackage-cpp.md)。  
  
 实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> 显式将该属性或模板远比强大  
  
-   可以指定与 **帮助** 图标不同的初始屏幕图标。  
  
-   可以指定与 **帮助** 产品名称不同的初始屏幕产品名。  
  
    > [!IMPORTANT]
    >  如果使用 <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> 并实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>，接口优先。  
  
    > [!NOTE]
    >  相同类型的图标资源用于初始屏幕和 **帮助** 对话框使用。  VSPackage 图标资源应包括初始屏幕的一个 16 x 16、图像和 **帮助** 对话框的 32 × 32 图像。  如果只提供一个图像大小，则将调整根据需要，但是，可视化会导致不欠佳的。  
  
 有关相关任务的列表，请参见 [Vspackage](../extensibility/internals/vspackages.md)。  
  
## 请参阅  
 [Vspackage](../extensibility/internals/vspackages.md)   
 [Visual Studio 库概述](../misc/visual-studio-library-overview.md)