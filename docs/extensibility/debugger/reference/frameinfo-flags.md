---
title: "FRAMEINFO_FLAGS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FRAMEINFO_FLAGS
helpviewer_keywords: FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e05d7471df151642f6495907694a0057ef39dfd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
指定要检索的堆栈帧对象有关的信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>成员  
 FIF_FUNCNAME  
 初始化/使用`m_bstrFuncName`字段。  
  
 FIF_RETURNTYPE  
 初始化/使用`m_bstrReturnType`字段。  
  
 FIF_ARGS  
 初始化/使用`m_bstrArgs`字段。  
  
 FIF_LANGUAGE  
 初始化/使用`m_bstrLanguage`字段。  
  
 FIF_MODULE  
 初始化/使用`m_bstrModule`字段。  
  
 FIF_STACKRANGE  
 初始化/使用`m_addrMin`和`m_addrMax`（堆栈范围） 字段。  
  
 FIF_FRAME  
 初始化/使用`m_pFrame`字段。  
  
 FIF_DEBUGINFO  
 初始化/使用`m_fHasDebugInfo`字段。  
  
 FIF_STALECODE  
 初始化/使用`m_fStaleCode`字段。  
  
 FIF_ANNOTATEDFRAME  
 初始化/使用`m_fAnnotatedFrame`字段。  
  
 FIF_DEBUG_MODULEP  
 初始化/使用`m_pModule`字段。  
  
 FIF_FUNCNAME_FORMAT  
 设置格式的函数名称。 在返回结果时`m_bstrFunName`填写字段及其没有其他字段。  
  
 FIF_FUNCNAME_RETURNTYPE  
 将添加到的返回类型`m_bstrFuncName`字段。  
  
 FIF_FUNCNAME_ARGS  
 添加的自变量`m_bstrFuncName`字段。  
  
 FIF_FUNCNAME_LANGUAGE  
 将添加到的语言`m_bstrFuncName`字段。  
  
 FIF_FUNCNAME_MODULE  
 将添加到的模块名称`m_bstrFuncName`字段。  
  
 FIF_FUNCNAME_LINES  
 将添加到的行数`m_bstrFuncName`字段。  
  
 FIF_FUNCNAME_OFFSET  
 将添加到`m_bstrFuncName`字段以字节为单位，从行的开头的偏移量，如果`FIF_FUNCNAME_LINES`指定。 如果`FIF_FUNCNAME_LINES`未指定，或如果行号不可用，从函数的开始将偏移量添加以字节为单位。  
  
 FIF_FUNCNAME_ARGS_TYPES  
 将添加到每个函数自变量的类型`m_bstrFuncName`字段。  
  
 FIF_FUNCNAME_ARGS_NAMES  
 将添加到每个函数自变量的名称`m_bstrFuncName`字段。  
  
 FIF_FUNCNAME_ARGS_VALUES  
 将添加到每个函数自变量的值`m_bstrFuncName`字段。  
  
 FIF_FUNCNAME_ARGS_ALL  
 添加类型、 名称和值的所有自变量`m_bstrFuncName`字段。  
  
 FIF_ARGS_TYPES  
 自变量类型检索，并且格式化。  
  
 FIF_ARGS_NAMES  
 将检索的自变量名称，并将其格式化。  
  
 FIF_ARGS_VALUES  
 自变量值，将检索并设置格式。  
  
 FIF_ARGS_ALL  
 检索并格式化类型、 名称和所有参数的值。  
  
 FIF_ARGS_NOFORMAT  
 指定自变量不会格式 （例如，进行不添加左、 右括号周围自变量列表也不添加自变量之间的分隔符）。  
  
 FIF_ARGS_NO_FUNC_EVAL  
 指定检索参数值时不应使用函数 （属性） 求值。  
  
 FIF_FILTER_NON_USER_CODE  
 调试引擎是进行筛选以便不会包含这些的非用户代码帧。  
  
 FIF_ARGS_NO_TOSTRING  
 不允许`ToString()`函数评估或格式设置时返回函数自变量。  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 应从托管的应用程序域，而不是宿主进程收到帧信息。  
  
## <a name="remarks"></a>备注  
 这些标志传递给[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)和[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)方法以指示哪些字段在中初始化[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)结构。  
  
 这些标志也用于指示哪些字段[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)结构均使用和有效时返回的结构。 这些值可以与按位组合`OR`。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)