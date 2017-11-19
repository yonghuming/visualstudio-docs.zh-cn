---
title: "如何： 向 C# 项目中添加应用程序配置文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 097e7a2eac78fe85b2a3ab62d5cdf1fd18908d56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>如何：向 C# 项目添加应用程序配置文件
通过将应用程序配置文件 （app.config 文件） 添加到 C# 项目中，你可以自定义公共语言运行时如何定位和加载程序集文件。 有关应用程序配置文件的详细信息，请参阅[运行时如何定位程序集](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)。  
  
> [!NOTE]
>  UWP 应用不包含 app.config 模板。
  
 生成你的项目时，开发环境中会自动将你的 app.config 文件的复制、 更改以匹配你可执行文件，复制的文件名称并随后将该副本移到 bin 目录。  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>若要将应用程序配置文件添加到你的 C# 项目  
  
1.  在菜单栏上，选择**项目**，**添加新项**。  
  
     “添加新项”对话框随即出现。  
  
2.  展开**已安装**，展开**Visual C# 项**，然后选择**应用程序配置文件**模板。  
  
3.  在**名称**文本框中，输入一个名称，然后选择**添加**按钮。  
  
     名为 app.config 的文件添加到你的项目。  
  
## <a name="see-also"></a>另请参阅  
 [管理应用程序设置 (.NET)](../ide/managing-application-settings-dotnet.md)   
 [配置文件架构](/dotnet/framework/configure-apps/file-schema/index)   
 [配置应用](/dotnet/framework/configure-apps/index)   
 [如何： 配置应用以面向.NET Framework 版本](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [使用 Visual Studio C# 开发环境](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)