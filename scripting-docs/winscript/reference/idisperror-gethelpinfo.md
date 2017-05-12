---
title: "IDispError::GetHelpInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHelpInfo"
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHelpInfo
如果可能返回帮助文件的路径和解释错误主题的上下文ID，。  
  
## 语法  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### 参数  
 `pbstrFileName`  
 \[in\]请字符串包含帮助文件的完全限定路径。  如果没有帮助文件或错误，则返回值是NULL。  
  
 `pdwContext`  
 \[in\]错误的帮助上下文ID。  如果没有帮助文件\(如果 `pbstrFileName` 为NULL\)，此参数没有意义。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|一个提供程序特定的错误。|  
|`E_INVALIDARG`|`pbstrFileName` 或 `pdwContext` 为NULL。|  
|`E_OUTOFMEMORY`|该提供程序无法分配返回帮助文件路径的足够的内存。|  
  
## 备注  
 如果可能此方法返回帮助文件的路径和解释错误主题的上下文ID，。  
  
> [!NOTE]
>  此方法未实现。  
  
## 请参阅  
 [IDispError 接口](../../winscript/reference/idisperror-interface.md)