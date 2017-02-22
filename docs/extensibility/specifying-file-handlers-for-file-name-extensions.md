---
title: "指定文件扩展名的文件处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "指定文件处理程序的文件扩展名"
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 指定文件扩展名的文件处理程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有多种方法来确定处理特定的文件扩展名的文件的应用程序。 OpenWithList 和 OpenWithProgids 谓词是两种方法可以指定文件的文件扩展名的注册表项之下的处理程序。  
  
## OpenWithList 谓词  
 右键单击 Windows 资源管理器中的某个文件时，您将看到 **打开** 命令。 如果多个产品与扩展相关联，您将看到 **打开** 子菜单。  
  
 您可以注册不同应用程序可通过在 HKEY\_CLASSES\_ROOT 中设置的文件扩展名的 OpenWithList 键打开扩展。 在文件扩展名为此项下面列出的应用程序会显示在 **推荐的程序** 标题中 **打开** 对话框。 下面的示例演示打开.vcproj 文件扩展名为您注册的应用程序。  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  指定应用程序键都来自 HKEY\_CLASSES\_ROOT\\Applications 下的列表。  
  
 通过添加 OpenWithList 键，您在声明您的应用程序支持文件扩展名，即使另一个应用程序将获得扩展的所有权。 这可能是您的应用程序或其他应用程序的未来版本。  
  
## OpenWithProgIDs  
 编程标识符 \(Progid\) 是友好版本的 Classid 标识应用程序或 COM 对象的版本。 每个共同创建的对象应具有其自己的 ProgID。 例如，VisualStudio.DTE.7.1 启动 Visual Studio.NET 2003 VisualStudio.DTE.10.0 启动时 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 作为项目类型或项目项类型的所有者，必须为您的文件扩展名来创建特定于版本的 ProgID。 这些 Progid 可能是冗余的多个 ProgID 可能启动同一个应用程序。 有关更多信息，请参见[注册文件扩展名的谓词](../extensibility/registering-verbs-for-file-name-extensions.md)。  
  
 使用版本控制文件的 Progid 为以下命名约定以避免与其他供应商提供的注册重复︰  
  
|文件扩展名|版本控制 ProgID|  
|-----------|-----------------|  
|.extension|产品名称。 extension.versionMajor.versionMinor|  
  
 您可以注册不同应用程序能够通过将版本控制的 Progid 作为值添加到 HKEY\_CLASSES\_ROOT\\ 打开某个特定文件扩展名*\< 扩展 \>*\\OpenWithProgids 键。 此注册表项包含文件扩展名关联的备用 Progid 的列表。 与列出的 Progid 关联的应用程序出现在 **打开***产品名称* 子菜单。 如果同一个应用程序中同时指定 `OpenWithList` 和 `OpenWithProgids` 密钥，操作系统将合并重复项。  
  
> [!NOTE]
>  `OpenWithProgids` 密钥仅支持在 Windows XP 中。 由于其他操作系统忽略此项，请不要使用它作为唯一的注册文件处理程序。 使用此密钥来提供在 Windows XP 中更好的用户体验。  
  
 添加所需的 Progid 作为类型 REG\_NONE 的值。 下面的代码提供举例说明如何为文件扩展名注册的 Progid \(。*ext*\).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 与指定的文件扩展名的默认值就是在默认文件处理程序的 ProgID。 如果您修改附带的早期版本的文件扩展名的 ProgID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或将接管其他应用程序，则必须注册 `OpenWithProgids` 文件扩展名的密钥和以及您支持旧 Progid 列表中指定的新 ProgID。 例如：  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 如果旧 ProgID 具有与其关联的谓词，则这些谓词也会出现在 **打开** *产品名称* 的快捷菜单中。  
  
## 请参阅  
 [有关文件扩展名](../extensibility/about-file-name-extensions.md)   
 [注册文件扩展名的谓词](../extensibility/registering-verbs-for-file-name-extensions.md)