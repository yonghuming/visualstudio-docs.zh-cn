---
title: "私有库 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX 库专用"
  - "专用库 VSIX"
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 私有库
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以共享控件、 模板和工具，通过粘贴到开发 *专用库* 为您的组织，如下所示在 intranet 上︰  
  
-   创建 Atom \(RSS\) 源到 intranet 上的适当配置中央位置 （存储库）。 有关详细信息，请参阅[如何: 创建 Atom 馈送专用库](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)。  
  
-   将分发描述专用库中的.pkgdef 文件。 我们建议此配置中的管理员想要连接到多台计算机的专用库，一次。  
  
## 将专用库添加到扩展和 Visual Studio 中的更新  
 提供一个专用库时，您可以将其添加到 **扩展和更新** Visual Studio 中。  
  
 ![“扩展管理器添加”对话框](~/extensibility/media/em_adddialog.png "EM\_AddDialog")  
  
#### 若要将私有库添加到扩展和更新  
  
1.  在菜单栏上，依次选择“工具”、“选项”。  
  
2.  在 **环境** 节点中，选择 **扩展和更新**。  
  
3.  选择**“添加”**按钮。  
  
4.  在 **名称** 字段中，例如，输入专用库的名称 `My Gallery`。  
  
5.  在 **URL** 字段中，输入的 Atom 馈送或承载专用库中的 SharePoint 站点的 URL。  
  
    1.  如果主机是一个 Atom 馈送︰ 连接到专用库，则 URL 将类似于此︰ http:\/\/www.mywebsite\/mygallery\/atom.xml。  此 URL 可以引用一个文件或网络路径。  
  
    2.  如果主机是 SharePoint 网站，URL 将类似于此︰ http:\/\/mysharepoint\/sites\/mygallery\/forms\/AllItems.aspx。  
  
### 管理专用库  
 管理员可以提供一个专用库到多台计算机同时通过修改每台计算机上的系统注册表。 若要实现此目的，创建介绍新的注册表项和它们的值的.pkgdef 文件。  下面是此文件的格式。  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 有关更多信息，请参见[如何︰ 通过使用注册表设置管理专用库](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)。  
  
## 从专用库安装扩展  
 您可以搜索并安装专用库，在从 Visual Studio 扩展 **扩展和更新**。 下列步骤将使用专用库中名为 `My Gallery`。  
  
 ![安装专用库的扩展管理器](~/extensibility/media/em_.png "EM\_")  
  
#### 搜索和从私有库安装扩展  
  
1.  在菜单栏上，选择**“工具”**，再选择**“扩展和更新”**。  
  
2.  在左窗格中，选择 **在线扩展**, ，然后选择 **我库**。  
  
3.  在右窗格中，选择一个扩展，扩展，然后选择 **下载** 按钮。  
  
## 从专用库更新扩展  
 在专用的库中发布新版本的 Visual Studio 扩展，可以更新已安装的扩展。 下列步骤将使用专用库中名为 `My Repository`。  
  
 ![扩展管理器专用库更新](~/extensibility/media/em_update.png "EM\_Update")  
  
#### 若要更新已安装的扩展从私有库  
  
1.  在菜单栏上，选择**“工具”**，再选择**“扩展和更新”**。  
  
2.  在左窗格中，选择 **更新**, ，然后选择 **我的存储库**。  
  
3.  在右窗格中，选择一个扩展，扩展，然后选择 **更新** 按钮。  
  
## 请参阅  
 [查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)   
 [传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)