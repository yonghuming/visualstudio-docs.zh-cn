---
title: "IEnumDebugStackFrames 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IEnumDebugStackFrames interface
ms.assetid: 13484429-0140-4f4f-8502-3ca2a0553ed4
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0174839a25695e9594b4cbbf4db6a302f5a2446
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugstackframes-interface"></a>IEnumDebugStackFrames 接口
枚举堆栈帧对应于一个线程。  
  
## <a name="methods"></a>方法  
 除了从继承的方法`IUnknown`、`IEnumDebugStackFrames`接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IEnumDebugStackFrames::Next](../../winscript/reference/ienumdebugstackframes-next.md)|检索指定的数量的段中枚举序列。|  
|[IEnumDebugStackFrames::Skip](../../winscript/reference/ienumdebugstackframes-skip.md)|跳过指定的数目的段中枚举序列。|  
|[IEnumDebugStackFrames::Reset](../../winscript/reference/ienumdebugstackframes-reset.md)|将枚举序列重置到开头。|  
|[IEnumDebugStackFrames::Clone](../../winscript/reference/ienumdebugstackframes-clone.md)|创建一个枚举器，其中包含与当前的枚举器相同的状态。|