---
title: "IVariantChangeType::ChangeType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IVariantChangeType::ChangeType"
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IVariantChangeType::ChangeType
采用不同的值并用指定的类型创建新的变量。  
  
## 语法  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### 参数  
 `pvarDst`  
 \[in，out\]包含值的变量表示 `pvarSrc`，但是，在 `vtNew`指定的类型。  
  
 `pvarSrc`  
 \[in\]更改的不同的值为新类型。  
  
 `lcid`  
 \[in\]使用的区域设置上下文，当参数强制转换成\/从字符串。  
  
 `vtNew`  
 \[in\]指定类型为 `pvarDst` 可以变为。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 在原始值复盖情况下，`pvarDst` 和 `pvarSrc` 参数可以是相等。  此方法通过 `pvarDst` 到 `VariantClear` 功能，因此，应该初始化 `pvarDst` 到一个有效值。  
  
## 请参阅  
 [IVariantChangeType 接口](../../winscript/reference/ivariantchangetype-interface.md)