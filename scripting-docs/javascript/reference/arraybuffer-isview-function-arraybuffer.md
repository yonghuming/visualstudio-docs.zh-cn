---
title: "ArrayBuffer.isView 函数 (ArrayBuffer) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ArrayBuffer.isView 函数 (ArrayBuffer)
确定对象是否提供缓冲区的视图。  
  
## 语法  
  
```javascript  
ArrayBuffer.isView(object)  
```  
  
#### 参数  
 `object`  
 必需。  要测试的对象。  
  
## 返回值  
 `true`，如果下列之一为 True：  
  
-   `object` 是一个 `DataView` 对象。  
  
-   `object` 是一个类型化数组。  
  
 否则，该方法将返回 `false`。  
  
## 备注  
  
## 示例  
 下面的示例演示如何使用 `isView` 函数来测试类型化数组和 `DataView` 对象。  
  
```javascript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## 要求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 请参阅  
 [Uint8ClampedArray 对象](../../javascript/reference/uint8clampedarray-object-javascript.md)