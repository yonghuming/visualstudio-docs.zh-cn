---
title: "IDebugHelper::CreatePropertyBrowser | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowser
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowser"
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowser
返回包装个变体的属性浏览器。  
  
## 语法  
  
```  
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### 参数  
 `pvar`  
 \[in\]浏览的根变量。  
  
 `bstrName`  
 \[in\]提供根的名称。  
  
 `pdat`  
 \[in\]请线程在哪些请求属性。  如果此参数是NULL，排列不执行。  
  
 `ppdob`  
 \[in\]属性浏览器。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回包装个变体的属性浏览器。  
  
## 请参阅  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper 接口](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)