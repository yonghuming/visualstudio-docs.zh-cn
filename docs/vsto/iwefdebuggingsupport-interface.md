---
title: "IWefDebuggingSupport 接口"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# IWefDebuggingSupport 接口
  实现由调试环境\(例如，Visual Studio，以便于调试Office的apps。  在调试会话期间，Office应用程序，例如Word或Excel中，从Visual Studio中对此接口然后调用接口中的方法在确定一个点。  
  
## 语法  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## 方法  
 下表列出了 IWefDebuggingSupport 接口定义的方法。  
  
|名称|说明|  
|--------|--------|  
|[GetAutoInsertExtensions 方法](../vsto/getautoinsertextensions-method.md)|获取有关在调试期间，将自动插入的apps的信息Office的。|  
|[SetWefProcessId 方法](../vsto/setwefprocessid-method.md)|提供将运行Web扩展框架\(WEF\)内容的进程标识符。|  
  
  