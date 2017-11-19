---
title: "IDebugBinder3::FindAlias |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::FindAlias
helpviewer_keywords: IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f209829e3b6c76571a53370c11c6d6d7343b088c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
此方法查找别名，指定一个名称。 这将在程序中搜索所有别名。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pcstrName`  
 [in]若要查找的别名的名称。  
  
 `ppAlias`  
 [out]找到 （如果有） 的别名由[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)接口。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回`S_FALSE`（如果找不到别名） 或错误代码。  
  
## <a name="remarks"></a>备注  
 此方法将目标对象初始化为 null 之前调用;然后，它测试有空值以确定已找到别名。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)