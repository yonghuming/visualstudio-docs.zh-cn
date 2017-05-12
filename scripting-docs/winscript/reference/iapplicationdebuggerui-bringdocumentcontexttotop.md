---
title: "IApplicationDebuggerUI::BringDocumentContextToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentContextToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentContextToTop"
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentContextToTop
将包含窗口提供在调试器用户界面和滚动的顶级文档上下文窗口到上下文。  
  
## 语法  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### 参数  
 `pddc`  
 \[in\]文档上下文对调试器用户界面的顶部显示。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|`pddc` 指定的上下文未知。|  
  
## 备注  
 此方法将包含窗口提供在调试器用户界面和滚动的顶级文档上下文窗口到上下文。  
  
## 请参阅  
 [IApplicationDebuggerUI 接口](../../winscript/reference/iapplicationdebuggerui-interface.md)