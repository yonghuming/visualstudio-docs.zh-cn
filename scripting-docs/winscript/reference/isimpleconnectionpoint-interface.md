---
title: "ISimpleConnectionPoint 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ISimpleConnectionPoint 接口"
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint 接口
提供描述提供了一种简单的方法，并枚举在特定激发的事件连接点。  此接口还可以轻松地安装了这些事件的一 `IDispatch` 对象。  此接口由处理实现调试管理器\(PDM\)和使用由脚本引擎。  
  
 此接口从 `IDebugHelper::CreateSimpleConnectionPoint`可用。  
  
 除了从 `IUnknown` 继承的方法之外，`ISimpleConnectionPoint` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|生成简单的之间的连接连接点对象和客户端的接收器。|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|返回DISPID和名称每个事件在事件中与指定的范围。|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|返回此接口公开的事件数。|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|终止先前通过 `ISimpleConnectionPoint::Advise` 建立的通知连接。|  
  
## 请参阅  
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)