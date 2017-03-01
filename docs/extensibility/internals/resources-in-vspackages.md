---
title: "VSPackages 迁移中的资源 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 23
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 184642501b9452566a15e1aba30312e17500f7bb
ms.lasthandoff: 02/22/2017

---
# <a name="resources-in-vspackages"></a>在 Vspackage 中的资源
本机附属 UI Dll 托管的附属 Dll 中或在托管 VSPackage 本身中，您可以嵌入的本地化的资源。  
  
 无法在 Vspackage 中嵌入一些资源。 可嵌入以下托管的类型︰  
  
-   字符串  
  
-   包加载密钥 （这也是字符串）  
  
-   工具窗口图标  
  
-   已编译的命令表输出 （首席技术官） 文件  
  
-   首席技术官位图  
  
-   命令行帮助  
  
-   关于对话框数据  
  
 管理包中的资源选择的资源 id。 异常是首席技术官文件，必须命名为 CTMENU。 首席技术官文件必须出现在资源表作为`byte[]`。 所有其他资源项类型进行标识。  
  
 您可以使用<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>属性以指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]托管的资源都可用。</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>  
  
 [!code-cs[VSSDKResources&#1;](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources&#1;](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 设置<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>以这种方式指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在它搜索资源，例如，通过使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>时应忽略非托管的附属 Dll</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 如果[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]遇到两个或多个资源具有相同的资源 ID，它使用它找到的第一个资源。  
  
## <a name="example"></a>示例  
 下面的示例是一个工具窗口图标托管表示形式。  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 下面的示例演示如何将嵌入的首席技术官字节数组，必须将命名为 CTMENU。  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>实现说明  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackages 迁移尽可能延迟加载。 首席技术官文件嵌入在 VSPackage 中后果是，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必须在安装期间，这是合并的命令表进行生成时加载所有此类 VSPackages 迁移在内存中的。 通过检查元数据不在 VSPackage 中运行代码的情况下，可以从 VSPackage 中提取资源。 最小的性能损失是这次 VSPackage 未初始化。  
  
 当[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]请求资源从 VSPackage 安装完成后，该包是有可能已加载并初始化，因此性能损失是最小。  
  
## <a name="see-also"></a>另请参阅  
 [托管的 VSPackages](../../misc/managed-vspackages.md)   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [已本地化的 MFC 应用程序中的资源︰ 附属 Dll](http://msdn.microsoft.com/Library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [托管的 VSPackage](../../misc/managed-vspackages.md)
