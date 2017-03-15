---
title: "有关配置和 SelectedItem 对象的自动化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自动化 [Visual Studio SDK]，SelectedItem 对象"
  - "生成自动化 [Visual Studio SDK]"
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 有关配置和 SelectedItem 对象的自动化
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

可以自动生成，并且选定的项。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]处理。  
  
## 生成的自动化  
 生成或配置具有提供的一个自动化模型，以便在实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>时。  有关更多信息，请参见 [了解生成配置](../../ide/understanding-build-configurations.md)。  
  
 如果创建 VSPackage 并希望将控件配置选项，则必须使用自动化模型。  
  
## SelectedItem 的自动化  
 ，因为 Visual Studio 包含标准实现，不必为 `SelectedItem` 对象提供实现。  但是，您可以实现 `SelectedItem` 对象是否喜欢。  您必须实现包含 `SelectedItem` 接口的对象并返回到调用响应到与 VSITEMID 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法设置为 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [导致自动化模型](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [了解生成配置](../../ide/understanding-build-configurations.md)