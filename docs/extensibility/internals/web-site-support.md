---
title: "网站支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 17
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
ms.openlocfilehash: 636cbee868bb53be2d0ef85bd309459570eb84c0
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support"></a>网站支持
Web 站点项目系统是创建 Web 项目的项目系统。 Web 项目又会创建 Web 应用程序。 Web 站点项目会生成一个可执行文件为每个具有关联的代码的网页。 其他可执行文件是从源代码文件 /App_Code 文件夹中生成的。  
  
 通过将模板和注册属性添加到现有的项目系统创建的 web 站点项目系统。 其中一个属性选择的语言智能感知提供程序。 IntelliSense 提供程序实现处理引用，并在不缓存智能网页的请求时调用的语言编译器。  
  
 用来编译 Web 页面的语言编译器必须将注册[!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]。 您可以使用[\<编译器&1;> 元素](http://msdn.microsoft.com/Library/7a151659-b803-4c27-b5ce-1c4aa0d5a823)在 Web.config 文件以注册该编译器中的，如以下示例所示︰  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>本节内容  
 [支持的网站模板](../../extensibility/internals/web-site-support-templates.md)  
 列出可用于创建新网站项目和相关的项的模板。  
  
 [网站支持属性](../../extensibility/internals/web-site-support-attributes.md)  
 显示连接到网站项目的注册属性[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和[!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]。  
  
## <a name="related-sections"></a>相关章节  
 [Web 项目](../../extensibility/internals/web-projects.md)  
 提供两种类型的 Web 项目、 网站项目和 Web 应用程序项目的概述。
