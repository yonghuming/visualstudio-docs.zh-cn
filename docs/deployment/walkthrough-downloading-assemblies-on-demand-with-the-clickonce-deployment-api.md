---
title: "演练： 下载使用 ClickOnce 部署 API 按需程序集 |Microsoft 文档"
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
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f84d1cfa2208dc8a8b9d279a46ecf52676c0ae62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>演练：使用 ClickOnce 部署 API 按需下载程序集
默认情况下，所有程序集包括在[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]首次运行应用程序时，会下载应用程序。 但是，您可能必须使用你的用户的一小部分的应用程序的部分。 在这种情况下，你希望仅当创建其类型之一时才下载程序集。 下面的演练演示如何将标记为"可选"应用程序中的某些程序集和如何通过使用下载中的类<xref:System.Deployment.Application>当公共语言运行时 (CLR) 要求它们时的命名空间。  
  
> [!NOTE]
>  应用程序必须在完全信任下运行才能使用此过程。  
  
## <a name="prerequisites"></a>先决条件  
 你将需要以下组件来完成本演练之一：  
  
-   Windows SDK 中。 可以从 Microsoft 下载中心下载 Windows SDK。  
  
-   Visual Studio。  
  
## <a name="creating-the-projects"></a>创建项目  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>若要创建使用按需程序集的项目  
  
1.  创建一个名为 ClickOnceOnDemand 目录。  
  
2.  打开 Windows SDK 命令提示或[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]命令提示符。  
  
3.  将更改为 ClickOnceOnDemand 目录。  
  
4.  生成使用以下命令公钥/私钥对：  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  使用记事本或其他文本编辑器中，定义一个名为类`DynamicClass`与名为的单个属性`Message`。  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  名为的文件另存文本`ClickOnceLibrary.cs`或`ClickOnceLibrary.vb`，取决于你使用到 ClickOnceOnDemand 目录的语言。  
  
7.  将文件编译到程序集。  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  若要获取的公钥令牌为程序集，请使用以下命令：  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. 创建新的文件使用你的文本编辑器，然后输入下面的代码。 此代码创建的 Windows 窗体应用程序需要时下载 ClickOnceLibrary 程序集。  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. 在代码中，找到调用<xref:System.Reflection.Assembly.LoadFile%2A>。  
  
11. 设置`PublicKeyToken`之前检索到的值。  
  
12. 将文件保存为`Form1.cs`或`Form1.vb`。  
  
13. 到使用以下命令可执行文件对其进行编译。  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>将程序集标记为可选  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>若要通过使用 MageUI.exe 中标记为可选 ClickOnce 应用程序中的程序集  
  
1.  使用 MageUI.exe 中，创建应用程序清单中所述[演练： 手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 对该应用程序清单中使用以下设置：  
  
    -   命名应用程序清单`ClickOnceOnDemand`。  
  
    -   上**文件**页上，在 ClickOnceLibrary.dll 行中，设置**文件类型**列**无**。  
  
    -   上**文件**页上，在 ClickOnceLibrary.dll 行中，类型`ClickOnceLibrary.dll`中**组**列。  
  
2.  使用 MageUI.exe 中，创建部署清单中所述[演练： 手动部署 ClickOnce 应用程序](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 对于部署清单中使用以下设置：  
  
    -   命名的部署清单`ClickOnceOnDemand`。  
  
## <a name="testing-the-new-assembly"></a>测试新程序集  
  
#### <a name="to-test-your-on-demand-assembly"></a>测试按需程序集  
  
1.  上载你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]向 Web 服务器部署。  
  
2.  启动应用程序部署与[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]从 Web 浏览器通过输入与部署清单的 URL。 如果调用你[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序`ClickOnceOnDemand`，并将其上载到 adatum.com 的根目录，你的 URL 将如下所示：  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  在主窗体显示时按 <xref:System.Windows.Forms.Button>。 你应看到"Hello，World ！"中读取一个消息框窗口中的字符串。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Deployment.Application.ApplicationDeployment>