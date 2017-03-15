---
title: "CommandPlacement 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommandPlacements 元素 (VSCT XML 架构)"
  - "VSCT XML 架构元素 CommandPlacements"
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# CommandPlacement 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CommandPlacement 元素使按钮、 组和要包括在多个组或菜单的菜单。 通过使用 CommandPlacement 元素，无需完全重新定义这些项，才能修改用户界面的外观。  
  
 有关详细信息，请参阅[创建可重用的按钮的组](../extensibility/creating-reusable-groups-of-buttons.md)。  
  
## 语法  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|guid|必需。 该命令集，如中所定义的 guid [符号元素](../extensibility/symbols-element.md)。|  
|id|必需。 菜单、 组或命令中定义要放置的 id `Symbols Element`。|  
|priority|必需。 确定其父元素中的可视位置的项。|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|父级|必需。 菜单或承载要放置的项的组。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|指定 CommandPlacements 和 CommandPlacement 元素组。|  
  
## 示例  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## 请参阅  
 [CommandPlacements 元素](../extensibility/commandplacements-element.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)