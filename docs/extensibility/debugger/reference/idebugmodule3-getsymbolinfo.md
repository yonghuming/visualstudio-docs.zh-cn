---
title: "IDebugModule3::GetSymbolInfo |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 341d31537f3c6c67e601296cf14eb5a6a10df08d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
检索的符号，以及搜索每个路径的结果中搜索的路径的列表。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```csharp  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `dwFields`  
 [in]中的标志的组合[SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)枚举指定的哪些字段`pInfo`要填充的。  
  
 `pInfo`  
 [out]A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)其成员要使用指定的信息填充的结构。 如果这是一个 null 值，此方法返回`E_INVALIDARG`。  
  
## <a name="return-value"></a>返回值  
 如果该方法成功，它将返回`S_OK`; 否则为它将返回错误代码。  
  
> [!NOTE]
>  返回的字符串 (在`MODULE_SYMBOL_SEARCH_INFO`结构) 能为空即使`S_OK`返回。 在这种情况下，没有要返回的搜索信息。  
  
## <a name="remarks"></a>备注  
 如果`bstrVerboseSearchInfo`字段`MODULE_SYMBOL_SEARCH_INFO`结构不为空，则它包含搜索路径和该搜索的结果的列表。 列表设置路径后, 跟省略号 （"..."） 后, 跟结果的格式。 如果有多个路径结果对，然后每个对隔开"\r\n"（回车符-返回/换行） 对。 模式如下所示：  
  
 \<路径 >...\<结果 > \r\n\<路径 >...\<结果 > \r\n\<路径 >...\<结果 >  
  
 请注意，最后一项没有 \r\n 序列。  
  
## <a name="example"></a>示例  
 在此示例中，此方法返回三个路径替换为三个不同的搜索结果。 每个行因回车/换行符对。 示例输出只输出作为单个字符串的搜索结果。  
  
> [!NOTE]
>  状态结果是紧靠"..."最多行的末尾的所有内容。  
  
```cpp  
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)  
{  
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };  
    HRESULT hr;  
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);  
    if (SUCCEEDED(hr)) {  
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;  
        if (searchInfo.Length() != 0) {  
            std::wcout << (wchar_t *)(BSTR)searchInfo;  
            std::wcout << std::endl;  
        }  
    }  
}  
```  
  
 **c:\symbols\user32.pdb...找不到的文件。**  
**c:\winnt\symbols\user32.pdb...版本不匹配。**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb...未加载符号。**   
## <a name="see-also"></a>另请参阅  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)