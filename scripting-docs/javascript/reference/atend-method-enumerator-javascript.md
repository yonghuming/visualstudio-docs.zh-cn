---
title: "atEnd 方法 (Enumerator) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: atEnd
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: atEnd method
ms.assetid: 326808fb-9a0f-428e-aff1-b11b237913f1
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b5097d00c11ffafc314264f134aedda3981c8e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="atend-method-enumerator-javascript"></a>atEnd 方法 (Enumerator) (JavaScript)
返回一个布尔值，该值指示枚举器是否在集合的末尾。  
  
> [!WARNING]
>  此对象仅在 Internet Explorer 中受支持。  
  
## <a name="syntax"></a>语法  
  
```  
  
myEnum.atEnd()  
```  
  
## <a name="remarks"></a>备注  
 所需 *myEnum* 引用可以是任何 `Enumerator` 对象。  
  
 如果当前项是集合中的最后一项、集合为空或当前项未定义， `atEnd` 方法将返回 **true** 。 否则，返回 **false**。  
  
## <a name="example"></a>示例  
 在以下代码中，使用 `atEnd` 方法确定是否已到达驱动器列表的末尾：  
  
```JavaScript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## <a name="requirements"></a>要求  
 在以下文档模式中受支持：Quirks、Internet Explorer 6 标准模式、Internet Explorer 7 标准模式、Internet Explorer 8 标准模式、Internet Explorer 9 标准模式和 Internet Explorer 10 标准模式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中不受支持。 请参阅 [版本信息](../../javascript/reference/javascript-version-information.md)。  
  
 **适用于**： [Enumerator Object](../../javascript/reference/enumerator-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [item 方法 (Enumerator)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveFirst 方法 (Enumerator)](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [moveNext 方法 (Enumerator)](../../javascript/reference/movenext-method-enumerator-javascript.md)   
 [Enumerator 对象](../../javascript/reference/enumerator-object-javascript.md)