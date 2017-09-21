---
title: "IDebugExpressionEvaluator2::Terminate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "终止"
  - "IDebugExpressionEvaluator2::Terminate"
ms.assetid: 38265100-4d80-4902-833a-07bb569f9ba8
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionEvaluator2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

停止并清理表达式计算器。  
  
## 语法  
  
```cpp#  
HRESULT Terminate (  
    void  
);  
```  
  
```c#  
int Terminate ();  
```  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 ，在清理时，调用表达式计算器。  
  
## 示例  
 下面的示例演示如何执行显示 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) 接口的 **ExpressionEvaluatorPackage** 对象的方法。  
  
```cpp#  
STDMETHODIMP ExpressionEvaluatorPackage::Terminate(void)  
{  
    // scan the namespaces contained and delete  
    EEExtensionMethodCache **ppChild = NULL;  
    m_HashExtensionMethodCache.ResetHashIterator();  
    while (ppChild = m_HashExtensionMethodCache.IterateHash())  
    {  
        delete *ppChild;  
    }  
    return VBEEImplicitVariables::Terminate();  
}  
```  
  
## 请参阅  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)