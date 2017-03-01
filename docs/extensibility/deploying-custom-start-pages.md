---
title: "部署自定义起始页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 21
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9e99f022f1dec71b82c2261cae1d45705fe8dc7f
ms.lasthandoff: 02/22/2017

---
# <a name="deploying-custom-start-pages"></a>部署自定义起始页
您可以部署自定义起始页，通过使用 VSIX 部署或通过将文件复制到目标计算机上的正确位置。  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>通过使用开始页项目模板 VSIX 部署  
 在通过使用起始页项目模板创建的起始页，然后生成项目时 Visual Studio 创建您可以将分发.vsix 文件。 打包.vsix 文件中的启动页为您提供以下选项进行部署，具体取决于您的目标受众︰  
  
-   在网络共享或公共网站上，您可将.vsix 文件。 当某人打开该文件时，会自动安装启动页。  
  
-   你可以上载到.vsix 文件[Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)Web 站点，以便用户可以通过使用安装该**扩展管理器**。  
  
 起始页项目模板创建一份默认 Visual Studio 起始页，以便您可以修改副本，并保留原始。  
  
 你可以通过进行起始页项目模板**扩展管理器**或通过从网站下载它。  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>而无需使用开始页项目模板 VSIX 部署  
 成功的 VSIX 部署需要安装在由 VSIX 注册过程和识别的文件夹的扩展名**扩展管理器**。 由于起始页项目模板已指定了正确的文件夹中，我们建议你想要打包的 VSIX 部署的扩展时使用它。 但是，如果您有种情况下，不能使用该模板，您可以不使用它创建 VSIX 部署。  
  
 若要创建 VSIX 部署而无需使用起始页项目模板，首先创建为这两种方式之一启动页的.vsix 文件︰  
  
-   通过将自定义起始页文件添加到空的 VSIX 项目。 有关详细信息，请参阅[VSIX 项目模板](../extensibility/vsix-project-template.md)。  
  
-   通过手动创建.vsix 文件。 有关详细信息，请参阅[如何︰ 手动打包的扩展 （VSIX 部署）](../misc/how-to-manually-package-an-extension-vsix-deployment.md)。  
  
 对 Visual Studio 能够识别起始页中，`Content Element`的 VSIX 清单必须包含`CustomExtension Element`具有`Type`属性设置为`"StartPage"`。 通过使用 VSIX 部署在装有起始页扩展将出现在**自定义起始页**列表**启动**选项页上为**[安装扩展]** *扩展名*。  
  
 如果您的起始页程序包包括程序集，必须添加绑定路径注册，以便它们可用于 Visual Studio 将启动。 若要执行此操作，请确保您的软件包包含一个.pkgdef 文件，其中包含以下信息。  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>所有用户的的 VSIX 部署  
 默认情况下，部署 VSIX 包中的扩展插件仅为当前用户安装。 您可以进行起始页安装目标计算机的所有用户创建的所有用户部署。  
  
##### <a name="to-create-an-all-users-deployment"></a>若要创建的所有用户部署  
  
1.  在代码视图中打开 extension.vsixmanifest 文件。  
  
2.  在`Identifier`vsix 清单中的元素添加`AllUsers`元素的值为`true`。  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     这将导致 vsix 安装程序，然后将文件安装到 \Common7\IDE\Extensions 地提示您输入管理员权限。  
  
3.  打开.pkgdef 文件。  
  
4.  修改.pkgdef 设置默认起始页在 HKLM 下的通过添加以下内容，其中*MyStartPage.xaml*是包含起始页的.xaml 文件的名称。  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     这将告知 Visual 尤为中新的起始页位置进行查找。  
  
## <a name="file-copy-deployment"></a>文件复制部署  
 不需要创建要部署自定义的起始页的.vsix 文件。 相反，您可以直接在用户的 \StartPages\ 文件夹复制标记和支持文件。 **自定义起始页**列表**启动**选项页列出了该文件夹，以及该路径中的每个.xaml 文件 — 例如，%USERPROFILE%\My Documents\Visual Studio*版本*\StartPages\\*文件名*.xaml。 如果您启动的页面包括对私有程序集引用，必须将它们复制并粘贴 \PrivateAssemblies\ 文件夹中。  
  
 分发您创建不含包装起始页在.vsix 文件，我们建议你使用的基本文件复制策略，例如，批处理脚本或其他部署技术，您可以将这些文件置于所需的目录。  
  
#### <a name="to-manually-install-a-custom-start-page"></a>若要手动安装自定义的起始页  
  
1.  复制的.xaml 文件，包含起始页标记中，以及任何支持文件以外的程序集，并将其粘贴在用户的 \StartPages\ 文件夹中。  
  
2.  如果启动页需要的程序集，请将它们复制并粘贴在...\\ *Visual Studio 安装文件夹*\Common7\IDE\PrivateAssemblies\\。  
  
3.  在**自定义起始页**列表**启动**选项页上，选择新的启动页。 有关详细信息，请参阅[自定义起始页](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [自定义起始页](../ide/customizing-the-start-page-for-visual-studio.md)   
 [将用户控件添加到开始页](../extensibility/adding-user-control-to-the-start-page.md)
