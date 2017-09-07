---
title: "如何： 使用注册表设置来管理专用库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 6
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
ms.openlocfilehash: 00c42a4dbd6a9a526d661b7fa04793d531acd8bc
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>如何： 使用注册表设置来管理专用库
如果你是管理员或开发人员的独立 Shell 扩展，你可以控制对控件、 模板和 Visual Studio 库、 示例库或专用库中的工具访问。 若要使库可用或不可用，请创建一个.pkgdef 文件，用于描述已修改的注册表项和它们的值。  
  
## <a name="managing-private-galleries"></a>管理私有库  
 你可以创建一个.pkgdef 文件来控制对多台计算机上的库的访问。 此文件必须具有以下格式。  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories`密钥引用库以启用或禁用。 Visual Studio 库和示例库使用以下存储库的 Guid:  
  
-   Visual Studio 库： 0F45E408-7995-4375-9485-86B8DB553DC9  
  
-   示例库： AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
 `Disabled`值是可选的。 默认情况下，启用库。  
  
 `Priority`值确定在选项对话框中列出的库的顺序。 Visual Studio 库具有优先级为 10，并且示例库具有优先级 20。 专用库在优先级 100 处开始。 如果多个库具有相同的优先级值，它们出现的顺序将由其本地化值`DisplayName`属性。  
  
 `Protocol` ，则需要对基于 Atom 或基于 SharePoint 的库的值。  
  
 请`DisplayName`，和 / 或`DisplayNameResourceID`和`DisplayNamePackageGuid`，必须指定。 如果指定了所有，则`DisplayNameResourceID`和`DisplayNamePackageGuid`对用于。  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>禁用 Visual Studio 库使用.pkgdef 文件  
 你可以禁用.pkgdef 文件中的库。 以下条目禁用 Visual Studio 库：  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 以下条目禁用示例库：  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [专用库](../extensibility/private-galleries.md)
