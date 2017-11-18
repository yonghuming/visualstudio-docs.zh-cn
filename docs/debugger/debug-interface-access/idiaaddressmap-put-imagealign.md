---
title: "Idiaaddressmap:: Put_imagealign |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38856520641ff2ea191e3f712a1f355e841e1aff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
设置的图像对齐方式。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>参数  
 NewVal  
 [in]新的图像对齐的可执行文件有值。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 指定的内存边界对齐映像 （加载可执行文件）。 由当前的系统体系结构以及编译和链接时间选项，则可能会影响此对齐方式。 图像对齐方式是始终在字节边界上。 下面的图像对齐方式值是有效的： 1、 2、 4、 8、 16、 32 和 64 字节边界。  
  
 可以通过调用检索当前的图像对齐方式[idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)方法。  
  
> [!NOTE]
>  可以调用此方法时已加载映像。 `put_imageAlign`当映像已被移动或更改并且需要新的对齐方式时，通常使用方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)