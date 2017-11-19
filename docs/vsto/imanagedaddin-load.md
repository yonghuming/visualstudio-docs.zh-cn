---
title: "IManagedAddin::Load |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 62c1af72158c0b416942e9124003dbeb06b584ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  在加载托管 VSTO 外接程序时调用。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|*bstrManifestURL*|VSTO 外接程序清单的完整路径。|  
|*pdispApplication*|指向代表正在加载 VSTO 外接程序的主机应用 IDispatch 的指针。|  
  
## <a name="return-value"></a>返回值  
 HRESULT 值，指示方法是否已成功完成。  
  
## <a name="remarks"></a>备注  
 清单是一个文件（通常是 XML 文件），提供用于帮助加载 VSTO 外接程序的信息。 例如，加载 VSTO 外接程序时，清单可以指定 VSTO 外接程序程序集的位置以及要实例化的入口点类。  
  
 *BstrManifestURL*参数包含的值`Manifest`下 HKEY_CURRENT_USER\Software\Microsoft\Office 条目\\*\<应用程序名称 >*\Addins\\*\<外接程序 ID >* VSTO 外接程序的注册表项。 有关详细信息，请参阅 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)。  
  
 实现 [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) 方法以执行各项任务，例如为正在加载的 VSTO 外接程序配置应用程序域和安全策略。  
  
## <a name="see-also"></a>另请参阅  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  