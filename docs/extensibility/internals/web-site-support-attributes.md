---
title: "网站支持属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 9
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
ms.openlocfilehash: dba1aeb8f8e3ad368f050ef425f76cc6c94f99e8
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support-attributes"></a>网站支持属性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]网站项目可以进行扩展以提供对 Web 的支持的编程语言。 语言必须将自己注册[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]这样，项目模板可以出现在**新的 Web 站点**对话框时选择的语言。  
  
 IronPython Studio 示例包括 web 站点的支持。 您可以找到其与[VSSDK 示例](../../misc/vssdk-samples.md)。 它包括以下的特性类，以将 IronPython 注册为新的 Web 项目的代码隐藏文件语言。  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 此特性置于语言项目。 它将语言添加到列表中的 Web 编程语言中的**语言**列入**新的 Web 站点**对话框。 例如，以下 IronPython 向列表添加︰  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 此属性还将设置模板路径以指向模板文件夹。 模板文件夹的位置的详细信息，请参阅[Web 站点支持模板](../../extensibility/internals/web-site-support-templates.md)。  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 此特性置于语言项目。 它允许在另一种文件类型 （主） 中的网站项目中嵌套 （相关） 的一种文件类型**解决方案资源管理器**。  
  
 例如:   
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 指定 IronPython 代码隐藏文件与.aspx 文件。 IronPython Web 站点解决方案中创建一个新的.aspx 网页时，新的、.py、 源文件生成并显示为.aspx 页的一个子节点。  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 此特性置于语言项目包。 它将选择的语言的 Intellisense 提供程序。  
  
 例如:   
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 指定 PythonIntellisenseProvider，实现的实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>，应按需提供语言服务创建。</xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>  
  
 IVsIntellisenseProject 实现处理引用，并带有代码的网页请求，但不是进行缓存时，将调用的语言编译器。  
  
## <a name="see-also"></a>另请参阅  
 [网站支持](../../extensibility/internals/web-site-support.md)
