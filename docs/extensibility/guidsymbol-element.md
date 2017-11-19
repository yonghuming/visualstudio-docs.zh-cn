---
title: "GuidSymbol 元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dcad9882b1c72c15837529d736eeabff58f3826
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="guidsymbol-element"></a>GuidSymbol 元素
`GuidSymbol`元素包含的 guid: id 对，表示菜单、 组或命令的 GUID。 ID 来自`IDSymbol`中的元素`GuidSymbol`元素。 `GuidSymbol`元素具有`name`提供的 guid，它包含在一个友好名称的属性`value`属性。  
  
## <a name="syntax"></a>语法  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|name|必需。 在 GUID 符号的名称。|  
|值|必需。 在 GUID 符号的 GUID。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[IDSymbol 元素](../extensibility/idsymbol-element.md)|包含表示菜单、 组或命令的 guid: id 对的 ID。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Symbols 元素](../extensibility/symbols-element.md)|组`GuidSymbol`.vsct 文件中的元素。|  
  
## <a name="remarks"></a>备注  
 通常情况下，.vsct 文件包含三种`GuidSymbol`中的元素及其`Symbols`部分、 一个用于包本身、 一个用于命令集 （菜单、 组和包提供的命令的集合） 和另一个用于提供的位图为按钮和其他可视组件的图标。 每个`IDSymbol`元素中的给定`GuidSymbol`元素必须具有唯一`value`。但是， `IDSymbol` ，只要它们具有不同的父，可以在包中存在具有相同的值的元素。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 命令表格 (.Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)