---
title: "Web 项目 Essentials | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "web 项目 essentials"
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Web 项目 Essentials
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Web 项目创建 Web 应用程序。 可以使用 Web 项目创建的 Web 应用程序有智能 Web 页。 智能网页上的呈现按需 Web 页面的服务器端代码。  
  
 使用传统的编程语言，如 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], ，你可以创建智能的 Web 页面，以收集和处理来自用户的信息，将其存储在数据库中，依次类推。  
  
-   代码隐藏模型将与具有文件扩展名.aspx 或.asmx 的网页关联依赖源代码文件。 例如，hello.aspx 可能必须依赖源代码文件 hello.aspx.cs。  
  
-   与智能网页关联的服务器端代码会编译成可执行文件位于网站 /bin 文件夹中。  
  
-   其他的源代码文件，如不与特定的 Web 页上，相关联的帮助器类位于网站 /App_Code 文件夹中。  
  
    -   网站项目 (WSP) 将生成一个可执行文件为每个智能 Web 页。 其他可执行文件是从任何 /App_Code 文件夹中的源代码文件中生成的。  
  
    -   Web 应用程序项目 (WAP) 生成合并所有智能 Web 页面，以及 /App_Code 文件夹中的所有源文件的代码的单个可执行文件。  
  
-   Web 项目的解决方案文件位于独立于该网站本身。 默认情况下，解决方案文件均位于 \Documents and 设置\\*你的帐户*\My Documents\\*\< Visual Studio # # # >*\Projects\\*YourWebSite*。  
  
    > [!NOTE]
    >  如果你想要保留与网站的解决方案文件，只需将其移存在并重新打开它。  
  
-   如果您打开 Visual Studio 中没有解决方案文件的网站，它为自动生成新的解决方案文件。  
  
-   Web 项目具有的任何项目文件。 项目信息存储在解决方案文件、 web.config 文件中，和其他地方。  
  
-   自动添加到 Web 项目的全局属性在 Web 项目的解决方案文件夹中创建存储文件。  
  
-   智能网页又可通过使用页指令与服务器端编程语言或 \< 脚本 runat ="server"> 标记。  
  
-   此外，Web 页可以具有任意任何的数量脚本语言编写的客户端脚本块。  
  
-   网站项目系统实现通过添加项目和项模板和注册到 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] 项目。  
  
-   WAP 系统实现为项目子类型，也称为项目风格。  [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] 项目风格的 WAP 子类型，以创建 WAP 系统。 有关项目子类型的详细信息，请参阅 [项目子类型](../../extensibility/internals/project-subtypes.md)。  
  
-   智能网页将 HTML 与服务器端编程语言相结合。 服务器端语言称为包含的语言。 若要支持包含的语言，Web 项目系统必须实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 系列的接口。  
  
    -   若要支持在编辑器中包含的语言，HTML 语言服务必须推迟到包含的语言服务显示包含的语言代码。  
  
    -   始终应在代码编辑器的主缓冲区中创建错误标记 （红色标记）。  
  
## <a name="see-also"></a>请参阅  
 [Web 项目](../../extensibility/internals/web-projects.md)