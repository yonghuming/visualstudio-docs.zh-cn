---
title: "marker_series::marker_series 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series 构造函数"
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# <a name="markerseriesmarkerseries-constructor"></a>marker_series::marker_series 构造函数
初始化 `marker_series` 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```  
marker_series();  
marker_series(  
   _In_ LPCTSTR _SeriesName  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid,  
   _In_ LPCTSTR _SeriesName  
);  
```  
  
#### <a name="parameters"></a>参数  
 `_SeriesName`  
 要创建的系列的名称。  
  
 `_ProviderGuid`  
 系列提供程序的 GUID。  
  
## <a name="requirements"></a>要求  
 **标头：**cvmarkersobj.h  
  
 **命名空间：**Concurrency::diagnostic  
  
## <a name="see-also"></a>另请参阅  
 [marker_series 类](../profiling/marker-series-class.md)


<!--HONumber=Feb17_HO4-->

