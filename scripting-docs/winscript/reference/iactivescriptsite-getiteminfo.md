---
title: "IActiveScriptSite::GetItemInfo |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.GetItemInfo
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccb898c14571d1f1fd1fcae7cb0b9a6d322f2754
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
允许要获取有关与添加的项的信息的脚本引擎[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrName`  
 [in]与中指定的项关联的名称[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
 `dwReturnMask`  
 [in]一个位掩码，指定应返回哪些项目的信息。 脚本引擎应请求信息可能的最小量，因为某些返回参数 (例如， `ITypeInfo`) 可能需要相当长的时间才能加载或生成。 可以是以下值的组合：  
  
|值|含义|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|返回`IUnknown`为此项目的接口。|  
|SCRIPTINFO_ITYPEINFO|返回`ITypeInfo`为此项目的接口。|  
  
 `ppunkItem`  
 [out]接收指向的变量的地址`IUnknown`与给定项相关联的接口。 可以使用脚本引擎`IUnknown::QueryInterface`方法来获取`IDispatch`项的接口。 如果此参数接收 NULL`dwReturnMask`不包括 SCRIPTINFO_IUNKNOWN 值。 此外，接收 NULL，如果没有与项名称; 关联的对象使用此机制来创建一个简单的类时，SCRIPTITEM_CODEONLY 标志设置添加了命名的项[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)方法。  
  
 `ppTypeInfo`  
 [out]接收指向的变量的地址`ITypeInfo`与项关联的接口。 如果此参数接收 NULL`dwReturnMask`不包括 SCRIPTINFO_ITYPEINFO 值，或如果没有可用于此项目类型信息。 如果类型信息不可用，该对象不能源事件，并且必须使用实现名称绑定`IDispatch::GetIDsOfNames`方法。 请注意，`ITypeInfo`检索的接口描述项的组件类 (TKIND_COCLASS)，因为该对象可能支持多个接口和事件接口。 如果项支持`IProvideMultipleTypeInfo`接口，`ITypeInfo`接口检索等同于索引零`ITypeInfo`将使用获得的`IProvideMultipleTypeInfo::GetInfoOfIndex`方法。  
  
## <a name="return-value"></a>返回值  
 返回下列值之一：  
  
|返回值|含义|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|自变量无效。|  
|`E_POINTER`|指定了无效的指针。|  
|`TYPE_E_ELEMENTNOTFOUND`|找不到指定名称的项。|  
  
## <a name="remarks"></a>备注  
 此方法只检索信息由`dwReturnMask`参数; 这将提高性能。 例如，如果`ITypeInfo`接口不需要的项，它只需中未指定`dwReturnMask`。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)