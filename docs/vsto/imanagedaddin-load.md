---
title: "IManagedAddin::Load"
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
  - "IManagedAddin::Load"
  - "Load 方法"
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# IManagedAddin::Load
  在加载托管 VSTO 外接程序时调用。  
  
## 语法  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|*bstrManifestURL*|VSTO 外接程序清单的完整路径。|  
|*pdispApplication*|指向代表正在加载 VSTO 外接程序的主机应用程序的 IDispatch 的指针。|  
  
## 返回值  
 HRESULT 值，指示方法是否已成功完成。  
  
## 备注  
 清单是一个文件（通常是 XML 文件），提供用于帮助加载 VSTO 外接程序的信息。 例如，加载 VSTO 外接程序时，清单可以指定 VSTO 外接程序程序集的位置以及要实例化的入口点类。  
  
 *bstrManifestURL* 参数包含 VSTO 外接程序 HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<application name\>*\\Addins\\*\<add\-in ID\>* 注册表项下的 `Manifest` 条目的值。 有关详细信息，请参阅[IManagedAddin 接口](../vsto/imanagedaddin-interface.md)。  
  
 实现 [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) 方法以执行各项任务，例如为正在加载的 VSTO 外接程序配置应用程序域和安全策略。  
  
## 请参阅  
 [IManagedAddin 接口](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  