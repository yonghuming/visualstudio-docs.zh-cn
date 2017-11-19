---
title: "如何： 包括与 ClickOnce 应用程序的系统必备组件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 18431ea15b53959234da4b2c6dedb24b8fa2e390
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>如何：将必备组件与 ClickOnce 应用程序包括在一起
你必须先将必备软件的安装程序包下载到开发计算机上，然后才能使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序分发这些软件。 当你发布应用程序并选择**从与我的应用程序相同的位置下载系统必备组件**，将会出错，如果安装程序包不在**包**文件夹。  
  
> [!NOTE]
>  若要添加.NET framework 的安装程序包，请参阅[开发人员的.NET Framework 部署指南](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx)。  
  
##  <a name="Package"></a>使用 Package.xml 添加安装程序包  
  
1.  在文件资源管理器，打开**包**文件夹。  
  
     默认情况下，路径为 C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages（32 位系统）和 C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages（64 位系统）。  
  
2.  打开你想要添加的系统必备组件的文件夹，然后打开你安装的版本的语言文件夹[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)](例如， **en**为英语)。  
  
3.  在记事本中，打开**Package.xml**文件。  
  
4.  找到**名称**包含的元素**http://go.microsoft.com/fwlink**，并复制 URL。 包括**LinkID**部分。  
  
    > [!NOTE]
    >  如果没有**名称**元素包含**http://go.microsoft.com/fwlink**，打开**Product.xml**的系统必备组件的根文件夹中文件并找到**fwlink**字符串。  
  
    > [!IMPORTANT]
    >  某些系统必备组件具有多个安装程序包（例如，用于 32 位或 64 位系统）。 如果选择多个**名称**元素包含**fwlink**，必须为每个重复的剩余步骤。  
  
5.  将 URL 粘贴到你的浏览器的地址栏，然后，系统提示要运行还是保存时，选择**保存**。  
  
     此步骤将安装程序文件下载到你的计算机中。  
  
6.  将此文件复制到系统必备组件的根文件夹中。  
  
     例如，对于 Windows Installer 4.5 系统必备组件，请将此文件复制到 \Packages\WindowsInstaller4_5 文件夹中。  
  
     现在你可以将安装程序包与你的应用程序一起分发。  
  
## <a name="see-also"></a>另请参阅  
 [如何：与 ClickOnce 应用程序一起安装系统必备组件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)