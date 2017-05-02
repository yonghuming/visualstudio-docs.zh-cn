---
title: "IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentToTop"
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentToTop
将包含窗口指定调试在调试器用户界面的顶级文档。  
  
## 语法  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### 参数  
 `pddt`  
 \[in\] Debug文档对调试器用户界面的顶部显示。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_INVALIDARG`|文档未知。|  
  
## 备注  
 将窗口包含指定的此方法调试在调试器用户界面的顶级文档。  
  
## 请参阅  
 [IApplicationDebuggerUI 接口](../../winscript/reference/iapplicationdebuggerui-interface.md)