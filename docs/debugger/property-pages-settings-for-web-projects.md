---
title: "Web 项目的属性页设置 |Microsoft 文档"
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
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c86e45ea5108361271658d5dd8e7dfadbde2012
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="property-pages-settings-for-web-projects"></a>Web 项目的属性页设置
你可以更改网站调试配置中的属性设置**属性页**对话框中中, 所述[调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)。 下表显示在何处可以找到中与调试器相关的设置**属性页**对话框。  
  
### <a name="configuration-properties-folder-start-options-category"></a>“配置属性”文件夹（“启动选项”类别）  
  
|**设置**|**描述**|  
|-----------------|---------------------|  
|**启动操作**|将与应用程序启动相关的选项归为一组的标题。|  
|**使用当前页**|将当前页指定为调试起点。|  
|**特定页：**|指定希望开始调试的网页。|  
|**启动外部程序：**|指定用于启动要调试的程序的命令。|  
|**命令行参数：**|为上面指定的命令指定自变量。|  
|**工作目录：**|指定被调试的程序的工作目录。 在 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 中，工作目录是启动应用程序的目录，默认情况下为 \bin\debug。|  
|**启动 URL**|指定要调试的 Web 应用程序的位置。|  
|**不打开页面。等待来自外部应用程序的请求**|表示等待来自外部应用程序的请求。 该选项不会启动 Internet Explorer 或另一个应用程序， 而只是为应用程序调用调试做好准备。|  
|**服务器**|将与要使用的服务器相关的选项归为一组的标题。|  
|**使用默认 Web 服务器**|表示使用默认的 Web 服务器。|  
|**使用自定义服务器**|允许您输入要用作服务器的基 URL。|  
|**调试器**|将与要进行的调试类型相关的选项归为一组的标题。|  
|**ASP.NET 调试**|启用为 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 开发平台编写的服务器页的调试。 你必须指定在 URL**启动 URL**。|  
|**本机代码调试**|使你能够从托管应用程序中调试对本机（非托管）Win32 代码的调用。|  
|**SQL Server 调试**|允许对 SQL Server 数据库对象进行调试。|  
|**Silverlight 调试**|允许调试 Silverlight 组件。|  
  
## <a name="see-also"></a>另请参阅  
 [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)