---
title: "在 JavaScript 中处理 Windows 运行时事件 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e963472ee51f2439b50807a49425dcd7f6d8443a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="handling-windows-runtime-events-in-javascript"></a>在 JavaScript 中处理 Windows 运行时事件
Windows 运行时事件在 JavaScript 中的表示方式与它们在 C++ 或 .NET Framework 中的表示方式不同。 它们不是类属性，而是表示为传递到类的 `addEventListener` 和 `removeEventListener` 方法的字符串标识符。 例如，可以通过将字符串“replacementchanged”传递给 `Geolocator.addEventListener` 方法来为 [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) 事件添加事件处理程序：  
  
```JavaScript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 你也可以设置 `locator.onpositionchanged` 属性。  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 在 JavaScript 中，Windows 运行时事件参数表示为单个事件对象。 在以下事件处理程序方法的示例中，`ev` 参数是一个同时包含发送方（目标属性）和另一个事件参数的对象。 事件参数是那些针对每个事件编档的参数。  
  
```JavaScript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Windows 运行时功能不适用于在 Internet Explorer 中运行的应用。  
  
## <a name="see-also"></a>另请参阅  
 [在 JavaScript 中使用 Windows 运行时](../jswinrt/using-the-windows-runtime-in-javascript.md)