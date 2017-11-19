---
title: "IScriptEntry 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a785be8777cf3400f7723c24f1022bad6e22e330
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentry-interface"></a>IScriptEntry 接口
实现的对象`IScriptEntry`接口表示脚本块或函数对象。  
  
 除了从继承的方法`IScriptNode`、`IScriptEntry`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|返回的正文对应的文本`IScriptEntry`脚本块、 函数块或 scriptlet。|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|返回标识的项名称`IScriptEntry`对象。|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|对于表示单个对象 （如函数） 的条目，返回对象的名称。|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|返回的起始位置和长度的一个条目。|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|返回类型信息`IScriptEntry`函数对象。|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|返回对应于文本`IScriptEntry`脚本块中或包含在源代码`IScriptScriptlet`事件处理程序。|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|设置的正文中的文本`IScriptEntry`脚本块或`IScriptScriptlet`scriptlet。|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|设置标识的项名称`IScriptEntry`对象。|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|对于表示单个对象 （如函数） 的条目，设置对象的名称。|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|设置类型信息`IScriptEntry`函数对象。|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|设置对应的文本`IScriptEntry`脚本块中或包含在源代码`IScriptScriptlet`事件处理程序。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本创作接口](../../winscript/reference/active-script-authoring-interfaces.md)