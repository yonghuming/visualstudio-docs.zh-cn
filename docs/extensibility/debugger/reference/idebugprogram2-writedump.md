---
title: "IDebugProgram2::WriteDump |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::WriteDump
helpviewer_keywords: IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b68392d94b16f13106e421c5d466e3fbdf4a2b27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
转储写入文件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>参数  
 `DumpType`  
 [in]取值范围为[DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)枚举，它指定的一种转储，例如、 short 或 long 类型的值。  
  
 `pszDumpUrl`  
 [in]要写入到转储的 URL。 通常，这是形式`file://c:\path\filename.ext`，但可能是任何有效的 URL。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 程序转储通常将包括当前堆栈帧，堆栈本身、 运行程序，并可能程序拥有任何内存中的线程的列表。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)