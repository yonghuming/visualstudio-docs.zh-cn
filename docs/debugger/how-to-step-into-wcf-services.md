---
title: "如何： 单步执行 WCF 服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aeaba831bb82731ae7d3e62cbff5190bb474357
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-step-into-wcf-services"></a>如何：单步执行 WCF 服务
在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中，可以单步执行 WCF 服务。 如果 WCF 服务与客户端位于同一 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案中，则可以命中 WCF 服务内部的断点。  
  
 若要使单步执行正常运行，必须在 app.config 或 Web.config 文件中启用调试。 有关如何启用调试和单步执行到 WCF 服务的限制，请参阅[WCF 调试的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
### <a name="to-step-into-a-wcf-service"></a>单步执行 WCF 服务  
  
1.  创建一个同时包含 WCF 客户端和 WCF 服务项目的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案。  
  
2.  在解决方案资源管理器，右键单击 WCF 客户端项目，然后单击**设为启动项目**。  
  
3.  在 app.config 或 web.config 文件中启用调试。 有关详细信息，请参阅[WCF 调试的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
4.  在客户端项目中需要开始单步执行的位置设置断点。 通常情况下，断点设置在 WCF 服务调用之前。  
  
5.  运行到断点，然后开始单步执行。 调试程序将自动在服务中单步执行。  
  
## <a name="see-also"></a>另请参阅  
 [调试 WCF 服务](../debugger/debugging-wcf-services.md)   
 [WCF 调试的限制](../debugger/limitations-on-wcf-debugging.md)   
 [如何：调试自托管的 WCF 服务](../debugger/how-to-debug-a-self-hosted-wcf-service.md)