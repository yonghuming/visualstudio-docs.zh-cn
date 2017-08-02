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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 722c32c139d2f560fa6d10aba9fd8bac610f9f20
ms.lasthandoff: 03/07/2017

---
# <a name="installing-the-visual-studio-sdk"></a>安装 Visual Studio SDK
Visual Studio SDK 是 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>作为 Visual Studio 安装的一部分安装 Visual Studio SDK  
 如果您想要在 Visual Studio 安装中包括 VSSDK，则应安装**Visual Studio 扩展开发**工作负荷下的**其他工具集**。 这将安装 Visual Studio SDK，以及所需的先决条件。 您可以进一步优化安装，通过选择或取消选择组件从摘要视图。 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>在安装 Visual Studio 后安装 Visual Studio SDK  
 如果您决定在完成你的 Visual Studio 安装后安装 Visual Studio SDK，重新运行 Visual Studio 安装程序并选择**Visual Studio 扩展开发**工作负荷。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>从解决方案安装 Visual Studio SDK  
 如果不首先安装 VSSDK，可以使用扩展性项目打开的解决方案，上面的解决方案资源管理器中突出显示的信息栏将提示你。 它看上去应如下所示︰  
  
 ![SolutionExplorerInstall](~/docs/extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>从命令行安装 Visual Studio SDK  
与任何 Visual Studio 工作负荷或组件，您还可以从命令行安装项。 请参阅[使用命令行参数来安装 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)有关的适当的命令行开关以及如何确定工作负荷或组件标识符的详细信息。
  
 请注意，您必须使用与匹配您已安装的 Visual Studio 版本的 Visual Studio 安装程序。 例如，如果必须在计算机上安装的 Visual Studio Enterprise，您必须运行 Visual Studio Enterprise 安装程序 (vs_enterprise.exe)。
