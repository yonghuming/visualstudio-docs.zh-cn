---
title: "ArrayBuffer.isView 函数 (ArrayBuffer) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5aaae2acb38aa2f8c4b5e49ea203e86665315700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="arraybufferisview-function-arraybuffer"></a>ArrayBuffer.isView 函数 (ArrayBuffer)
确定对象是否提供缓冲区的视图。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
ArrayBuffer.isView(object)  
```  
  
#### <a name="parameters"></a>参数  
 `object`  
 必需。 要测试的对象。  
  
## <a name="return-value"></a>返回值  
 `true`，如果下列之一为 True：  
  
-   `object` 是一个 `DataView` 对象。  
  
-   `object` 是一个类型化数组。  
  
 否则，该方法将返回 `false`。  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 `isView` 函数来测试类型化数组和 `DataView` 对象。  
  
```JavaScript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Uint8ClampedArray 对象](../../javascript/reference/uint8clampedarray-object-javascript.md)