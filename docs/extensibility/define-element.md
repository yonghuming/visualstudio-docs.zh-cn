---
title: "定义元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML 架构元素定义"
  - "定义元素 (VSCT XML 架构)"
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 定义元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定义的符号名称和值对。 此符号可由条件属性进行计算。 有关详细信息，请参阅[条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。 另请参阅 [符号元素](../extensibility/symbols-element.md)。  
  
## 语法  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|name|必需。 符号名称:<br /><br /> 名称 \="模式"|  
|值|必需。 符号的值:<br /><br /> 值 \="标准"|  
|条件|可选。 有关更多信息，请参见[条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定义表示命令的 VSPackage 提供了集成的开发环境 \(IDE\) 的所有元素。 例如，菜单项、 菜单、 工具栏和组合框。|  
  
## 示例  
  
```  
<Define name="DEMO_UI"/> <Define name="MODE" value="Standard"/>  
```  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)