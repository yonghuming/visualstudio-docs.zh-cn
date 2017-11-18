---
title: "IDiaSession::findAcceleratorInlineesByName |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25aceb146aac7d23647172e53989d30bd9d72a08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
返回与指定的内联函数名称对应的嵌入式框架的符号的枚举。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>参数  
 `name`  
 [in]要搜索的被内联方函数名称。  
  
 `option`  
 [in]名称搜索选项，用于搜索内联帧，对应于`name`。 有关详细信息，请参阅[NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md)。  
  
 `ppResult`  
 [out]指向的指针`IDiaEnumSymbols`结果初始化的接口指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此函数搜索的 inlinees 仅在快捷键存根 （stub） 函数中。 它将忽略本机 c + + 过程记录。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)