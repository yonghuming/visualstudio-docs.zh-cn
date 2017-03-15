---
title: "Xml（XElement 动态属性）| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
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
ms.openlocfilehash: 3bd6e84a3e59033aeb5050c172439bccbd096082
ms.lasthandoff: 02/22/2017

---
# <a name="xml-xelement-dynamic-property"></a>Xml（XElement 动态属性）
获取元素的非格式化 XML 内容。  
  
## <a name="syntax"></a>语法  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 表示元素的非格式化 XML 内容的 <xref:System.String>。  
  
## <a name="remarks"></a>备注  
 此属性等效于 <xref:System.Xml.Linq.XNode?displayProperty=fullName> 类的 <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> 方法，且 `SaveOptions` 参数设置为 <xref:System.Xml.Linq.SaveOptions>。  
  
## <a name="see-also"></a>另请参阅  
 [XElement 类动态属性](../designers/xelement-class-dynamic-properties.md)   
 [值](../designers/value-xelement-dynamic-property.md)
