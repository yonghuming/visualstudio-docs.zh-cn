---
title: "IDispatchEx::DeleteMemberByName |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb9a9dfd979954c42101fde41819d7e12db59e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
按名称删除成员。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>参数  
 `bstrName`  
 要删除的成员名称。  
  
 `grfdex`  
 确定是否区分大小写的成员名称。 这可以是下列值之一：  
  
|值|含义|  
|-----------|-------------|  
|fdexNameCaseSensitive|在区分大小写方式中进行的名称查找的请求。 可以忽略不支持区分大小写查找的对象。|  
|fdexNameCaseInsensitive|在不区分大小写方式中进行的名称查找的请求。 可以忽略不支持不区分大小写查找的对象。|  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|成员存在，但不能删除。|  
  
## <a name="remarks"></a>备注  
 如果删除成员，则需要保持对有效 DISPID `GetNextDispID`。  
  
 如果删除具有给定名称的成员，并且以后重新创建具有相同名称的成员，DISPID 应相同。 （只有大小写不同的成员是否"相同"与对象相关。）  
  
## <a name="example"></a>示例  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>另请参阅  
 [IDispatchEx 接口](../../winscript/reference/idispatchex-interface.md)