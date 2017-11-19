---
title: "部署自定义起始页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2217b77116ea561c32e96fcb7b92b520e680025
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-custom-start-pages"></a>部署自定义起始页
通过使用 VSIX 部署或通过将文件复制到目标计算机上的正确位置，你可以部署自定义起始页。  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>使用起始页项目模板的 VSIX 部署  
 当你通过使用起始页项目模板，创建一个启动页，然后生成项目时，Visual Studio 将创建可以分发的.vsix 文件。 打包.vsix 文件中的启动页为您提供部署，具体取决于您的目标受众的以下选项：  
  
-   在网络共享或公共的 Web 站点上，你可以放置.vsix 文件。 当有人打开文件时，会自动安装启动页。  
  
-   你可以上载.vsix 文件到[Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)Web 站点，以便用户可以使用来安装它**扩展管理器**。  
  
 起始页项目模板创建一份默认 Visual Studio 起始页，以便可以修改副本，并保留原始。  
  
 你可以通过使用获取起始页项目模板**扩展管理器**或通过从网站下载它。  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX 部署，而不必使用起始页项目模板  
 成功的 VSIX 部署需要要由 VSIX 注册过程和识别的文件夹中安装的扩展**扩展管理器**。 由于起始页项目模板已指定正确的文件夹，我们建议你它使用，无论何时你想要扩展的 VSIX 部署打包。 但是，如果你具有的用例，你不能在其中使用该模板，你可以创建 VSIX 部署，而无需使用它。  
  
 创建 VSIX 部署而不使用起始页项目模板，首先创建这两种方式之一的启动页的.vsix 文件：  
  
-   通过将你的自定义起始页文件添加到一个空的 VSIX 项目。 有关详细信息，请参阅[VSIX 项目模板](../extensibility/vsix-project-template.md)。  
  
-   通过手动创建.vsix 文件。 若要手动创建.vsix 文件：  
    
    1.  在新的文件夹中创建 extension.vsixmanifest 文件和 [Content_Types].xml 文件。 有关详细信息，请参阅[剖析 VSIX 包](/visualstudio/extensibility/anatomy-of-a-vsix-package)。  
  
    2.  在 Windows 资源管理器，右键单击包含两个 XML 文件的文件夹，单击发送到，然后单击压缩 (zipped) 文件夹。 将生成的.zip 文件重命名为 Filename.vsix，这里的文件名是安装你的包的可再发行文件的名称。  
  
 Visual studio 能够识别起始页，`Content Element`的 VSIX 清单必须包含`CustomExtension Element`具有`Type`属性设置为`"StartPage"`。 已安装使用 VSIX 部署起始页扩展将出现在**自定义起始页**列表上**启动**选项页上为**[安装的扩展]***扩展名*。  
  
 如果你的起始页包包括程序集，必须添加绑定路径注册，以便在 Visual Studio 启动时才可用。 若要执行此操作，请确保你的包，包含一个.pkgdef 文件，其中包含以下信息。  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>所有用户的 VSIX 部署  
 默认情况下，仅为当前用户安装部署 VSIX 包中的扩展。 你可以通过创建的所有用户部署为起始页安装使目标计算机的所有用户。  
  
##### <a name="to-create-an-all-users-deployment"></a>若要创建的所有用户部署  
  
1.  在代码视图中打开 extension.vsixmanifest 文件。  
  
2.  在`Identifier`vsix 清单中，元素将添加`AllUsers`元素的值为`true`。  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     这将导致该 vsix 的安装程序提示管理员权限，然后将文件安装到 \Common7\IDE\Extensions。  
  
3.  打开.pkgdef 文件。  
  
4.  修改.pkgdef 设置默认起始页 HKLM 下的添加以下内容，其中*MyStartPage.xaml*是包含你的起始页.xaml 文件的名称。  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     这将告知 Visual 尤为要在新的起始页位置进行查找。  
  
## <a name="file-copy-deployment"></a>文件复制部署  
 不需要创建要部署自定义起始页的.vsix 文件。 相反，你可以直接在用户的 \StartPages\ 文件夹复制标记和支持文件。 **自定义起始页**列表上**启动**选项页将列出该文件夹，以及路径中的每个.xaml 文件-例如，%USERPROFILE%\My Documents\Visual Studio *版本*\StartPages\\*文件名*.xaml。 如果你的起始页包括对私有程序集引用，必须将其复制并将它们粘贴在 \PrivateAssemblies\ 文件夹。  
  
 若要分发起始页上，你创建不带打包在.vsix 文件，建议你使用的基本文件复制策略，例如，一个批处理脚本或其他部署技术，你可以将文件放入所需的目录。  
  
#### <a name="to-manually-install-a-custom-start-page"></a>若要手动安装自定义起始页  
  
1.  复制的.xaml 文件，包含起始页标记，以及程序集，以外的任何支持文件，并将它们粘贴在用户的 \StartPages\ 文件夹中。  
  
2.  如果启动页要求程序集，将其复制和粘贴在...\\ *Visual Studio 安装文件夹*\Common7\IDE\PrivateAssemblies\\。  
  
3.  在**自定义起始页**列表上**启动**选项页上，选择新的启动页。 有关详细信息，请参阅[自定义起始页](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [自定义起始页](../ide/customizing-the-start-page-for-visual-studio.md)   
 [将用户控件添加到起始页](../extensibility/adding-user-control-to-the-start-page.md)