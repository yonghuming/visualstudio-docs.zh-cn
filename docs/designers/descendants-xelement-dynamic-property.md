---
title: "子代（XElement 动态属性）| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 78a9401593e900969c27dcd223a2510ea2ffd24f
ms.lasthandoff: 02/22/2017

---
# <a name="descendants-xelement-dynamic-property"></a>子代（XElement 动态属性）
获取一个索引器，用于检索与指定扩展名匹配的当前元素的所有子代元素。  
  
## <a name="syntax"></a>语法  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 一个类型为 `IEnumerable<XElement> Item(String expandedName)` 的索引器。 此索引器获取指定子代元素的扩展名，并返回 <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` 集合中的匹配子元素。  
  
## <a name="remarks"></a>备注  
 此属性等效于 <xref:System.Xml.Linq.XContainer> 类的 <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> 方法。  
  
 返回集合中的元素按 XML 源文档顺序排列。  
  
 此属性使用延迟执行。  
  
## <a name="see-also"></a>另请参阅  
 [XElement 类动态属性](../designers/xelement-class-dynamic-properties.md)   
 [元素](../designers/elements-xelement-dynamic-property.md)
