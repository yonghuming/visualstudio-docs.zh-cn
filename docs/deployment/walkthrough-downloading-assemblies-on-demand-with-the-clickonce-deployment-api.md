---
title: "演练：使用 ClickOnce 部署 API 按需下载程序集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "程序集, 下载 [ClickOnce]"
  - "ClickOnce 部署, 按需下载"
  - "按需程序集, ClickOnce"
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演练：使用 ClickOnce 部署 API 按需下载程序集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

默认情况下，首次运行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序时，会下载该应用程序中包含的所有程序集。  但是，少数用户可能仅使用应用程序的某些部分。  在这种情况下，您可能希望只有在创建某一类型的程序集时，才下载一个该类型的程序集。  下面的演练演示如何将应用程序中的某些程序集标记为“可选”，以及如何在公共语言运行时 \(CLR\) 需要这些程序集时，通过使用 <xref:System.Deployment.Application> 命名空间中的类来下载这些程序集。  
  
> [!NOTE]
>  要使用此过程，应用程序必须以完全信任的方式运行。  
  
## 系统必备  
 若要完成本演练，您将需要下列组件之一：  
  
-   Windows SDK。  可以从 Microsoft 下载中心下载 Windows SDK。  
  
-   Visual Studio。  
  
## 创建项目  
  
#### 创建使用按需程序集的项目  
  
1.  创建一个名为 ClickOnceOnDemand 的目录。  
  
2.  打开 Windows SDK 命令提示符或 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令提示符。  
  
3.  转到目录 ClickOnceOnDemand。  
  
4.  使用以下命令生成一个公钥\/私钥对：  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  使用记事本或其他文本编辑器，定义一个名为 `DynamicClass`、且仅有一个 `Message` 属性的类。  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-cs[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  将文本另存为名为 `ClickOnceLibrary.cs` 或 `ClickOnceLibrary.vb` 的文件，具体文件名取决于您所使用的语言，并将其保存到 ClickOnceOnDemand 目录。  
  
7.  将该文件编译为一个程序集。  
  
    ```c#  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb#  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  若要获取该程序集的公钥标记，请使用以下命令：  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. 使用文本编辑器创建一个新文件，然后输入下面的代码。  此代码创建一个 Windows 窗体应用程序，在需要 ClickOnceLibrary 程序集时该应用程序会下载它。  
  
     [!code-cs[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. 在代码中，找到对 <xref:System.Reflection.Assembly.LoadFile%2A> 的调用。  
  
11. 将 `PublicKeyToken` 设置为您在前面检索的值。  
  
12. 将该文件另存为 `Form1.cs` 或 `Form1.vb`。  
  
13. 使用以下命令将该文件编译为一个可执行文件。  
  
    ```c#  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb#  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## 将程序集标记为可选  
  
#### 使用 MageUI.exe 在 ClickOnce 应用程序中将程序集标记为可选  
  
1.  按照[演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中的描述，使用 MageUI.exe 创建一个应用程序清单。  请对该应用程序清单使用下列设置：  
  
    -   将该应用程序清单命名为 `ClickOnceOnDemand`。  
  
    -   在**“文件”**页上的 ClickOnceLibrary.dll 行中，将**“文件类型”**列设置为**“无”**。  
  
    -   在**“文件”**页上的 ClickOnceLibrary.dll 行中，在**“组”**列中键入 `ClickOnceLibrary.dll`。  
  
2.  按照[演练：手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中的描述，使用 MageUI.exe 创建一个部署清单。  请对该部署清单使用下列设置：  
  
    -   将该部署清单命名为 `ClickOnceOnDemand`。  
  
## 测试新的程序集  
  
#### 测试按需程序集  
  
1.  将 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署上载到 Web 服务器。  
  
2.  通过在 Web 浏览器中输入部署清单的 URL 来启动使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的应用程序。  如果调用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序 `ClickOnceOnDemand`，并将其上载到 adatum.com 的根目录下，则该 URL 可能如下所示：  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  显示主窗体时，按 <xref:System.Windows.Forms.Button>。  此时，消息框窗口中应该显示“Hello, World\!”这样的字符串。  
  
## 请参阅  
 <xref:System.Deployment.Application.ApplicationDeployment>