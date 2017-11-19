---
title: "WCF 调试的限制 |Microsoft 文档"
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
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72e166d5501849dd84964364a94b2bdf6dc239a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="limitations-on-wcf-debugging"></a>WCF 调试的限制
有三种开始 WCF 服务调试的方式：  
  
-   调试调用服务的客户端进程。 调试器单步执行该服务。 该服务不必与客户端应用程序处于同一个解决方案中。  
  
-   调试请求服务的客户端进程。 该服务必须是解决方案的一部分。  
  
-   你使用**附加到进程**将附加到当前运行的服务。 调试将在该服务内部开始。  
  
 本主题描述了有关这些方案的限制。  
  
## <a name="limitations-on-stepping-into-a-service"></a>单步执行服务的限制  
 若要从正在调试的客户端应用程序单步执行服务，必须满足下列条件：  
  
-   客户端必须使用同步客户端对象调用服务。  
  
-   协定操作不能是单向的。  
  
-   如果服务器是异步的，则无法在服务内部执行代码时查看完整的调用堆栈。  
  
-   必须使用 app.config 或 Web.config 文件中的以下代码启用调试：  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     此代码只需添加一次。 您可以通过编辑.config 文件或通过附加到服务中通过使用添加此代码**附加到进程**。 当你使用**附加到进程**在服务上，调试代码将自动添加到.config 文件。 随后，您可以调试并单步执行该服务，而无需编辑 .config 文件。  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>跳出服务的限制  
 跳出服务并返回到客户端与单步执行服务具有相同的限制（如上所述）。 另外，调试器必须附加到客户端上。 若要调试客户端并单步执行服务，调试器将继续附加到服务中。 这是 true 通过使用启动客户端是否**启动调试**或附加到客户端通过使用**附加到进程**。 如果是通过附加到服务开始调试的，则说明尚未将调试器附加到客户端。 在这种情况下，如果你有到跳出服务并返回到客户端，你必须首先使用**附加到进程**手动附加到客户端。  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>自动附加到服务的限制  
 自动附加到服务具有下列限制：  
  
-   该服务必须是要调试的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案的一部分。  
  
-   该服务必须进行托管。 它可以是网站项目（文件系统和 HTTP）、Web 应用程序项目（文件系统和 HTTP）或 WCF 服务库项目的一部分。 WCF 服务库项目可以是服务库或工作流服务库。  
  
-   必须从 WCF 客户端调用该服务。  
  
-   必须使用 app.config 或 Web.config 文件中的以下代码启用调试：  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>自我托管  
 A*自我托管服务*是不会在 IIS、 WCF 服务主机内运行的 WCF 服务或[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]开发服务器。 有关如何调试自承载的服务的信息，请参阅[如何： 调试自承载的 WCF 服务](../debugger/how-to-debug-a-self-hosted-wcf-service.md)。  
  
## <a name="self-hosting"></a>自我托管  
 若要能够调试[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]3.0 或 3.5 应用程序，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]之前必须安装 3.0 或 3.5[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]安装。 如果[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]之前安装了[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]3.0 或 3.5，尝试进行调试时出现错误[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]3.0 或 3.5 应用程序。 错误消息为：无法自动单步执行服务器。 若要修复此问题，请使用 Windows**控制面板** > **程序和功能**修复你[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]安装。  
  
## <a name="see-also"></a>另请参阅  
 [调试 WCF 服务](../debugger/debugging-wcf-services.md)   
 [如何：调试自托管的 WCF 服务](../debugger/how-to-debug-a-self-hosted-wcf-service.md)