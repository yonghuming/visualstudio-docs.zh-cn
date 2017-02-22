---
title: "Icon 元素 | Microsoft Docs"
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
  - "VSCT XML 架构元素，图标"
  - "Icon 元素 (VSCT XML 架构)"
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Icon 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

图标标记的 guid 属性是定义位图的 guid。  Id 属性选择位图条带中的槽。 此元素为可选元素。  如果省略此元素的值 **guidOfficeIcon:msotcidNoIcon** 将隐式。  
  
## 语法  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|guid|必需。 定义位图的 guid。|  
|id|必需。 选择位图条带中的槽。|  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|无。|无。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[按钮元素](../extensibility/buttons-element.md)||  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)