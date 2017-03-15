---
title: "CommandPlacements 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandPlacements"
helpviewer_keywords: 
  - "CommandPlacements 元素 (VSCT XML 架构)"
  - "VSCT XML 架构元素 CommandPlacements"
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# CommandPlacements 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CommandPlacements 元素组 CommandPlacement 元素，并且其他 CommandPlacements 分组。  
  
 CommandPlacements 元素是可选的。 如果没有命令、 组或菜单必须包括在辅助位置中，您无需在.vsct 文件中包含此节。  
  
## 语法  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
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
|CommandPlacements|CommandPlacement 元素进行分组和其他 CommandPlacements 分组。|  
|[CommandPlacement 元素](../extensibility/commandplacement-element.md)|使按钮、 组和要包括在多个组或菜单的菜单。|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定义表示命令的所有元素。|  
  
## 示例  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## 请参阅  
 [CommandPlacement 元素](../extensibility/commandplacement-element.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)