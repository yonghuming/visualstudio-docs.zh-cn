---
title: "IScriptScriptlet 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3fa3253997d3a09a7170f3795bf8a7bbf8a182c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet 接口
实现的对象`IScriptScriptlet`接口表示一个事件处理程序脚本。  
  
 除了从继承的方法`IScriptEntry`、`IScriptScriptlet`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|返回与 scriptlet 关联事件的名称。|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|返回与 scriptlet 相关联的简单事件名称。 这是不包含任何空格的单个词名称。|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|返回的最后一个标识符中 scriptlet 对象主机的完全限定名称。|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|设置与 scriptlet 相关联的事件的名称。|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|设置与 scriptlet 相关联的简单事件名称。 这是不包含任何空格的单个词名称。|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|设置 scriptlet 对象主机的完全限定名称中的最后一个标识符。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本创作接口](../../winscript/reference/active-script-authoring-interfaces.md)