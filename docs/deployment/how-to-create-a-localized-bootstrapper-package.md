---
title: "如何： 创建本地化的引导程序包 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f19ec03dda8666eea39b50af40a44ab2c68694ce
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>如何：创建本地化的引导程序包
在你创建引导程序包以后，你可以通过为每个区域设置再创建两个文件（软件许可条款文件（如 eula.rtf）和包清单 (package.xml)）来创建引导程序包的本地化版本。  
  
 默认情况下，Visual Studio 2010 只包括 .NET Framework 4、.NET Framework 4 Client Profile、F# Runtime 2.0 和 F# Runtime 4.0 的本地化引导程序包。 你可以通过完成三步操作来为其他引导程序创建本地化包。  
  
1.  创建 files\microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages 中的区域设置名称命名的文件夹\\*BootstrapperPackageName*。  
  
2.  创建包含引导程序包的软件许可条款的文件并将其放入新的文件夹中。  
  
3.  创建名为 package.xml 的包清单，更新字符串和区域性，并将该文件放入新的文件夹中。 如果你已经用目标语言创建 Visual Studio 的引导程序，则可以复制 Visual Studio package.xml 文件并在此步骤中修改它。  
  
> [!NOTE]
>  如果使用安装程序项目来部署应用程序，则可以通过更改本地化你的应用程序**本地化**属性。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>创建本地化的引导程序包  
  
1.  创建以区域设置名称命名的文件夹。  
  
     在 32 位计算机上创建文件夹中 files\microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\*BootstrapperPackageName*\ 文件夹。  
  
     在 64 位计算机上创建文件夹在 \Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\*BootstrapperPackageName*\ 文件夹。  
  
     下表显示可以用来匹配区域设置的文件夹名称。  
  
    |区域设置|文件夹名称|  
    |------------|-----------------|  
    |中文(简体)|zh-Hans|  
    |中文(繁体)|zh-Hant|  
    |捷克语|cs|  
    |德语|de|  
    |英语|en|  
    |西班牙语|es|  
    |法语|fr|  
    |意大利语|it|  
    |朝鲜语|ko|  
    |日语|ja|  
    |波兰语|pl|  
    |葡萄牙语(巴西)|pt-BR|  
    |俄语|ru|  
    |土耳其语|tr|  
  
2.  创建包含引导程序包的软件许可条款的文件并将其放入新的文件夹中。  
  
3.  创建名为 package.xml 的包清单并将其放入新的文件夹中。 有关详细信息，请参阅[如何： 创建程序包清单](../deployment/how-to-create-a-package-manifest.md)。  
  
4.  更新包清单的 `<Strings>` 部分，使字符串以正确的区域设置语言表示。  
  
5.  更改 `<String Name="Culture">` 值以匹配文件夹名称。  
  
6.  保存 package.xml 文件。  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>为用法语本地化的 .NET Framework 3.5 Service Pack 1 创建引导程序包  
  
1.  创建名为 fr 的文件夹。 该文件夹名称必须与区域设置名称匹配。  
  
     在 32 位计算机上，在 \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\ 文件夹中创建文件夹。  
  
     在 64 位计算机上，在 \Program Files (86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\ 文件夹中创建文件夹。  
  
2.  将软件许可条款的本地化版本放入 fr 文件夹。  
  
3.  将 \Program Files (x86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml 文件复制到 fr 文件夹，并在 XML 设计器中打开该文件。  
  
4.  更新包清单的 `<Strings>` 部分，以便用法语表示错误字符串。  
  
5.  将 `<String Name="Culture">` 值更改为 fr。  
  
6.  保存 package.xml 文件。  
  
## <a name="see-also"></a>另请参阅  
 [创建引导程序包](../deployment/creating-bootstrapper-packages.md)   
 [应用程序部署必备](../deployment/application-deployment-prerequisites.md)   
 [如何：创建程序包清单](../deployment/how-to-create-a-package-manifest.md)