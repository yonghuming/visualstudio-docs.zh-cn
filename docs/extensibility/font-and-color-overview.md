---
title: "字体和颜色概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13a2a8b584af507f8937fd6abb46c85f329de0b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="font-and-color-overview"></a>字体和颜色概述
本主题讨论中的文本字体和颜色设置[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)。 此外引入了类别和显示项的概念并介绍 Vspackage 和核心编辑器如何使用文本特性。  
  
## <a name="the-fonts-and-colors-property-page"></a>字体和颜色属性页  
 你可以管理中显示的文本特性[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 通过**字体和颜色**属性页。 若要查找**字体和颜色**属性页，请在**工具**菜单上，单击**选项**。 展开**环境**，然后单击**字体和颜色**。  
  
## <a name="categories-and-display-items"></a>类别和显示项  
 字体和颜色组织成**类别**和**显示项**。  
  
-   A**类别**是大量的逻辑或功能容器**显示项**。  
  
     一份**类别**处于**显示其设置**下拉列表框**字体和颜色**属性页。  
  
-   A**显示项**是定义完善的文本的实体，例如注释、 字符串或控制结构，它是以显示时着色。  
  
 每个**显示项**中唯一定义**类别**包含它。 因此，多个**类别**可以**显示项**具有相同的名称。  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage 控制的字体和颜色  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]允许 VSPackages 迁移到：  
  
-   定义字体和颜色**类别**。  
  
-   指定的字体和颜色来显示**显示项**。  
  
-   与交互**字体和颜色**属性页。  
  
-   聚合多个**类别**分组。  
  
-   保留默认设置中的更改。  
  
 有两种方法与中的字体和颜色选择进行交互[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]。  
  
-   一种方法被称为*语法着色*。 它由自定义现有的 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]编辑器以实现语言服务和创建编辑器的源。  
  
     只有一个**类别**支持这种机制，即，**文本编辑器**。  
  
-   更多常规的替代项支持所有其他**类别**和源代码编辑器中显示文本时以外的用户界面组件。 有关更多信息，请参见<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>。  
  
## <a name="core-editor-text-settings"></a>核心编辑器文本设置  
 语言服务对象的核心编辑器的字体和颜色设置均由**文本 EditorCategory**中找到**显示其设置**下拉列表框**字体和颜色**属性页。  
  
 使用编辑器时, 应使用专用的字体和颜色控制机制语言服务提供的控制和扩展**文本编辑器**设置。 机制称为*语法着色*并提供：  
  
-   用于管理的字体和颜色显示项的非常简化的技术。  
  
     有关详细信息，请参阅 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>。  
  
-   一种明确定义且经过优化着色机制。  
  
     有关更多信息，请参见<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>。  
  
-   能够同时使用内置的显示项从**文本 EditorCategory**并对它们进行扩展。  
  
     有关详细信息，请参阅[如何： 使用内置可着色项](../extensibility/internals/how-to-use-built-in-colorable-items.md)和[自定义可着色项](../extensibility/internals/custom-colorable-items.md)。  
  
-   当前状态的两个内置和自定义自动持久性显示与项**文本编辑器**类别。  
  
 有关详细信息的语法着色，请参阅[旧语言服务中的语法着色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在编辑器中的旧接口](../extensibility/legacy-interfaces-in-the-editor.md)   
 [在旧版语言服务中进行语法着色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)