---
title: "Office 解决方案中的应用程序和部署清单"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "清单 [Visual Studio 中的 Office 开发]"
  - "部署清单 [Visual Studio 中的 Office 开发]"
  - "应用程序清单 [Visual Studio 中的 Office 开发]"
  - "程序集 [Visual Studio 中的 Office 开发]，更新"
ms.assetid: 4e9abc7c-ef9f-4cb2-a7a9-c95c5f4a1fb7
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Office 解决方案中的应用程序和部署清单
  应用程序清单是一个 XML 文件，该文件提供由 Office 解决方案使用的信息来定位和更新其程序集。 应用程序清单可结合部署清单一起使用，部署清单是一个存储在服务器上的 XML 文件，提供定位最新版本的应用程序清单和程序集所需的信息。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Office 解决方案的清单结构  
 对于通过使用 Visual Studio 中的 Office 开发工具创建的 Microsoft Office 解决方案，所有清单都基于标准的 ClickOnce 架构。 在部署 Office 解决方案时，文档级和 VSTO 外接程序项目的应用程序清单都位于 ClickOnce 缓存。 部署清单不可复制到客户端计算机。  
  
 有关 Office 项目的应用程序内容和部署清单的信息，请参阅 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 和 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)。  
  
## 创建应用程序和部署清单  
 应用程序清单可作为生成过程的一部分自动创建。 每次生成文档级项目时，部署清单的位置就会作为自定义文档属性嵌入到该文档。 对于 VSTO 外接程序，部署清单的位置存储在注册表中。  
  
 有关**发布向导**的详细信息，请参阅 [使用 ClickOnce 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
 有关清单如何与 Office 解决方案配合使用的详细信息，请参阅 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
## 请参阅  
 [文档级自定义项的体系结构](../vsto/architecture-of-document-level-customizations.md)   
 [VSTO 外接程序的体系结构](../vsto/architecture-of-vsto-add-ins.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)  
  
  