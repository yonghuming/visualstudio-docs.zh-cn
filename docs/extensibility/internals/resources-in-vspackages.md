---
title: "在 Vspackage 中的资源 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4f74912dc5233cd62a4d35465d34c70e376c1df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="resources-in-vspackages"></a>在 Vspackage 中的资源
你可以在本机附属 UI Dll 托管的附属 Dll 或托管的 VSPackage 本身中嵌入的本地化的资源。  
  
 无法将某些资源嵌入在 Vspackage 中。 可以嵌入以下托管的类型：  
  
-   字符串  
  
-   程序包加载密钥 （这也是字符串）  
  
-   工具窗口图标  
  
-   已编译的命令表输出 （首席技术官） 文件  
  
-   首席技术官位图  
  
-   命令行帮助  
  
-   有关对话框数据  
  
 托管包中的资源选择的资源 id。 异常是首席技术官文件，它必须命名为 CTMENU。 首席技术官文件必须出现在资源表作为`byte[]`。 所有其他资源项由类型标识。  
  
 你可以使用<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>属性以指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是否提供了托管的资源。  
  
 [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 设置<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>以这种方式指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在搜索的资源，例如，通过使用时应忽略非托管的附属 Dll <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>。 如果[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]遇到两个或多个资源具有相同的资源 ID，它使用它找到的第一个资源。  
  
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
  
 下面的示例演示如何嵌入必须命名为 CTMENU 首席技术官字节数组。  
  
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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]只要有可能的 Vspackage 的延迟加载。 在 VSPackage 中嵌入首席技术官文件的结果是，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必须在安装期间，这是在构建合并的命令表时将加载在内存中的所有此类 Vspackage。 通过检查元数据，而无需在 VSPackage 中运行代码，可以从 VSPackage 中提取资源。 最小的性能损失而在此时，VSPackage 未初始化。  
  
 当[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]从安装后，VSPackage 的资源的请求，该程序包很可能已加载并初始化，因此是最小的性能损失。  
  
## <a name="see-also"></a>另请参阅  
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [MFC 应用程序中已本地化的资源：附属 DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
