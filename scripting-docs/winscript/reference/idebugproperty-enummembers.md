---
title: "IDebugProperty::EnumMembers |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.EnumMembers
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cb57f2609fcd9a80e2a9e0dfd63637e6f700047
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
枚举的成员的属性。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwFieldSpec`  
 [in]指定`DBGPROP_INFO_FLAGS`确定枚举的调试属性结构中的哪些字段是必填的常量。  
  
 `nRadix`  
 [in]用于解释的任何数字信息的基数。  
  
 `refiid`  
 [in]为筛选枚举数传递的此 IID。 IID 是之一`IDebugPropertyEnumType`继承的接口`IDebugPropertyEnumType_All`。  
  
 `ppEnum`  
 [out]返回`IEnumDebugPropertyInfo`枚举的成员属性的接口。  
  
## <a name="return-value"></a>返回值  
 返回一个有效`HRESULT`，通常`S_OK`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType_All 接口](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo 接口](../../winscript/reference/ienumdebugpropertyinfo-interface.md)