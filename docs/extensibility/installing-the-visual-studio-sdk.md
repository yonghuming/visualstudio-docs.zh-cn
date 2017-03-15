---
title: "安装 Visual Studio SDK |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9c25532605613b34ded15a4bd6a533e589b7fce2
ms.openlocfilehash: d039c50cea2ee038baec26fad02a98ae45f0d521
ms.lasthandoff: 02/22/2017

---
# <a name="installing-the-visual-studio-sdk"></a>安装 Visual Studio SDK
启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>作为 Visual Studio 安装的一部分安装 Visual Studio SDK  
 如果您想要在 Visual Studio 安装中包括 VSSDK，则必须执行自定义安装。  
  
> [!NOTE]
>  在安装可执行文件的情况下，Visual Studio SDK 称为**Visual Studio 扩展性工具**。  
  
1.  启动 Visual Studio 2015 安装。 您可以安装任何版本的 Visual Studio Express 除外。  
  
2.  在第一个屏幕上，选择**自定义**，而不**默认**。 单击“下一步” 。  
  
3.  您应看到自定义功能的树的视图。 打开**常见工具**。 您应该看到**Visual Studio 扩展性工具**。  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  检查**Visual Studio 扩展性工具**，然后单击**下一步**并继续安装。  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>在安装 Visual Studio 后安装 Visual Studio SDK  
 如果您决定在完成你的 Visual Studio 安装后安装 Visual Studio SDK，则应该遵循以下过程︰  
  
1.  转到**控制面板 / 程序 / 程序和功能**，并查找**Visual Studio 2015**。 您可以安装除 Express 之外的 Visual Studio 2015 的任何版本的 Visual Studio SDK。  
  
2.  用鼠标右键单击**Visual Studio 2015**，然后单击**更改**。 您应该看到安装页。  
  
3.  相同的步骤如下所示**作为 Visual Studio 安装的一部分安装 Visual Studio SDK**上方。  
  
4.  单击**Visual Studio 扩展性工具**指向安装 Visual Studio SDK 的链接。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>从解决方案安装 Visual Studio SDK  
 如果不首先安装 VSSDK，可以使用扩展性项目打开的解决方案，上面的解决方案资源管理器中突出显示的信息栏将提示你。 它看上去应如下所示︰  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>从命令行安装 Visual Studio SDK  
 可通过从命令行安装 VSSDK **/InstallSelectableItems**开关和 Visual Studio 安装程序。 有关使用安装程序使用命令行参数的详细信息，请参阅[使用命令行参数来安装 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)。  
  
 下面介绍了如何安装 VSSDK 以无提示方式使用 Visual Studio 2015 Community 安装程序︰  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 请注意，您必须使用与匹配您已安装的 Visual Studio 版本的 Visual Studio 安装程序。 例如，如果必须在计算机上安装的 Visual Studio Enterprise，您必须运行 Visual Studio Enterprise 安装程序 (vs_enterprise.exe)。
