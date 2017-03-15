---
title: "注册项目和项模板 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目 [Visual Studio SDK]，添加项"
  - "注册表中，添加新项对话框"
  - "“添加新项”对话框"
  - "添加新项目对话框"
  - "注册表中，添加新项目对话框"
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# 注册项目和项模板
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

项目类型必须注册他们的项目和项目项模板的位置的目录。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用与您的项目类型相关联的注册信息来确定要在中显示的内容 **添加新项目** 和 **添加新项** 对话框。  
  
 有关模板的详细信息，请参阅 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
## 项目的注册表项  
 下面的示例演示 HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ 下的注册表条目 \<*版本*\>。 随附的表列出的示例中使用的元素。  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|名称|类型|描述|  
|--------|--------|--------|  
|@|REG\_SZ|这种类型的项目的默认名称。|  
|DisplayName|REG\_SZ|在包下注册的名称的资源 ID，要从附属 DLL 中检索。|  
|package|REG\_SZ|在包下注册的包的类 ID。|  
|ProjectTemplatesDir|REG\_SZ|项目模板文件的默认路径。 通过显示中的项目模板文件 **新项目** 模板。|  
  
### 注册项模板  
 您必须注册其中存储项模板的目录。  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|名称|类型|描述|  
|--------|--------|--------|  
|@|REG\_SZ|添加项模板的资源 ID。|  
|TemplatesDir|REG\_SZ|显示在对话框中的项目项的路径 **添加新项** 向导。|  
|TemplatesLocalizedSubDir|REG\_SZ|资源 ID 命名的子目录 TemplatesDir 的字符串包含本地化的模板。 因为 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 加载如果您已拥有的字符串资源附属 Dll，每个附属 DLL 可以包含一个不同的本地化的子目录的名称。|  
|SortPriority|REG\_DWORD|设置来控制模板中的显示的顺序的 SortPriority **添加新项** 对话框。 模板列表中较早出现较大的 SortPriority 值。|  
  
### 注册文件筛选器  
 （可选） 可以注册的筛选器， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用提示输入的文件名。 例如， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 筛选 **打开的文件** 对话框时︰  
  
 **Visual C\# 文件 （\*.cs、 \*.resx、 \*.settings、 \*.xsd、 \*.wsdl）; \*.cs，\*.resx、 \*.settings、 \*.xsd、 \*.wsdl\)**  
  
 若要支持多个筛选器的注册，每个筛选器中登记下 HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ 自己子项 \<*版本*\> \\Projects\\ {\<*ProjectGUID*\>} \\Filters\\ \<*子项*\>。 子项的名称可以是任意; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 忽略子项的名称，并使用只是其值。  
  
 您可以控制在其中使用筛选器通过设置标志，如下表所示的上下文。 如果筛选器没有设置任何标志，它将列中的常见筛选器后 **添加现有项** 对话框和 **打开的文件** 对话框中，但它不会在使用 **在文件中查找** 对话框。  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|名称|类型|描述|  
|--------|--------|--------|  
|CommonFindFilesFilter|REG\_DWORD|使常见的筛选器之一中的筛选 **在文件中查找** 对话框。 在未标记为公共的筛选器之前的筛选器列表中列出了常用的筛选器。|  
|CommonOpenFilesFilter|REG\_DWORD|使常见的筛选器之一中的筛选 **打开的文件** 对话框。 在未标记为公共的筛选器之前的筛选器列表中列出了常用的筛选器。|  
|FindInFilesFilter|REG\_DWORD|中的常见筛选器后列出的筛选器 **在文件中查找** 对话框。|  
|NotOpenFileFilter|REG\_DWORD|表示筛选器不使用在 **打开的文件** 对话框。|  
|NotAddExistingItemFilter|REG\_DWORD|表示筛选器不使用在 **添加现有项** 对话框。|  
|SortPriority|REG\_DWORD|设置 SortPriority 来控制筛选器的显示的顺序。 筛选器列表中较早出现较大的 SortPriority 值。|  
  
## 目录结构  
 Vspackage 可以模板文件和文件夹在任何地方放置在本地或远程磁盘上，只要通过集成的开发环境 \(IDE\) 注册的位置。 但是，为了便于组织，我们建议您的产品的安装路径下的以下目录结构。  
  
 \\Templates  
  
 \\Projects （包含的项目模板）  
  
 \\Applications  
  
 \\Components  
  
 \\ ...  
  
 \\ProjectItems （包含的项目项）  
  
 \\Class  
  
 \\Form  
  
 \\Web 页  
  
 \\HelperFiles （包含多文件项目项中所使用的文件）  
  
 \\WizardFiles  
  
## 请参阅  
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [向导](../../extensibility/internals/wizards.md)   
 [本地化应用程序](../../ide/localizing-applications.md)   
 [通常用于扩展项目的对象的 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)