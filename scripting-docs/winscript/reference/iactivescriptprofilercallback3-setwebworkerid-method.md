---
title: "Iactivescriptprofilercallback3:: Setwebworkerid 方法 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId 方法
通知探查器有关要用于此分析会话的辅助 ID。 如果函数不在页的上下文中执行的则不会调用此方法。 值`webWorkerId`对于每个工作进程，从 1 开始的 1 为增量。 ID 值不应是稳定超出会话，并且仅对辅助进程已创建的顺序对应。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>参数  
 `webWorkerId`  
 Web 辅助进程 id。  
  
## <a name="return-value"></a>返回值  
 通过脚本引擎忽略此方法的返回值。