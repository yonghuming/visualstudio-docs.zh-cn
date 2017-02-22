---
title: "ButtonText 元素 | Microsoft Docs"
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
  - "ButtonText 元素 (VSCT XML 架构)"
  - "VSCT XML 架构元素 ButtonText"
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# ButtonText 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此字段允许您指定各种菜单中显示的文本。 默认情况下， `ButtonText` 元素出现在菜单控制器中。`ButtonText` 元素也成为默认值，如果其他文本字段为空白。`ButtonText` 元素不能为空，即使指定了其他文本字段。  
  
## 语法  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
 无。  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[字符串元素](../extensibility/strings-element.md)|文本元素，如分组 `ButtonText` 和 `CommandName`。|  
  
## 文本值  
 文本值 `ButtonText` 元素提供了显示的菜单项、 组合和其他包含的可见文本的用户界面 \(UI\) 元素的文本。  
  
## 请参阅  
 [Visual Studio 命令表 \(。Vsct\) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)