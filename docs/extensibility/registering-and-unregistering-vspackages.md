---
title: "注册和撤消注册 Vspackage |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
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
ms.openlocfilehash: 73039d6e9bf0db6b3deee00745e21660173f21c0
ms.lasthandoff: 02/22/2017

---
# <a name="registering-and-unregistering-vspackages"></a>注册和注销 Vspackage
您使用属性来注册 VSPackage，但  
  
## <a name="registering-a-vspackage"></a>注册 VSPackage  
 属性可用于控制托管的 VSPackages 的注册。 .Pkgdef 文件中包含的所有注册信息。 基于文件的注册的详细信息，请参阅[CreatePkgDef 实用程序](../extensibility/internals/createpkgdef-utility.md)。  
  
 下面的代码演示如何使用标准的注册属性来注册你的 VSPackage。  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>注销扩展  
 如果已尝试过使用大量不同的 Vspackage，并且想要从实验实例中删除它们，你可以仅运行**重置**命令。 查找**重置 Visual Studio 实验实例**在您的计算机，开始页上或从命令行运行以下命令︰  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 如果您想要卸载一个扩展，您已经在您的 Visual Studio 的开发实例安装，请转到**工具 / 扩展和更新**，找到扩展，然后单击**卸载**。  
  
 如果由于某种原因这些方法均未成功在卸载该扩展，可以将从命令行的 VSPackage 程序集取消注册，如下所示︰  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage](../extensibility/internals/vspackages.md)
