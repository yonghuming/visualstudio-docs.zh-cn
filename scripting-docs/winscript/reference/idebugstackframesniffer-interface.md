---
title: "IDebugStackFrameSniffer 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer 接口
使您能够枚举已知的组件的逻辑的堆栈帧。 脚本引擎通常实现此接口。 此接口以查找所有堆栈帧过程调试 manager 使用与给定线程关联。  
  
> [!NOTE]
>  调试程序调用此接口从在感兴趣的线程中。 脚本引擎必须标识当前线程，并返回相应的枚举器。  
  
## <a name="methods"></a>方法  
 除了从继承的方法`IUnknown`、`IDebugStackFrameSniffer`接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|返回当前线程的堆栈帧的枚举。|