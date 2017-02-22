---
title: "如何：创建程序包清单 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "依赖项, 自定义引导程序包"
  - "包文件 [ClickOnce]"
  - "包文件 [Windows Installer]"
  - "系统必备, 自定义引导程序包"
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：创建程序包清单
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要为您的应用程序部署系统必备组件，您可以使用引导程序包。  引导程序包包含单个产品清单文件以及与每个区域设置一一对应的程序包清单。  不同的本地化版本共享的功能应放入产品清单中。  
  
 有关程序包清单的更多信息，请参见[如何：创建产品清单](../deployment/how-to-create-a-product-manifest.md)。  
  
## 创建程序包清单  
  
#### 创建程序包清单  
  
1.  为引导程序包创建目录。  此示例使用 C:\\package。  
  
2.  使用区域设置的名称（如 en 代表英语）创建一个子目录。  
  
3.  在 Visual Studio 中，创建一个名为 `package.xml` 的 XML 文件，并将其保存到 C:\\package\\en 文件夹中。  
  
4.  添加 XML 以列出引导程序包的名称、此本地化程序包清单的区域性和可选的许可协议。  下面的 XML 使用在后面的一个元素中定义的 `DisplayName` 变量和 `Culture` 变量。  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  添加 XML 以列出特定于区域设置的目录中的所有文件。  下面的 XML 使用适用于**“en”**区域设置的名为 eula.txt 的文件。  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  添加 XML 以为引导程序包定义可本地化的字符串。  下面的 XML 为 en 区域设置添加错误字符串。  
  
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
  
7.  将 C:\\package 文件夹复制到 Visual Studio 引导程序目录中。  对于 Visual Studio 2010，该目录为 \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages。  
  
## 示例  
 程序包清单包含特定于区域设置的信息，如错误消息、软件许可条款和语言包。  
  
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
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)