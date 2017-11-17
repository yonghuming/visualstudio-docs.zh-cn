---
title: "如何： 创建的包清单 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 92182b9b6c6b2b2759b77e7b14d71dfd40379fc7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-package-manifest"></a>如何：创建程序包清单
若要部署你的应用程序的先决条件，你可以使用引导程序包。 引导程序包包含一个单个产品清单文件，但是包清单的每个区域设置。 产品清单都应共享的功能分布在不同的本地化版本。  
  
 有关包清单的详细信息，请参阅[如何： 创建产品清单](../deployment/how-to-create-a-product-manifest.md)。  
  
## <a name="creating-the-package-manifest"></a>创建包清单  
  
#### <a name="to-create-the-package-manifest"></a>若要创建包清单  
  
1.  创建引导程序包的目录。 此示例使用 C:\package。  
  
2.  创建的区域设置，例如英语 en 同名的子目录。  
  
3.  在 Visual Studio 中，创建名为一个 XML 文件`package.xml`，并将其保存到 C:\package\en 文件夹。  
  
4.  添加 XML 以列出相应的引导程序包的名称、 此本地化的包清单，以及可选的许可协议的区域性。 下面的 XML 使用变量`DisplayName`和`Culture`，这在后面的一个元素中定义。  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  添加 XML，以列出在特定于区域设置的目录中的所有文件。 下面的 XML 使用名为适用于的 eula.txt 文件**en**区域设置。  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  添加 XML，以定义引导程序包的可本地化字符串。 下面的 XML 将添加的 en 区域设置的错误字符串。  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  将 C:\package 文件夹复制到 Visual Studio 引导程序目录。 对于 Visual Studio 2010 中，这是 files\microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages 目录。  
  
## <a name="example"></a>示例  
 包清单包含特定于区域设置信息，例如错误消息、 软件许可条款和语言包。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>另请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)