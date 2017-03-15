---
title: "DEBUG_CUSTOM_VIEWER | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_CUSTOM_VIEWER"
helpviewer_keywords: 
  - "DEBUG_CUSTOM_VIEWER 结构"
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DEBUG_CUSTOM_VIEWER
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

标识一个自定义浏览器类型或可视化工具的结构。  
  
## 语法  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```c#  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## 成员  
 dwID  
 区分多个浏览器或可视化工具的 ID 实现一 `GUID`。  
  
 bstrMenuName  
 将显示在下拉菜单中的文本。  
  
 bstrDescription  
 自定义浏览器类型或可视化工具的说明 \(必须是 null 值，如果未使用\)。  
  
 guidLang  
 提供的表达式计算器的语言。  
  
 guidVendor  
 提供的表达式计算器的供应商联系。  
  
 bstrMetric  
 存储该自定义浏览器类型或可视化工具 `CLSID` 的度量值在下。  
  
## 备注  
 此结构中通过对 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 方法 \(此外，具有扩展名， [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 方法\) 调用返回。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)