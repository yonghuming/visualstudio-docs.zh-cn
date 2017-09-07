---
title: "使用 VSIX v3 扩展文件夹之外安装 |Microsoft 文档"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: 1
author: gregvanl
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: da7f91cc71eb6d0bc403089a0e34b6d81165e026
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="installing-outside-the-extensions-folder"></a>安装扩展文件夹之外

从 Visual Studio 2017 和 VSIX v3 （版本 3），现在支持用于安装扩展文件夹外的扩展资产。 目前，作为有效的安装位置 （其中 [INSTALLDIR] 映射到 Visual Studio 实例的安装目录） 启用的以下位置：

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets

>**注意：** VSIX 格式不允许您将其安装在 VS 安装文件夹结构之外。

为了支持安装到这些目录，VSIX 必须安装"每个实例每台计算机"。 通过检查 extension.vsixmanifest 设计器中的"所有用户"复选框，可以启用此：

![检查所有用户](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>如何设置 InstallRoot

若要设置的安装目录，你可以使用**属性**Visual Studio 中的窗口。 例如，你可以设置`InstallRoot`到上述位置之一的项目引用的属性：

![安装根属性](media/install-root-properties.png)

这会将一些元数据添加到相应`ProjectReference`在 VSIX 项目的.csproj 文件的属性：

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**注意：**如果你愿意，你可以直接编辑.csproj 文件。

## <a name="how-to-set-a-subpath-under-the-installroot"></a>如何设置子路径下 InstallRoot

如果你想要安装到下的子路径`InstallRoot`，你可以通过设置来实现`VsixSubPath`属性就像`InstallRoot`属性。 例如，假设我们想要我们项目引用的输出，以将安装到 [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0。 轻松使用属性设计器，我们可以执行此操作：

![组的子路径](media/set-subpath.png)

相应的.csproj 更改将如下所示：

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>额外的信息

属性设计器更改适用于以外的其他项目引用;你可以设置`InstallRoot`以及你的项目内的项元数据 （使用上文所述的相同方法）。

