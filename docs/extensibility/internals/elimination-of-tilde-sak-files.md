---
title: "消除了 ~ SAK 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e487acefcb06c4fa0cd2070bfcf20bd065d500ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="elimination-of-sak-files"></a>消除了 ~ SAK 文件
在源控件插件 API 1.2，~ 功能标志和检测源代码管理插件支持 MSSCCPRJ 文件和共享签出的新函数已替换为 SAK 文件。  
  
## <a name="sak-files"></a>~ SAK 文件  
 Visual Studio.NET 2003 中创建带有前缀的临时文件 ~ SAK。 这些文件用于确定了源代码管理插件是否支持：  
  
-   MSSCCPRJ。SCC 文件。  
  
-   多个 （共享） 的方式签出。  
  
 即插即用的项的源控件插件 API 1.2 中支持提供的高级的功能，IDE 可以检测这些功能，而无需创建的临时文件，通过使用新功能、 标志和函数，将在以下各节详细说明。  
  
## <a name="new-capability-flags"></a>新功能标志  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>新的函数  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 如果源代码管理插件支持多个 （共享） 签出，则它声明`SCC_CAP_MULTICHECKOUT`功能和实现`SccIsMultiCheckOutEnabled`函数。 在任何受源代码管理项目发生签出操作时，调用此函数。  
  
 如果源代码管理插件支持创建和使用 MSSCCPRJ。SCC 文件，则该声明`SCC_CAP_SCCFILE`功能和实现[SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)。 使用文件的列表，调用此函数。 该函数将返回`TRUE/FALSE`为每个文件，以指示 Visual Studio 是否应使用 MSSCCPRJ。它 SCC 文件。 如果源代码管理插件选择不支持这些新功能和函数，它可以使用以下注册表项以禁用在创建这些文件：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateTemporaryFilesInSourceControl"= dword: 00000001  
  
> [!NOTE]
>  如果此注册表项设置为 00000000 时表示，它相当于的键不存在，，和 Visual Studio 仍尝试创建临时文件。 但是，如果注册表项设置为 dword: 00000001，Visual Studio 不会不尝试创建临时文件。 相反，它假设源代码管理插件不支持 MSSCCPRJ。SCC 文件和不支持共享签出。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)