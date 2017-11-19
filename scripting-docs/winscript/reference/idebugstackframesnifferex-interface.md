---
title: "IDebugStackFrameSnifferEx 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx 接口
使您能够枚举已知的组件的逻辑的堆栈帧。 脚本引擎通常实现此接口。 此接口以查找所有堆栈帧过程调试 manager 使用与给定线程关联。  
  
> [!NOTE]
>  此接口是从感兴趣的线程中调用的。 接口的实现必须标识当前线程，并返回相应的枚举器。  
  
 除了从继承的方法`IDebugStackFrameSniffer`、`IDebugStackFrameSnifferEx`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|返回当前线程的堆栈帧的枚举。|