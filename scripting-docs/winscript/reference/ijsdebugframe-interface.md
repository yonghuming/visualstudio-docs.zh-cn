---
title: "IJsDebugFrame 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugFrame 接口
表示堆栈帧。  
  
## 语法  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[IJsDebugFrame::Evaluate 方法](../../winscript/reference/ijsdebugframe-evaluate-method.md)|在此堆栈帧的上下文中计算表达式。|  
|[IJsDebugFrame::GetDebugProperty 方法](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|返回该堆栈帧的属性浏览器。|  
|[IJsDebugFrame::GetDocumentPositionWithId 方法](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|在用户级别文档中返回此堆栈框架的当前位置。|  
|[IJsDebugFrame::GetDocumentPositionWithName 方法](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|在用户级别文档中返回此堆栈框架的当前位置。|  
|[IJsDebugFrame::GetName 方法](../../winscript/reference/ijsdebugframe-getname-method.md)|获取堆栈帧的用户友好名称。|  
|[IJsDebugFrame::GetReturnAddress 方法](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|获取推进至框架“开始”（请参阅 GetStackRange）的返回地址。|  
|[IJsDebugFrame::GetStackRange 方法](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|返回逻辑 JavaScript 堆栈帧的绝对地址范围。|  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)