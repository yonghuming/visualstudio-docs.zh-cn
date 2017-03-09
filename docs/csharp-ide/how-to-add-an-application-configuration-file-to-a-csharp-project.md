---
title: "如何：向 C# 项目添加应用程序配置文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "app.config 文件, 添加到 C# 项目"
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：向 C# 项目添加应用程序配置文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过将应用程序配置文件 \(app.config 文件\) 添加到 C\# 项目中，可以自定义公共语言运行时如何定位并加载程序集文件。  有关应用程序配置文件的更多信息，请参见[运行时如何定位程序集](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md)。  
  
> [!NOTE]
>  windows 中不支持 <xref:System.Configuration>。  因此，存储 apps 不包含一个 app.config 模板。  
  
 当生成项目时，开发环境会自动复制您的 app.config 文件中，将该副本的文件名与可执行文件，然后将复制到 bin 目录中。  
  
### 向 C\# 项目添加应用程序配置文件  
  
1.  在菜单栏上，选择 **项目**，**添加新项**。  
  
     此时将显示**“添加新项”**对话框。  
  
2.  外接 **已安装**，展开 **Visual C\# 项**，然后选择 **应用程序配置文件** 模板。  
  
3.  在 **名称** 文本框中，输入名称，然后选择 **添加** 按钮。  
  
     名为 app.config 的文件添加到项目中。  
  
## 请参阅  
 [管理应用程序设置 \(.NET\)](../ide/managing-application-settings-dotnet.md)   
 [配置文件架构](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [配置应用](../Topic/Configuring%20Apps%20by%20using%20Configuration%20Files.md)   
 [How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/zh-cn/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [使用 Visual C\# 开发环境](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)