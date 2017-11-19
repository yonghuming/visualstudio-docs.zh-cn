---
redirect_url: shell/distributing-isolated-shell-applications
title: "分发独立的 Shell 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a40d2b8c108d7180ffc68ac2eee6811d49b21c08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="distributing-isolated-shell-applications"></a>分发独立的 Shell 应用程序
要创建独立的 shell 应用程序，你必须安装 Visual Studio 和 Visual Studio SDK。 若要分发到的计算机的其他用户或客户应用程序，必须包括独立 shell 的特殊可再发行组件包。  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>分发独立的 Shell 应用程序的先决条件  
  
|名称|描述|  
|----------|-----------------|  
|Visual Studio SDK|必须具有用于开发和测试的扩展 SDK [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 SDK 还可用于创建您自己的 Visual Studio 独立 shell 的实例。<br /><br /> Visual Studio 是 sdk 的先决条件。|  
|Microsoft Visual Studio 独立 Shell 可再发行组件|可再发行安装程序中时包括生成 Visual studio 工具环境隔离 shell。 独立的 Shell 可再发行组件包包括.NET Framework 4.5。|  
  
## <a name="creating-an-installation-program-for-the-application"></a>为应用程序创建的安装程序  
 为集成或独立 shell 应用程序，必须创建特殊的安装程序。 有关详细信息，请参阅[安装独立 Shell 应用程序](../extensibility/installing-an-isolated-shell-application.md)。  
  
## <a name="allowing-for-updates-to-your-application"></a>允许你的应用程序更新  
 安装程序必须允许，你的应用程序将更新，通过 Microsoft 更新或你公司的更新的可能性。 有关更新的详细信息，请参阅[维护独立 Shell 应用程序的准则](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)。