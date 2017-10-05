---
title: "注册和注销 Vspackage |Microsoft 文档"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 312c06295492ac9bd1136ea7de9a0399f247c365
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="registering-and-unregistering-vspackages"></a>注册和注销 Vspackage
特性用于注册 VSPackage，但  
  
## <a name="registering-a-vspackage"></a>注册 VSPackage  
 特性可用于控制托管的 Vspackage 的注册。 .Pkgdef 文件中包含的所有注册信息。 基于文件的注册的详细信息，请参阅[CreatePkgDef 实用工具](../extensibility/internals/createpkgdef-utility.md)。  
  
 下面的代码演示如何使用标准注册特性注册你的 VSPackage。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>注销扩展  
 如果你已尝试过使用大量不同的 Vspackage，并且想要从实验实例中删除它们，你可以仅运行**重置**命令。 查找**重置 Visual Studio 实验实例**在你的计算机，开始页上或从命令行运行此命令：  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 如果你想要卸载已在你的 Visual Studio 的开发实例安装的扩展，请转到**工具 / 扩展和更新**，找到的扩展，然后单击**卸载**。  
  
 如果出于某种原因这些方法均未成功在卸载该扩展，可以将 VSPackage 程序集，从命令行取消注册，如下所示：  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>使用自定义注册特性注册扩展  
  
在某些情况下可能需要创建你的扩展的新注册属性。 若要添加新的注册表项，或将新值添加到现有的密钥，你可以使用注册特性。 新的属性必须派生自<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>，且必须重写<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>和<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>方法。  
  
### <a name="creating-a-custom-attribute"></a>创建自定义属性  
  
下面的代码演示如何创建新的注册属性。  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
```  
  
 <xref:System.AttributeUsageAttribute>在特性类中用于指定对该属性有关、 是否它可以使用一次以上，和是否可以继承的程序元素 （类、 方法等）。  
  
### <a name="creating-a-registry-key"></a>创建注册表项  
  
在下面的代码中，创建自定义特性**自定义**子项下要注册的 VSPackage 的密钥。  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
```  
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>创建现有的注册表项下的新值  
  
可以将自定义值添加到现有密钥。 下面的代码演示如何将新值添加到 VSPackage 注册密钥。  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```
  
## <a name="see-also"></a>另请参阅  
 [VSPackage](../extensibility/internals/vspackages.md)
