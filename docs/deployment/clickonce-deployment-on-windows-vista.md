---
title: "在 Windows Vista 上的 ClickOnce 部署 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 22a50c85db54ed58b675253bb071c4aab47fe197
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista 上的 ClickOnce 部署
在 Windows Vista 上的用户帐户控制 (UAC) 通常会生成嵌入的清单，Visual Studio 中生成应用程序编码为二进制的 XML 数据，应用程序的可执行文件中。 ClickOnce 和免注册 COM 应用程序需要外部清单，因为 Visual Studio 将生成这些类型的项目包含 UAC 数据而不是嵌入的清单的文件。 默认情况下，Visual Studio 使用信息从调用应用程序清单文件来生成外部 UAC 清单信息 （对于 ClickOnce 和免注册 COM 部署），或将其嵌入在应用程序的可执行文件 （对于所有其他情况下）。 Visual Studio 针对清单生成提供以下选项：  
  
-   使用嵌入的清单。 在应用程序的可执行文件中嵌入 UAC 数据并作为正常用户运行。  
  
     （除非你使用 ClickOnce），这是默认设置。 此设置将在 Windows Vista; 上支持 Visual Studio 进行操作的常用方式也就是说，生成的内部和外部的清单，这两个使用`AsInvoker`。  
  
-   使用外部清单。 通过使用应用程序清单中生成外部清单。  
  
     这可以通过使用应用程序清单中的信息生成仅外部清单。 通过使用 ClickOnce 或免注册 COM 发布应用程序时，Visual Studio 向项目中添加应用程序清单，并增加了此选项。  
  
-   不使用清单。 创建不带清单应用程序。  
  
     这种方法是也称为*虚拟化*。 为了兼容现有应用程序从 Visual Studio 的早期版本中使用此选项。  
  
 新的属性都位于**应用程序**项目设计器 （对于 Visual C# 项目） 的页和 MSBuild 项目文件格式。  
  
 请注意，在 Visual Studio IDE 中配置 UAC 清单生成的方法取决于项目类型 （Visual C# 和 Visual Basic）。  
  
 有关配置清单生成的 Visual C# 项目的信息，请参阅[应用程序页，项目设计器 (C#)](../ide/reference/application-page-project-designer-csharp.md)。  
  
 有关配置清单生成 Visual Basic 项目的信息，请参阅[应用程序页，项目设计器 (Visual Basic 中)](../ide/reference/application-page-project-designer-visual-basic.md)。  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)   
 [用户权限与 Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [应用程序页、项目设计器 (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [“项目设计器”->“应用程序”页 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)