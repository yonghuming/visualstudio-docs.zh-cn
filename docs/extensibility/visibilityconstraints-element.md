---
title: "VisibilityConstraints 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisibilityConstraints"
helpviewer_keywords: 
  - "VSCT XML 架构元素 VisibilityConstraints"
  - "VisibilityConstraints 元素 (VSCT XML 架构)"
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# VisibilityConstraints 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VisibilityConstraints 元素可确定静态组的可见性的命令和工具栏。 第一次通过控制可见性 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成的开发环境 \(IDE\) 而无需加载 VSPackage。  
  
## 语法  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[VisibilityItem 元素](../extensibility/visibilityitem-element.md)|确定静态可见性命令和工具栏。|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|确定静态组的可见性的命令和工具栏。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定义表示 VSPackage 提供到 IDE 的命令 \(例如，菜单项、 菜单、 工具栏和组合框\) 的所有元素。|  
  
## 示例  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## 请参阅  
 [VisibilityItem 元素](../extensibility/visibilityitem-element.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)