---
title: "Group 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML 架构元素、 组"
  - "Groups 元素 (VSCT XML 架构)"
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Group 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定义 VSPackage 命令组。  
  
## 语法  
  
```  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|guid|必需。 ID 的 GUID 的命令标识符的 GUID。|  
|id|必需。 ID 的 GUID 的命令标识符的 ID。|  
|priority|可选。 一个数字值，指定的优先级。|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|父级|可选。 该按钮的父元素。|  
|批注|可选注释。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[Groups 元素](../extensibility/groups-element.md)|包含定义 VSPackage 的命令组的条目。|  
  
## 示例  
  
```  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/> </Group>  
```  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)