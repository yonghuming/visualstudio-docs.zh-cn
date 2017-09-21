---
title: "MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_SYMBOL_SEARCH_INFO"
helpviewer_keywords: 
  - "MODULE_SYMBOL_SEARCH_INFO 结构"
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

包含有关已搜索的符号搜索路径的状态信息。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```c#  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>参数  
 `dwValidFields`  
 中的标志的组合 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 枚举指定此结构中所述的搜索信息的类型。  
  
 `bstrVerboseSearchInfo`  
 搜索路径和串联成一个单一字符串的结果。  
  
## <a name="remarks"></a>备注  
 此结构返回到调用 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) 方法。  
  
 如果 `bstrVerboseSearchInfo` 字段不为空，则它包含搜索路径和该搜索的结果的列表。 列表设置路径后, 跟省略号 （"…"） 后, 跟结果的格式。 如果有多个路径结果对，可通过"\r\n"（回车-/ 换行） 对分隔每一对。 该模式如下所示︰  
  
 \< 路径>...\< 结果>\r\n \< 路径>...\< 结果>\r\n \< 路径>...\< 结果>  
  
 请注意的最后一项不具有一个 \r\n 序列。  
  
 下面是可能发生的 `bstrVerboseSearchInfo` 已发送到标准输出的字符串。  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>要求  
 标头︰ msdbg.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)