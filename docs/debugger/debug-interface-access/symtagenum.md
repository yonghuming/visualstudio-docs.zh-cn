---
title: "SymTagEnum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SymTagEnum 枚举"
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# SymTagEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定符号的类型。  
  
## 语法  
  
```cpp#  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## Elements  
 `SymTagNull`  
 该符号不表示任何类型。  
  
 `SymTagExe`  
 指示的符号是.exe 文件。  只有一个`SymTagExe`符号存储区的每个符号。  它可作为全局作用域并没有词法父级。  
  
 `SymTagCompiland`  
 表示符号存储区的每个编译文件中组件的编译符号。  对于本机应用程序， `SymTagCompiland`符号对应于对象文件链接到图像。  对于某些类型的 Microsoft 中间语言 \(MSIL\) 图像中，没有一个编译文件中的每个类。  
  
 `SymTagCompilandDetails`  
 指示该元件包含编译的文件的扩展的属性。  检索这些属性，则可能需要加载符号编译文件中。  
  
 `SymTagCompilandEnv`  
 表示符号为编译文件中定义的环境字符串。  
  
 `SymTagFunction`  
 指示的符号是一个函数。  
  
 `SymTagBlock`  
 指示的符号是嵌套的块。  
  
 `SymTagData`  
 指示的符号是数据。  
  
 `SymTagAnnotation`  
 表示符号为代码注释。  此符号的子代是连续的数据字符串 （`SymTagData`， `LocIsConstant`， `DataIsConstant`\)。  大多数客户端忽略此符号。  
  
 `SymTagLabel`  
 指示的符号是一个标签。  
  
 `SymTagPublicSymbol`  
 指示的符号是公共符号。  对于本机应用程序，该符号是链接图像时遇到的 COFF 外部符号。  
  
 `SymTagUDT`  
 指示的符号是用户定义类型 （结构、 类或联合）。  
  
 `SymTagEnum`  
 表示符号枚举。  
  
 `SymTagFunctionType`  
 指示的符号是一种函数签名类型。  
  
 `SymTagPointerType`  
 表示符号为指针类型。  
  
 `SymTagArrayType`  
 指示的符号是数组类型。  
  
 `SymTagBaseType`  
 指示的符号是基类型。  
  
 `SymTagTypedef`  
 指示的符号是`typedef`，即为另一种类型的别名。  
  
 `SymTagBaseClass`  
 指示的符号是用户定义类型的基类。  
  
 `SymTagFriend`  
 指示的符号是用户定义的类型的友元。  
  
 `SymTagFunctionArgType`  
 指示的符号是函数的参数。  
  
 `SymTagFuncDebugStart`  
 指示的符号是该函数的序言代码的结束位置。  
  
 `SymTagFuncDebugEnd`  
 指示的符号是该函数的跋代码的开始位置。  
  
 `SymTagUsingNamespace`  
 指示的符号是命名空间名称，在当前范围内的活动。  
  
 `SymTagVTableShape`  
 指示的符号是虚拟表的说明。  
  
 `SymTagVTable`  
 指示的符号是虚拟表的指针。  
  
 `SymTagCustom`  
 表示符号是自定义的符号，并不由 DIA.解释  
  
 `SymTagThunk`  
 指示的符号是一个 thunk，用于 16 和 32 位代码之间共享数据。  
  
 `SymTagCustomType`  
 指示的符号是一个自定义编译器符号。  
  
 `SymTagManagedType`  
 指示的符号是在元数据中。  
  
 `SymTagDimension`  
 指示的符号是 FORTRAN 多维数组。  
  
 `SymTagCallSite`  
 指示该符号表示调用站点。  
  
 `SymTagInlineSite`  
 指示该符号表示的内联网站。  
  
 `SymTagBaseInterface`  
 指示的符号是基接口。  
  
 `SymTagVectorType`  
 指示的符号是向量类型。  
  
 `SymTagMatrixType`  
 指示的符号是矩阵类型。  
  
 `SymTagHLSLType`  
 指示的符号是高级别着色器的语言类型。  
  
## 备注  
 调试文件中的所有符号都具有标识标记，指定元件的类型。  
  
 返回此枚举中的值通过调用[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)方法。  
  
 此枚举中的值传递到下列方法来限制到特定的元件类型的搜索范围：  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## 要求  
 标题： cvconst.h  
  
## 请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)