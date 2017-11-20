---
title: "DebugStackFrameDescriptor 结构 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugstackframedescriptor-structure"></a>DebugStackFrameDescriptor 结构
枚举堆栈帧并在同一线程上将多个枚举器的输出合并。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>成员  
 `pdsf`  
 堆栈帧对象。  
  
 `dwMin`  
 依赖于计算机的表示形式较低的与此堆栈帧关联的物理地址的范围。  
  
 `dwLim`  
 依赖于计算机的表示形式与此堆栈帧关联的物理地址的上限范围。  
  
 `fFinal`  
 该标志指示正在处理的帧。  
  
 `punkFinal`  
 如果此参数不是`NULL`、 合并当前的枚举数应停止，并且应该启动一个新。 该对象指示如何启动新的枚举。  
  
## <a name="remarks"></a>备注  
 过程调试管理器使用此结构进行排序从多个脚本引擎的堆栈帧。 按照约定，堆栈向下增长。 因此，在堆栈长大的体系结构上的地址应成对求反。  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)