---
title: "VisibilityItem 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VisibilityItem 元素 (VSCT XML 架构)"
  - "VSCT XML 架构元素 VisibilityItem"
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# VisibilityItem 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`VisibilityItem` 元素确定的静态可见性命令和工具栏。 每个条目用于标识某个命令或菜单上，以及关联的命令 UI 上下文。 Visual Studio 检测命令、 菜单和工具栏和它们的可见性，而不加载 Vspackage 定义它们。 IDE 将使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 方法，以确定命令 UI 上下文是否处于活动状态。  
  
 Visual Studio 加载 VSPackage 中之后，期望命令可见性由 VSPackage 而不是 `VisibilityItem`。 若要确定命令的可见性，可以实现任何一个 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 事件处理程序或 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法，具体取决于您的命令的实现方式。  
  
 命令或菜单上具有 `VisibilityItem` 仅当关联的上下文处于活动状态时出现的元素。 您可以关联具有一个或多个命令 UI 上下文的单个命令、 菜单或工具栏，方法是包括为每个命令上下文组合的条目。 如果与多个命令 UI 上下文相关联的命令或菜单，然后命令或菜单时才可见关联的命令 UI 上下文中的任何一个处于活动状态。  
  
 `VisibilityItem` 元素仅适用于命令、 菜单和工具栏，不到组。 不具有相关的元素 `VisibilityItem` 元素是可见的只要其父菜单处于活动状态。  
  
## 语法  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|guid|必需。 ID 的 GUID 的命令标识符的 GUID。|  
|id|必需。 ID 的 GUID 的命令标识符的 ID。|  
|上下文|必需。 该命令处于可见 UI 上下文。|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
 无  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints` 元素可确定静态组的可见性的命令和工具栏。|  
  
## 备注  
 在中定义的标准的 Visual Studio UI 上下文 *Visual Studio SDK 安装路径*\\VisualStudioIntegration\\Common\\Inc\\vsshlids.h 文件以及如下所示 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> 和 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 类。 在中定义一组更完整的 UI 上下文 <xref:Microsoft.VisualStudio.VSConstants> 类。  
  
## 示例  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)