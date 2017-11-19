---
title: "指定文件扩展名的文件处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5833285a3d9ce9df02dc0359379ea623054588a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>指定文件扩展名的文件处理程序
有多种方式可确定处理具有特定文件扩展名的文件的应用程序。 OpenWithList 和 OpenWithProgids 谓词是两种方法可以指定文件的文件扩展名的注册表项之下的处理程序。  
  
## <a name="openwithlist-verb"></a>OpenWithList 谓词  
 右键单击 Windows 资源管理器中的文件时，你将看到**打开**命令。 如果多个产品与扩展相关联，你将看到**打开**子菜单。  
  
 你可以注册不同应用程序可通过在注册表中设置的文件扩展名的 OpenWithList 密钥打开扩展。 列出有关文件扩展名的文件的此项下的应用程序会出现在**推荐的程序**标题中**打开**对话框。 下面的示例演示注册以打开.vcproj 文件扩展名的应用程序。  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  指定应用程序的键是从 HKEY_CLASSES_ROOT\Applications 下的列表。  
  
 通过添加 OpenWithList 密钥，你可以声明你的应用程序支持文件扩展名的文件，即使另一个应用程序将获得扩展的所有权。 这可能是你的应用程序或其他应用程序的未来版本。  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 编程标识符 (Progid) 是友好版本的 Classid 标识应用程序或 COM 对象的版本。 每个可共同创建的对象应具有其自己的 ProgID。 同时 VisualStudio.DTE.10.0 开始 VisualStudio.DTE.7.1; 例如，启动 Visual Studio.NET 2003年[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 作为项目类型或项目项类型的所有者，必须为该文件扩展名来创建特定于版本的 ProgID。 以下 Progid 可能冗余，因为多个 ProgID 可能会启动同一应用程序。 有关详细信息，请参阅[注册文件扩展名的谓词](../extensibility/registering-verbs-for-file-name-extensions.md)。  
  
 使用版本控制文件 Progid 以下命名约定以避免与其他供应商的注册重复：  
  
|文件扩展名|版本控制 ProgID|  
|--------------------|----------------------|  
|.extension|产品名称。 extension.versionMajor.versionMinor|  
  
 你可以注册不同应用程序能够通过将已进行版本管理 Progid 作为值添加到 hkey_classes_root。 打开特定的文件扩展名\\*\<扩展 >*\OpenWithProgids 密钥。 此注册表项包含与文件扩展名关联的备用 Progid 的列表。 与列出的 Progid 关联的应用程序出现在**打开***产品名称*子菜单。 如果同一应用程序中同时指定`OpenWithList`和`OpenWithProgids`密钥，操作系统将合并重复项。  
  
> [!NOTE]
>  `OpenWithProgids` Windows XP 中仅支持密钥。 因为其他操作系统忽略此密钥，请不要使用它作为唯一的注册文件处理程序。 使用此密钥来提供更好的用户体验在 Windows XP。  
  
 添加所需的 Progid 作为类型 REG_NONE 的值。 下面的代码提供了一个示例的 Progid 注册的文件扩展名的文件 (。*ext*)。  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 指定为文件扩展名的默认值是默认文件处理程序的 ProgID。 如果修改附带的早期版本的文件扩展名的 ProgID[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]或将接管其他应用程序，则必须注册`OpenWithProgids`密钥的文件扩展名并连同列表中指定的新 ProgID支持旧 Progid。 例如:   
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 如果旧 ProgID 具有与其关联的谓词，则这些谓词还将显示下**打开***产品名称*的快捷菜单中。  
  
## <a name="see-also"></a>另请参阅  
 [有关文件扩展名](../extensibility/about-file-name-extensions.md)   
 [注册文件扩展名的谓词](../extensibility/registering-verbs-for-file-name-extensions.md)