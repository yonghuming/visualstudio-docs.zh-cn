---
title: "IDebugModule3::GetSymbolInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::GetSymbolInfo"
helpviewer_keywords: 
  - "GetSymbolInfo 方法"
  - "IDebugModule3::GetSymbolInfo 方法"
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索路径中搜索符号，以及搜索每个路径的结果的列表。  
  
## 语法  
  
```cpp#  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```c#  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### 参数  
 `dwFields`  
 \[\] in中的标志组合 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 枚举指定的哪些字段 `pInfo` 是必填。  
  
 `pInfo`  
 \[\] out一个 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) 结构的成员是要使用指定的信息来填充。 如果这是一个 null 值，此方法返回 `E_INVALIDARG`。  
  
## 返回值  
 如果该方法成功，它将返回 `S_OK`; 否则为它将返回错误代码。  
  
> [!NOTE]
>  返回的字符串 \(在 `MODULE_SYMBOL_SEARCH_INFO` 结构\) 能为空即使 `S_OK` 返回。 在这种情况下，没有要返回的搜索信息。  
  
## 备注  
 如果 `bstrVerboseSearchInfo` 字段 `MODULE_SYMBOL_SEARCH_INFO` 结构不为空，则它包含搜索路径和搜索操作的结果的列表。 列表设置路径后, 跟省略号 （"…"） 后, 跟结果的格式。 如果有多个路径结果对，可通过"\\r\\n"（回车\-\/ 换行） 对分隔每一对。 该模式如下所示︰  
  
 \< 路径 \>...\< 结果 \> \\r\\n \< 路径 \>...\< 结果 \> \\r\\n \< 路径 \>...\< 结果 \>  
  
 请注意的最后一项不具有一个 \\r\\n 序列。  
  
## 示例  
 在此示例中，此方法返回三个路径替换为三个不同的搜索结果。 每个行终止，回车\/换行符对。 示例输出只输出作为单个字符串的搜索结果。  
  
> [!NOTE]
>  状态结果是行的紧随"..."最多末尾的所有内容。  
  
```cpp#  
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
  
 **c:\\symbols\\user32.pdb...找不到文件。 c:\\winnt\\symbols\\user32.pdb...版本不匹配。 \\\\symbols\\symbols\\user32.dll\\0a8sd0ad8ad\\user32.pdb...未加载符号。**   
## 请参阅  
 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)