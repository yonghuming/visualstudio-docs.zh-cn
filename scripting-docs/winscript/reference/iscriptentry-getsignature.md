---
title: "IScriptEntry::GetSignature |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 062f069bb6a19c24f26a6a0bc6a9f4de2292d88f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
返回类型信息`IScriptEntry`函数对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppti`  
 [out]键入与此相关联的信息`IScriptEntry`函数对象。  
  
 `piMethod`  
 [out]中的方法索引`ITypeInfo`对象。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 使用设置类型信息[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)或[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)。 此外可以通过基于内部函数表示形式的条目生成类型信息。  
  
## <a name="see-also"></a>另请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)