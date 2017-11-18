---
title: "moveFirst 方法 (Enumerator) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: moveFirst
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: MoveFirst method
ms.assetid: 96eedc66-7974-443c-b0cd-55373a7c0e59
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af8c59194a5655730e8509b43533f699aeef51d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="movefirst-method-enumerator-javascript"></a>moveFirst 方法 (Enumerator) (JavaScript)
将集合中的当前项重置为第一项。  
  
> [!WARNING]
>  此对象仅在 Internet Explorer 中受支持。  
  
## <a name="syntax"></a>语法  
  
```  
  
enumObj.moveFirst( )   
```  
  
## <a name="remarks"></a>备注  
 所需 *enumObj* 引用可以是任何 `Enumerator` 对象。  
  
 如果集合中没有项，则将当前项设置为未定义。  
  
## <a name="example"></a>示例  
 在以下示例中，使用 `moveFirst` 方法从列表开始处计算 `Drives` 集合成员数：  
  
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
 [atEnd 方法 (Enumerator)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [item 方法 (Enumerator)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveNext 方法 (Enumerator)](../../javascript/reference/movenext-method-enumerator-javascript.md)