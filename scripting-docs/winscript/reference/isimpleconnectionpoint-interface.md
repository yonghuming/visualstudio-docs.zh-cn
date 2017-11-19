---
title: "ISimpleConnectionPoint 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint 接口
用于描述和枚举的特定连接点上激发的事件提供一种简单方法。 此接口还可以轻松挂钩`IDispatch`这些事件的对象。 此接口是实现通过过程调试管理器 (PDM)，且由脚本引擎使用。  
  
 此接口是可从`IDebugHelper::CreateSimpleConnectionPoint`。  
  
 除了从继承的方法`IUnknown`、`ISimpleConnectionPoint`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|建立简单的连接点对象和客户端的接收器之间的连接。|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|在指定范围的事件中返回的 DISPID 和每个事件的名称。|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|返回公开此接口上的事件数。|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|终止通过以前建立的通知连接`ISimpleConnectionPoint::Advise`。|  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)