---
title: "IEnumDebugModules2::Skip |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugModules2::Skip
helpviewer_keywords: IEnumDebugModules2::Skip
ms.assetid: 61dc42f4-8544-45bb-8da0-fb22cccec7da
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80a26d7ab621429508956d4060dffe741090a7b7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugmodules2skip"></a>IEnumDebugModules2::Skip
跳过指定数量的元素。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>参数  
 `celt`  
 [in]要跳过的元素数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`。 返回`S_FALSE`如果`celt`大于剩余元素的数目; 否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果`celt`指定一个值大于数剩余元素的枚举设置为结束和`S_FALSE`返回。  
  
## <a name="see-also"></a>另请参阅  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)