---
title: "JS_NATIVE_FRAME 结构 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7e93041a6dec767cb3bb11382abfb562068c925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="jsnativeframe-structure"></a>JS_NATIVE_FRAME 结构
表示堆栈帧。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>成员  
 `InstructionOffset`  
 指令指针。  
  
 `ReturnOffset`  
 寄信人地址。  
  
 `FrameOffset`  
 帧指针。  
  
 `StackOffset`  
 堆栈指针。  
  
## <a name="remarks"></a>备注  
 `JS_NATIVE_FRAME`结构由`IJsStackFrameEnumerator`。  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)