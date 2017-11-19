---
title: "Idiasymbol:: Get_undecoratednameex |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dac35a0e01890488e6290759b563d25f7067067
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
检索部分或全部 c + + 的未修饰名称修饰 （链接） 名称。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>参数  
 `undecoratedOptions`  
 [in]返回该控件指定的标志的组合。 请参阅备注部分的特定值和它们执行的操作。  
  
 `pRetVal`  
 [out]返回 c + + 的未修饰的名称修饰名。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回`S_FALSE`或错误代码。  
  
> [!NOTE]
>  返回值`S_FALSE`意味着属性不是可用于符号。  
  
## <a name="remarks"></a>备注  
 `undecorateOptions`可以是以下标志的组合。  
  
> [!NOTE]
>  在 DIA SDK 中，未定义的标志名称，因此你需要将声明添加到你的代码，或者使用的原始值。  
  
|Flag|值|描述|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|启用完全 undecoration。|  
|UNDNAME_NO_LEADING_UNDERSCORES|从 0x0001|从 Microsoft 扩展关键字前导下划线的删除。|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|禁用扩展的 Microsoft 扩展关键字。|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|禁用扩展的主声明返回类型。|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|禁用的声明模型的扩展。|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|禁用的声明语言说明符的扩展。|  
|UNDNAME_RESERVED1|0x0020|保留。|  
|UNDNAME_RESERVED2|0x0040|保留。|  
|UNDNAME_NO_THISTYPE|0x0060|在中禁用所有修饰符`this`类型。|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|禁用扩展的成员的访问说明符。|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|禁用扩展"抛出的签名"的函数、 指向函数的指针。|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|禁用的扩展`static`或`virtual`成员。|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|UDT 返回禁用 Microsoft 模型的扩展。|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates 32 位修饰的名称。|  
|UNDNAME_NAME_ONLY|0x1000|获取仅主声明; 的名称只需返回 [作用域::] 名称。  展开模板参数。|  
|UNDNAME_TYPE_ONLY|0x2000|输入，则只需编码; 的类型组合了抽象声明符。|  
|UNDNAME_HAVE_PARAMETERS|0x4000|可以使用实际模板参数。|  
|UNDNAME_NO_ECSU|0x8000|取消枚举/类/结构/联合。|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|禁止检查有效的标识符字符。|  
|UNDNAME_NO_PTR64|0x20000|不在输出中包括 ptr64。|  
  
## <a name="see-also"></a>另请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)