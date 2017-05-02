---
title: "IActiveScriptSite::GetItemInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetItemInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetItemInfo"
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetItemInfo
允许脚本引擎获取有关项目的信息添加与 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 方法。  
  
## 语法  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### 参数  
 `pstrName`  
 \[in\]名称与项目，在 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 方法中指定。  
  
 `dwReturnMask`  
 \[in\]一个位掩码指定应返回有关项目的信息。  脚本引擎应该请求可能最少量信息，因为某些返回参数\(例如，`ITypeInfo`\)可能需要大量时间加载或生成。  可为下列值的组合：  
  
|值|含义|  
|-------|--------|  
|SCRIPTINFO\_IUNKNOWN|返回此项目的 `IUnknown` 接口。|  
|SCRIPTINFO\_ITYPEINFO|返回此项目的 `ITypeInfo` 接口。|  
  
 `ppunkItem`  
 \[in\]接收指向该 `IUnknown` 接口变量的地址与给定的项目。  脚本引擎可以使用 `IUnknown::QueryInterface` 方法获取该项的 `IDispatch` 接口。  如果 `dwReturnMask` 不包括SCRIPTINFO\_IUNKNOWN值，此参数中接收NULL。  此外，;如果没有对象与项目名称，它接受NULL;，当命名项目添加了与 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 方法，设置的SCRIPTITEM\_CODEONLY标志此机制用于创建简单的选件类。  
  
 `ppTypeInfo`  
 \[in\]接收指向该 `ITypeInfo` 接口变量的地址与该项目关联。  此参数中接收NULL，如果 `dwReturnMask` 不包括SCRIPTINFO\_ITYPEINFO值，或者，如果类型信息在此项目中不可用。  如果类型信息不可用，对象不能发出事件，并且，必须注意名称绑定与 `IDispatch::GetIDsOfNames` 方法。  请注意检索的 `ITypeInfo` 接口描述项目的coclass \(TKIND\_COCLASS\)，因为对象都可以支持多个接口和事件接口。  如果项目支持 `IProvideMultipleTypeInfo` 接口，检索的 `ITypeInfo` 接口相同。使用 `IProvideMultipleTypeInfo::GetInfoOfIndex` 方法，将获取的索引零 `ITypeInfo`。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|参数无效。|  
|`E_POINTER`|无效指针指定了。|  
|`TYPE_E_ELEMENTNOTFOUND`|未找到该指定名称的项目。|  
  
## 备注  
 此方法检索 `dwReturnMask` 参数指定的仅信息;这将提高性能。  例如，因此，如果 `ITypeInfo` 接口为项目不是必需的，在 `dwReturnMask`未指定。  
  
## 请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)