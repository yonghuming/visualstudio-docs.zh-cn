---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1442297fcacb3a9464f9ea67489c91c8ab64ad78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
此方法共同创建的类中的传递其 ID`rclsid`使用`dwClsContext`。 这是类似的方式[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)工作原理，只不过的情况下`CreateObjectWithSiteAtWebApp`web 应用程序的 UI 线程上以异步方式创建对象。 指定的类 ID 的对象应实现[IWebAppDiagnosticsObjectInitialization 接口](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)。 创建对象后， [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)调用与对 PDM 调试应用程序的引用和`hPassToObject`参数`CreateObjectWithSiteAtWebApp`。 你可以使用此方法将传递到应用程序句柄到已复制使用匿名管道[DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450)。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup 接口](../../winscript/reference/iwebappdiagnosticssetup-interface.md)是实现由 PDM v11.0 和更高版本。 在 activdbg100.h 中发现。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>参数  
 `rclsid`  
 要创建类的类 ID。  
  
 `dwClsContext`  
 将在其中运行代码的上下文。 在大多数情况下很 CLSCTX_INPROC_SERVER。  
  
 `riid`  
 未使用。  
  
 `hPassToObject`  
 一个值，将传递给该对象在 UI 线程上创建后如果对象实现[IWebAppDiagnosticsObjectInitialization 接口](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)。