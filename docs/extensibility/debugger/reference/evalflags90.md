---
title: "EVALFLAGS90 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EVALFLAGS90 枚举"
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# EVALFLAGS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

枚举控制表达式计算的标志的有效值。  此枚举扩展 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 枚举。  
  
## 语法  
  
```cpp#  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```c#  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### 参数  
 EVAL90\_RETURNVALUE  
 指定返回值，如果有，则计算。  
  
 EVAL90\_NOSIDEEFFECTS  
 指定副作用不允许。  
  
 EVAL90\_ALLOWBPS  
 停止的标识在断点。  
  
 EVAL90\_ALLOWERRORREPORT  
 指定错误报告给将允许的。  主要用于表达式计算在脚本在 Internet Explorer。  
  
 EVAL90\_FUNCTION\_AS\_ADDRESS  
 军队的优点函数会计算为地址，而不是调用该函数。  
  
 EVAL90\_NOFUNCEVAL  
 防止函数进行求值。  例如，请考虑在表达式 `myExpression(int) + 10`的 `int` 标记。  此功能能被正确计算为地址，但是，不是值。  
  
 EVAL90\_NOEVENTS  
 指示标志。表达式计算期间发生的事件不应发送到该会话调试管理器 \(SDM\)或对 IDE。  
  
 EVAL90\_DESIGN\_TIME\_EXPR\_EVAL  
 支持设计时表达式计算。  
  
 EVAL90\_ALLOW\_IMPLICIT\_VARS  
 允许隐式变量的创建。  
  
 EVAL90\_FORCE\_EVALUATION\_NOW  
 强制计算立即发生。  ，以作为一个请求，如用户请求时，这会很有用。  
  
## 要求  
 标题:Msdbg90.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)