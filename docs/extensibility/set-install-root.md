---
title: "安装与 VSIX v3 扩展文件夹之外 |Microsoft 文档"
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
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 6d87c86d0a7793f661c6a3b28e95340f3a28c616
ms.lasthandoff: 03/07/2017

---
# <a name="installing-outside-the-extensions-folder"></a>安装扩展文件夹之外

从 Visual Studio 2017 和 VSIX v3 （版本 3），现在支持用于安装外部 extensions 文件夹的扩展资产。 目前，作为有效的安装位置 （其中 [installdir] 映射到 Visual Studio 实例的安装目录），应启用下列位置︰

* [installdir] \Common7\IDE\PublicAssemblies
* [installdir] \Common7\IDE\ReferenceAssemblies
* [installdir] \MSBuild
* [installdir] \Schemas
* [installdir] \Licenses
* [installdir] \RemoteDebugger
* [installdir] \VSTargets

>**注意︰** VSIX 格式不允许您安装 VS 安装文件夹结构之外。

为了支持将安装到这些目录，VSIX 必须安装"每个实例每台计算机"。 可以通过检查 extension.vsixmanifest 设计器中的"所有用户"复选框来启用该选项︰

![检查所有用户](~/docs/extensibility/media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>如何设置 InstallRoot

若要设置的安装目录，可以使用**属性**Visual Studio 窗口中的。 例如，您可以设置`InstallRoot`属性的项目引用到上述位置之一︰

![安装根属性](~/docs/extensibility/media/install-root-properties.png)

这将一些元数据添加到相应的`ProjectReference`VSIX 项目的.csproj 文件内的属性︰

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**注意︰**如果您愿意，您可以直接编辑.csproj 文件。

## <a name="how-to-set-a-subpath-under-the-installroot"></a>如何设置 InstallRoot 下的子路径

如果您想要安装到下的子路径`InstallRoot`，可以执行操作来设置`VsixSubPath`属性一样`InstallRoot`属性。 例如，假设我们希望我们的项目引用的输出，以将安装到 [installdir]\MSBuild\MyCompany\MySDK\1.0。 我们可以轻松地与属性设计器执行此操作︰

![设置子路径](~/docs/extensibility/media/set-subpath.png)

相应的.csproj 更改将如下所示︰

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>附加信息

属性设计器更改应用于以外的其他项目的引用;您可以设置`InstallRoot`以及您的项目内的项元数据 （使用上面所述的相同方法）。

