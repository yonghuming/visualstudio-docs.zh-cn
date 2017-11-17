---
title: "&lt;PackageFiles&gt;元素 （引导程序） |Microsoft 文档"
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
helpviewer_keywords: <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: a85b06bfc5c82e7d4bd08bef8f768ad2e28a2ab0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles&gt;元素 （引导程序）
`PackageFiles`元素包含`PackageFile`元素，后者定义的结果执行的安装程序包`Command`元素。  
  
## <a name="syntax"></a>语法  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `PackageFiles`元素具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|可选。 如果设置为`false`，安装程序将仅下载文件从引用`Command`元素。 如果设置为`true`，将下载所有文件。<br /><br /> 如果设置为`IfNotHomesite`，安装将具有相同的行为就像`False`如果`ComponentsLocation`设置为`HomeSite`，和将否则具有相同行为就像`True`。 此设置可用于在 HomeSite 方案中执行其自己的行为对于允许它们本身的程序包。<br /><br /> 默认值为 `true`。|  
  
## <a name="packagefile"></a>即包文件  
 `PackageFile`元素是的子`PackageFiles`元素。 A`PackageFiles`元素必须具有至少一个`PackageFile`元素。  
  
 `PackageFile`具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`Name`|必需。 包文件的名称。 这是的名称，`Command`它定义包安装在其下的条件时，将引用元素。 此值还用作键到`Strings`表以检索等工具的本地化的名称[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]将用来描述包。|  
|`HomeSite`|可选。 在远程服务器上，如果不包括安装包的位置。|  
|`CopyOnBuild`|可选。 指定引导程序生成时是否应将复制到磁盘的包文件。 默认值为 true。|  
|`PublicKey`|加密的包的证书签名者的公钥。 如果存在`HomeSite`为止使用; 否则为可选。|  
|`Hash`|可选。 包文件的 SHA1 哈希。 这用于在安装时验证该文件的完整性。 如果不能为相同的哈希计算从包文件，将不会安装包。|  
  
## <a name="example"></a>示例  
 下面的代码示例定义包[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可再发行组件包和依赖项，如 Windows Installer。  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<产品 > 元素](../deployment/product-element-bootstrapper.md)   
 [\<包 > 元素](../deployment/package-element-bootstrapper.md)   
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)