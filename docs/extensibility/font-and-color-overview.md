---
title: "字体和颜色概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]、 字体和颜色"
  - "字体和颜色控件 [Visual Studio SDK] 编辑器"
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# 字体和颜色概述
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(ide\) 讨论文本的字体和颜色设置 \(IDE\)。  它还引入了类并显示项目的概念，该组件，并描述 Vspackage 和核心编辑器如何使用文本属性。  
  
## 字体和颜色属性页  
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(ide\) 可以通过 **字体和颜色** 属性页 \(IDE\)管理中显示的文本属性。  若要查找 **字体和颜色** 属性页，在 **工具** 菜单上，单击 **选项**。  展开**“环境”**，然后单击**“字体和颜色”**。  
  
## 类别和显示项目  
 字体和颜色会被组织成 **类** 和 **显示项目**。  
  
-   **类** 是许多的 **显示项目**的逻辑或函数容器。  
  
     **类** 列表中 **显示设置。** 下拉框 **字体和颜色** 属性页。  
  
-   **显示项目** 是一个定义完善的文本实体 \(如注释、字符串或将 colorized，同时显示的控制结构。  
  
 每 **显示项目** 在包含它的 **类** 中唯一定义。  因此，多个 **类** 可能存在同名的 **显示项目** 。  
  
## 字体和颜色 VSPackage 控件  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 允许 Vspackage:  
  
-   定义字体和颜色 **类**。  
  
-   指定用于的字体和颜色存在 **显示项目**。  
  
-   与 **字体和颜色** 属性页进行交互。  
  
-   复合多个 **类** 到组中。  
  
-   保持默认设置的更改。  
  
 有两种方式与字体和颜色选择适合在 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]中。  
  
-   一种称为 *语法着色*。  自定义现有 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 编辑器实现语言服务和创建源编辑器的 VSPackage 使用它。  
  
     只有一 **类** 支持此机制，也就是说， **文本编辑器**。  
  
-   ，同时显示文本时，更常规的替代支持其他 **类** 和用户界面元素除了源编辑器之外。  有关更多信息，请参见 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>。  
  
## 核心编辑器文本设置  
 语言服务对象的核心编辑器的字体和颜色设置由 **文本编辑器**在 **显示设置。** 下拉框中的**类** 管理 **字体和颜色** 属性页。  
  
 当使用编辑器时，应使用语言服务提供控件和扩展 **文本编辑器** 设置的专用的字体和颜色控制机制。  框架引用 *语法着色* 并提供:  
  
-   管理显示项目的字体和颜色的简化技术。  
  
     有关更多信息，请参见<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>。  
  
-   显式定义和优化着色机制。  
  
     有关更多信息，请参见 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>。  
  
-   对两个使用内置显示项目的能力从 **文本编辑器类** 和扩展它们。  
  
     有关更多信息，请参见[如何: 使用内置可着色的项](../extensibility/internals/how-to-use-built-in-colorable-items.md)和 [自定义可着色的项](../extensibility/internals/custom-colorable-items.md)。  
  
-   内置和自定义显示项的当前状态的自动持久性与 **文本编辑器** 类别。  
  
 有关语法着色的更多信息 [语法着色在传统语言服务](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)请参见。  
  
## 请参阅  
 [在编辑器中的旧接口](../extensibility/legacy-interfaces-in-the-editor.md)   
 [语法着色在传统语言服务](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)