---
title: "SccIsMultiCheckoutEnabled 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 13
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
ms.openlocfilehash: a8c1a00aa923374b7833e83edde4a0d7b5b4b9b6
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 函数
此函数检查源代码管理插件是否允许多次签出文件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>参数  
 pContext  
 [in]源控件插件上下文结构。  
  
 pbMultiCheckout  
 [out]指定是否为此项目 （非零方法，支持多个签出） 启用多重签出。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|检查成功。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|非特定的失败。|  
  
## <a name="remarks"></a>备注  
 IDE 将使两个检查以确定是否文件可以签同时由多个用户。 首先，源控制系统必须支持多重签出。 源代码管理插件可以指定此功能在初始化期间通过指定`SCC_CAP_MULTICHECKOUT`。 此后，作为第二个检查，IDE 调用此函数可确定当前的项目支持多重签出。 如果所选项目支持多重签出，则插件将返回成功代码，并将设置`pbMultiCheckout`不为零 (`TRUE`) 或`FALSE`。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)
