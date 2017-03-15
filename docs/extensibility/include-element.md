---
title: "Include 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Include"
helpviewer_keywords: 
  - "包括元素 (VSCT XML 架构)"
  - "VSCT XML 架构元素包括"
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Include 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Include 元素指定可以找到的文件提供包含要插入到当前文件的路径。  所有的符号和定义的类型将成为已编译的结果的一部分。  
  
## 语法  
  
```c#  
<Include href="stdidcmd.h" />  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|href|必需。 标头文件的路径:<br /><br /> "href\="stdidcmd.h|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|无。|无。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定义表示命令的元素的所有 — 也就是说，菜单项、 菜单、 工具栏和组合框 — VSPackage 提供到 IDE。|  
  
## 示例  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)