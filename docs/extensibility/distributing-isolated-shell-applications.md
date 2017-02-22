---
title: "分发独立的 Shell 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 分发独立的 Shell 应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要创建独立的 shell 应用程序，必须安装 Visual Studio 和 Visual Studio SDK。 若要分发到的计算机的其他用户或客户的应用程序，必须包括独立 shell 的特殊可再发行组件包。  
  
## 分发独立的 Shell 应用程序的先决条件  
  
|名称|描述|  
|--------|--------|  
|Visual Studio SDK|您必须开发和测试的扩展 SDK [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 您可以使用 SDK 来创建您自己的独立的 Visual Studio shell 的实例。<br /><br /> Visual Studio 是 SDK 的先决条件。|  
|Microsoft Visual Studio 独立 Shell 可再发行组件|可再发行的纳入您的安装程序时生成在 Visual Studio 上的工具环境隔离的 shell。 独立的 Shell 可再发行组件包中包含.NET Framework 4.5。|  
  
## 为应用程序创建安装程序  
 您必须为集成在一起或独立外壳应用程序创建的特殊安装程序。 有关详细信息，请参阅[安装独立的 Shell 应用程序](../extensibility/installing-an-isolated-shell-application.md)。  
  
## 允许您的应用程序更新  
 安装程序必须允许，您的应用程序将被更新，通过 Microsoft 更新或您公司的更新的可能性。 有关更新的详细信息，请参阅 [独立的 Shell 应用程序的服务指南](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)。