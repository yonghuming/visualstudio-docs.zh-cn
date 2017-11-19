---
title: "EncUnavailableReason |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EncUnavailableReason
helpviewer_keywords: EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7fe64a8c8e91535e575677d60b6d30d39fa9abf4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`表示原因，**编辑并继续**不可用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>参数  
 ENCUN_NONE  
 没有特定原因，编辑并继续不可用的原因。  
  
 ENCUN_INTEROP  
 编辑并继续在互操作调用期间不可用。  
  
 ENCUN_SQLCLR  
 编辑并继续在使用公共语言运行时 (CLR) 的 SQL 过程调用期间不可用。  
  
 ENCUN_MINIDUMP  
 编辑并继续处理一个小型转储时不可用。  
  
 ENCUN_EMBEDDED  
 处理嵌入的代码时，编辑并继续不可用。  
  
 ENCUN_ATTACH  
 编辑并继续就不可用因为会话已附加到，不会启动的调试器。  
  
 ENCUN_WIN64  
 编辑并继续处理 64 位 Windows 编码时不可用。  
  
## <a name="remarks"></a>备注  
 此枚举仅适用于内部使用通过[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]。 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)和[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)方法的自定义端口供应商提供的实施方式应始终返回`E_NOTIMPL`。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)