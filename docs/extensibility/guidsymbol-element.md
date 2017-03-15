---
title: "GuidSymbol 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML 架构元素 GuidSymbol"
  - "GuidSymbol 元素 (VSCT XML 架构)"
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# GuidSymbol 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`GuidSymbol` 元素包含的 GUID:ID 对，表示菜单、 组或命令的 GUID。 ID 来自 `IDSymbol` 中的元素 `GuidSymbol` 元素。`GuidSymbol` 元素具有 `name` 提供 GUID，它包含在一个友好名称的属性 `value` 属性。  
  
## 语法  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|name|必需。 在 GUID 符号的名称。|  
|值|必需。 在 GUID 符号的 GUID。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[IDSymbol 元素](../extensibility/idsymbol-element.md)|包含的 GUID:ID 对，表示菜单、 组或命令的 ID。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[符号元素](../extensibility/symbols-element.md)|组 `GuidSymbol` .vsct 文件中的元素。|  
  
## 备注  
 通常情况下，.vsct 文件包含三个 `GuidSymbol` 中的元素及其 `Symbols` 部分中，一个用于在程序包本身中，一个为命令集 \(菜单、 组和包提供的命令的集合\)，一个用于按钮和其他可视组件提供图标的位图。 每个 `IDSymbol` 元素中的给定 `GuidSymbol` 元素必须具有一个唯一 `value`。但是， `IDSymbol` ，只要它们具有不同的父，可以在包中存在具有相同的值的元素。  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)