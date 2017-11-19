---
title: "IDebugDisassemblyStream2::Seek |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::Seek
helpviewer_keywords: IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61ef1e649a80fcda5ec3ce4be6c74b154c17f9a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
将读取的指针移反汇编流给定数目的相对于指定位置的说明中。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwSeekStart`  
 [in]取值范围为[SEEK_START](../../../extensibility/debugger/reference/seek-start.md)指定开始查找过程的相对位置的枚举。  
  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)表示搜索操作是相对于代码上下文对象。 仅当使用此参数`dwSeekStart`  =  `SEEK_START_CODECONTEXT`; 否则为将忽略此参数，并且可以是 null 值。  
  
 `uCodeLocationId`  
 [in]查找操作是相对于代码位置标识符。 如果使用此参数`dwSeekStart`  =  `SEEK_START_CODELOCID`; 否则为此参数将被忽略，并且可以设置为 0。 请参阅备注部分[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)方法有关的代码位置标识符的说明。  
  
 `iInstructions`  
 [in]将相对于中指定位置对指令数`dwSeekStart`。 此值可以是负值以向后移动。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`。 返回`S_FALSE`搜寻位置是否可用的说明超出列表的位置。 否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果 seek 到之前的位置的列表，则将读取的位置设置为列表中的第一个指令。 如果看到的是将其置于之后列表的末尾，读取的位置将设置到最后一个指令在列表中。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)