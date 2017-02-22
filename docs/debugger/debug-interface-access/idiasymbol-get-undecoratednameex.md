---
title: "IDiaSymbol::get_undecoratedNameEx | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_undecoratedNameEx 方法"
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索部分或全部一个未修饰名对于 c. C\+\+ 修饰的连接 \(\) 名称。  
  
## 语法  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### 参数  
 `undecoratedOptions`  
 \[in\] 指定控件标记的组合了返回。  为特定值请参见 " 备注 " 部分，以及它们。  
  
 `pRetVal`  
 \[out\] 返回未修饰名对于 c. C\+\+ 修饰名。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 备注  
 `undecorateOptions` 可以是以下标志的组合。  
  
> [!NOTE]
>  标志名称。 DIA SDK 未定义，因此，您需要添加声明添加到代码或使用原始值。  
  
|Flag|值|说明|  
|----------|-------|--------|  
|UNDNAME\_COMPLETE|0x0000|启用完整的 undecoration。|  
|UNDNAME\_NO\_LEADING\_UNDERSCORES|0x0001|从 Microsoft 扩展的关键字移除前导下划线。|  
|UNDNAME\_NO\_MS\_KEYWORDS|0x0002|禁用 Microsoft 扩展的关键字展开。|  
|UNDNAME\_NO\_FUNCTION\_RETURNS|0x0004|禁用该外接返回主要声明中的类型。|  
|UNDNAME\_NO\_ALLOCATION\_MODEL|0x0008|禁用描述模型的扩展。|  
|UNDNAME\_NO\_ALLOCATION\_LANGUAGE|0x0010|禁用声明语言说明符的扩展。|  
|UNDNAME\_RESERVED1|0x0020|保留。|  
|UNDNAME\_RESERVED2|0x0040|保留。|  
|UNDNAME\_NO\_THISTYPE|0x0060|禁用了 `this` 类型的所有修饰符。|  
|UNDNAME\_NO\_ACCESS\_SPECIFIERS|0x0080|禁用访问说明符展开成员。|  
|UNDNAME\_NO\_THROW\_SIGNATURES|0x0100|禁用引发 “签名”扩展功能和指针的函数。|  
|UNDNAME\_NO\_MEMBER\_TYPE|0x0200|禁用 `static` 或 `virtual` 成员展开。|  
|UNDNAME\_NO\_RETURN\_UDT\_MODEL|0x0400|禁用 Microsoft 模型的扩展 UDT 的返回值。|  
|UNDNAME\_32\_BIT\_DECODE|0x0800|Undecorates 32 位修饰名。|  
|UNDNAME\_NAME\_ONLY|0x1000|获取仅名称主要声明;返回范围: \[\]:名称。  展开模板参数。|  
|UNDNAME\_TYPE\_ONLY|0x2000|输入是类型编码;由一个抽象声明。|  
|UNDNAME\_HAVE\_PARAMETERS|0x4000|实际模板参数可用。|  
|UNDNAME\_NO\_ECSU|0x8000|禁止显示枚举\/类\/结构\/联合。|  
|UNDNAME\_NO\_IDENT\_CHAR\_CHECK|0x10000|禁止显示有效的标识符字符的检查。|  
|UNDNAME\_NO\_PTR64|0x20000|在输出不包括 ptr64。|  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)