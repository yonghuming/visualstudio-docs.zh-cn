---
title: "IDebugHelper 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugHelper 接口"
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper 接口
作为一个工厂用作对象浏览器和简单的连接点。  进程内调试管理器\(PDM\)实现此接口，该接口由脚本引擎使用。  
  
 除了从 `IUnknown` 继承的方法之外，`IDebugHelper` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|返回包装个变体的属性浏览器。|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|返回包装个变体的属性浏览器，并允许不同的值或VARTYPE类型的自定义转换为字符串。|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|返回包装特定 `IDispatch` 对象的事件接口。|