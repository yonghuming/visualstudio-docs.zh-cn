---
title: "IDSymbol 元素 | Microsoft Docs"
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
  - "IDSymbol 元素 (VSCT XML 架构)"
  - "VSCT XML 架构元素 IDSymbol"
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDSymbol 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`IDSymbol` 元素包含的 GUID:ID 对，表示菜单、 组或命令的 ID。 GUID 来自父 `GuidSymbol` 元素。`IDSymbol` 元素具有 `name` 提供 ID，它包含在一个友好名称的属性 `value` 属性。  
  
## 语法  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|name|必需。 ID 符号名称。|  
|值|必需。 ID 符号的数字 ID 值。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[GuidSymbol 元素](../extensibility/guidsymbol-element.md)|包含的 GUID:ID 对，表示菜单、 组或命令的 GUID。 对 `IDSymbol` 元素进行分组。|  
  
## 备注  
 每个 `IDSymbol` 元素中的给定 `GuidSymbol` 元素必须具有一个唯一 `value`。 但是， `IDSymbol` ，只要它们具有不同的父，可以在包中存在具有相同的值的元素。  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)