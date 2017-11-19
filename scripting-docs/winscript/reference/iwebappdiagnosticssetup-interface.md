---
title: "IWebAppDiagnosticsSetup 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e273f29bee6e4d2aae26c01c477373a735624c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup 接口
此接口由 PDM 调试应用程序在正在调试的过程中创建 COM 对象，并启用 web 诊断实现。 如果 PDM 调试应用程序对象实现[IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438)，Internet Explorer 调用[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)上后已创建，并对引用传入[IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). WWA 应用程序调用[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) WWA 传入界面 IWebApplicationHost 改为和。 如果[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)已使用非 NULL 值，调用[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) ，则返回 true。 如果不是，它返回 false，且调用[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)失败。  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup`实现由 PDM v11.0 和更高。 在 activdbg100.h 中发现。  
  
## <a name="methods"></a>方法  
 此接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|获取由指定的筛选器隐藏的文本文档。|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|确定此节点的子节点之一是否属于指定的文档。|