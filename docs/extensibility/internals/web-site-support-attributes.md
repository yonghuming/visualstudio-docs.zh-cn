---
title: "网站支持特性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 504046999814b4766fa9e5e8c006a02049e7007d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="web-site-support-attributes"></a>网站支持属性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]网站项目可以扩展以支持 Web 编程语言。 语言必须注册自行向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以便项目模板可以出现在**新网站**对话框时选择的语言。  
  
 IronPython Studio 示例包括网站的支持。 它包括以下的属性类，以将 IronPython 注册为新的 Web 项目的代码隐藏文件语言。  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 此特性置于语言项目。 它将语言添加到 Web 编程语言中的列表**语言**列入**新网站**对话框。 例如，以下 IronPython 向列表添加：  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 此属性也设置的模板路径指向的模板文件夹。 有关模板文件夹的位置的详细信息，请参阅[网站支持模板](../../extensibility/internals/web-site-support-templates.md)。  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 此特性置于语言项目。 它允许在另一个文件类型 （主） 下，在网站项目嵌套 （相关） 的一种文件类型**解决方案资源管理器**。  
  
 例如:   
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 指定 IronPython 代码隐藏文件与一个.aspx 文件。 IronPython Web 站点解决方案中创建新的.aspx 网页后，新的、.py、 源文件生成，并且显示为子节点的.aspx 页面。  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 此特性置于语言项目包。 它将选择的语言的 Intellisense 提供程序。  
  
 例如:   
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 指定的 PythonIntellisenseProvider，实现实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>，应按需提供语言服务创建。  
  
 IVsIntellisenseProject 实现处理引用，并当具有代码的 Web 页请求，但不会缓存时调用的语言编译器。  
  
## <a name="see-also"></a>另请参阅  
 [网站支持](../../extensibility/internals/web-site-support.md)