---
title: "私有库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
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
ms.sourcegitcommit: 8ce054bf6149f0224785f4c3cd9274e86dc09d04
ms.openlocfilehash: e4c49a19a9befad5d90b9526842786f49af0851b
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="private-galleries"></a>Private Galleries
你可以共享控件、 模板和通过发布到开发的工具*专用库*对你的组织，如下所示 intranet 上：  
  
-   创建 Atom (RSS) 源到 intranet 上的适当配置的中央位置 （存储库）。 有关详细信息，请参阅[如何： 创建专用库 Atom 馈送](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)。  
  
-   将分发描述专用库的.pkgdef 文件。 我们建议管理员想要在同一时间连接到多台计算机的专用库的此的配置。  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>将专用库添加到扩展和 Visual Studio 中的更新  
 提供专用库时，你可以将其添加到**扩展和更新**Visual Studio 中。  
  
 ![扩展管理器添加对话框](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>将专用库添加到扩展和更新  
  
1.  在菜单栏上，依次选择“工具” 、“选项” 。  
  
2.  在**环境**节点中，选择**扩展和更新**。  
  
3.  选择 **“添加”** 按钮。  
  
4.  在**名称**字段中，例如，输入一个名称为专用库， `My Gallery`。  
  
5.  在**URL**字段中，输入 Atom 馈送或承载专用库的 SharePoint 站点的 URL。  
  
    1.  如果主机是一个 Atom 馈送： 连接到专用库，URL 将类似于此形式： http://www.mywebsite/mygallery/atom.xml。  此 URL 可以引用文件或网络路径。  
  
    2.  如果主机是 SharePoint 站点，该 URL 类似于此： http://mysharepoint/sites/mygallery/forms/AllItems.aspx。  
  
### <a name="managing-private-galleries"></a>管理私有库  
 管理员可以提供专用库到多台计算机在同一时间通过修改每台计算机上的系统注册表。 若要实现此目的，创建新的注册表项和其值描述一个.pkgdef 文件。  此文件的格式如下所示。  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 有关详细信息，请参阅[如何： 管理私有库通过使用注册表设置](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)。  
  
## <a name="installing-extensions-from-a-private-gallery"></a>从专用库安装扩展  
 你可以搜索和专用库中, 安装 Visual Studio 扩展**扩展和更新**。 下列步骤将使用名为专用库`My Gallery`。  
  
 ![安装专用库的扩展管理器](../extensibility/media/em_.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>若要搜索并从专用库安装扩展  
  
1.  在菜单栏上，选择“工具”，再选择“扩展和更新”。  
  
2.  在左窗格中，选择**联机扩展**，然后选择**我库**。  
  
3.  在右窗格中，选择扩展，，然后选择**下载**按钮。  
  
## <a name="updating-extensions-from-a-private-gallery"></a>从专用库更新扩展  
 在私有的库中发布新版本的 Visual Studio 扩展，可更新已安装的扩展。 下列步骤将使用名为专用库`My Repository`。  
  
 ![扩展管理器专用库更新](../extensibility/media/em_update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>若要更新已安装的扩展从专用库  
  
1.  在菜单栏上，选择“工具”，再选择“扩展和更新”。  
  
2.  在左窗格中，选择**更新**，然后选择**我的存储库**。  
  
3.  在右窗格中，选择扩展，，然后选择**更新**按钮。  
  
## <a name="see-also"></a>另请参阅  
 [查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)   
 [传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)
