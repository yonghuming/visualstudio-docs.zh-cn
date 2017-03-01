---
title: "部署层模型扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 27
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
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
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 03164fe80a0b8f4dbc321a7e57b7db9e38e405d5
ms.lasthandoff: 02/22/2017

---
# <a name="deploy-a-layer-model-extension"></a>部署层模型扩展
其他 Visual Studio 用户可通过使用 Visual Studio 安装你创建的层建模扩展。  
  
## <a name="installing-your-extension"></a>安装你的扩展  
 将你的扩展编译为可在其他计算机上安装的 VSIX 文件。 你也可以将其安装到开发计算机，确保该扩展在 Visual Studio 的主实例中可用。  
  
#### <a name="to-install-the-extension"></a>安装扩展  
  
1.  项目中包含**source.vsix.manifest**，打开**bin\\ \* **在文件资源管理器。  
  
2.  复制** \*.vsix**到要安装扩展的计算机的文件。  
  
3.  在目标计算机的 Windows 资源管理器中，双击 *.vsix 文件。  
  
     VSIX 安装程序将打开。  
  
#### <a name="to-uninstall-the-extension"></a>卸载扩展  
  
1.  在 Visual Studio 中，在**工具**菜单上，单击**扩展和更新**。  
  
2.  单击扩展插件的名称，然后单击**卸载**。  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>在 Team Foundation Build 服务器上安装扩展  
 通常情况下，[!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 服务器并未安装 Visual Studio，因此无法通过对其双击来安装 VSIX。 
          [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 的安装包括一些允许运行 VSIX 扩展的组件，但你必须手动安装该扩展。  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>在 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 服务器上安装层扩展  
  
1.  复制**.vsix**文件从开发计算机[!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]的计算机。  
  
     将 VSIX 文件置于下列位置之一：  
  
    -   为所有用户和服务安装：  
  
         %ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft  
  
    -   仅为运行 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 的网络服务安装：  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version] \Extensions\Microsoft  
  
    -   如果你已将 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] 配置为在交互模式下以特定用户身份运行，则你可以仅为该用户安装：  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version] \Extensions\Microsoft  
  
        > [!NOTE]
        >  %Localappdata%通常是*DriveName*︰ 用户*用户名*AppDataLocal。  
  
2.  将各个 VSIX 文件展开至相同位置的文件夹中：  
  
    1.  更改文件扩展名，从**.vsix**到**.zip**。  
  
    2.  将 .zip 文件中的内容提取到一个文件夹中。  
  
    3.  删除 .zip 文件。  
  
3.  重新启动 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]。

