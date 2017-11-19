---
title: "部署 64 位应用程序的先决条件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: aefb619487fba984e8f625dfe414c2f514f28c70
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>部署 64 位应用程序的必备组件
ClickOnce 部署支持 64 位平台上的应用程序安装。 目标平台是**x86**对于 32 位平台， **x64**机支持 AMD64 和 EM64T 指令集和**Itanium**在 64 位 Itanium 处理器。  
  
## <a name="prerequisites"></a>先决条件  
 下表列出了可用作 64 位应用程序安装的系统必备组件的可再发行组件。  
  
 如果选择不具有 64 位组件的系统必备组件，则可能会看到一条警告，该警告声明选择的程序包不能用于 64 位平台。  
  
|可再发行组件|x64 支持|IA64 支持|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|是|否|  
|Visual C++ 2010 运行库 (IA64)|否|是|  
|Visual C++ 2010 运行库 (x64)|是|否|  
|Microsoft .NET Framework 4（x86 和 x64）|是||  
|Microsoft .NET Framework 4 Client Profil（x86 和 x64）|是||  
  
## <a name="see-also"></a>另请参阅  
 [部署应用程序、 服务和组件](../deployment/deploying-applications-services-and-components.md)   
 [如何： 与 ClickOnce 应用程序一起安装系统必备组件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64 位应用程序](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)