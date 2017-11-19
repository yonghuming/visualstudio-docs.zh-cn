---
title: "IDebugExtendedProperty 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugExtendedProperty interface
ms.assetid: e92ea064-0d92-44cf-bb9f-abda783d84be
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11edca1fbce6b7dab755a25dfc3e192225b5f6e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugextendedproperty-interface"></a>IDebugExtendedProperty 接口
扩展`IDebugProperty`接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 除了从继承的方法`IDebugProperty`，此接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugExtendedProperty::GetExtendedPropertyInfo](../../winscript/reference/idebugextendedproperty-getextendedpropertyinfo.md)|获取`ExtendedDebugPropertyInfo`描述此`IDebugExtendedProperty``.`|  
|[IDebugExtendedProperty::EnumExtendedMembers](../../winscript/reference/idebugextendedproperty-enumextendedmembers.md)|枚举的扩展属性的成员。|  
  
## <a name="requirements"></a>要求  
 标头： dbgprop.h  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)