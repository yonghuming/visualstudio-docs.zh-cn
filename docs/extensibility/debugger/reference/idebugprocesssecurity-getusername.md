---
title: "IDebugProcessSecurity::GetUserName |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 081f073ba59021ca56dd084bd2cef0fde6c5c32e
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
从端口供应商处获取的用户名。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pbstrUserName`  
 [out]包含的用户名称的字符串。  
  
## <a name="return-value"></a>返回值  
 如果该方法成功，它将返回`S_OK`。 否则它将返回错误代码。  
  
## <a name="remarks"></a>备注  
 `GetUserName`返回在显示的用户名称**用户名**列**附加到进程**对话框。 若要查看**附加到进程**对话框中，单击**附加到进程**上**工具**菜单中的[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
