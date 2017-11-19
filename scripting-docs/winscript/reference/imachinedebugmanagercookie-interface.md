---
title: "IMachineDebugManagerCookie 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie 接口
类似于`IMachineDebugManager`接口，`IMachineDebugManagerCookie`接口支持调试 cookie。  
  
 此接口 (连同`IDebugCookie`接口) 允许脚本在脚本调试器进程中运行，而无需调试器保持跟踪的这些脚本。  
  
 脚本调试程序调用`IDebugCookie::SetDebugCookie`方法过程调试管理器 (PDM)。 然后，PDM 会发送此 cookie 与任何请求以添加或删除脚本的应用程序到或从机调试管理器 (MDM)，一起使用的方法`IMachineDebugManagerCookie`接口。 MDM 然后通知更改，但具有该 cookie 的那个除外的每个的调试器。  
  
 除了从继承的方法`IUnknown`、`IMachineDebugManagerCookie`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|添加应用程序与运行应用程序列表。|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|返回当前正在运行的应用程序的列表的枚举。|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|从运行中移除应用程序应用程序列表。|  
  
## <a name="see-also"></a>另请参阅  
 [IMachineDebugManager 接口](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie 接口](../../winscript/reference/idebugcookie-interface.md)