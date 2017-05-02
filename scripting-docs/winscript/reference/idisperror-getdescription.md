---
title: "IDispError::GetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetDescription
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetDescription"
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetDescription
返回错误的文本说明。  
  
## 语法  
  
```  
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### 参数  
 `pbstrDescription`  
 \[in\]请字符串包含错误的简短说明。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 该文本在传递到方法的 `IDispatchEx::InvokeEx` 遇到此错误的区域设置标识符指定的语言返回\(LCID\)。  
  
> [!NOTE]
>  此方法未实现。  
  
## 请参阅  
 [IDispError 接口](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)