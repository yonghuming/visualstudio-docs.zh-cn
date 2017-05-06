---
title: "IManagedAddin::Unload"
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
helpviewer_keywords: 
  - "Unload 方法"
  - "IManagedAddin::Unload"
ms.assetid: 40a73f07-2605-4745-8ac5-0a0189167fd7
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# IManagedAddin::Unload
  只在托管 VSTO 外接程序卸载之前调用。  
  
## 语法  
  
```  
HRESULT Unload();  
```  
  
## 返回值  
 HRESULT 值，指示方法是否已成功完成。  
  
## 备注  
 当前版本的 Microsoft Office 不调用此方法。 此方法保留供将来使用。  
  
## 请参阅  
 [IManagedAddin 接口](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  