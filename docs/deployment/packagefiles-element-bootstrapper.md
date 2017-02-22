---
title: "&lt;PackageFiles&gt; 元素（引导程序） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "<PackageFiles> 元素 [引导程序]"
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;PackageFiles&gt; 元素（引导程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`PackageFiles` 元素包含 `PackageFile` 元素，后者定义作为 `Command` 元素的结果执行的安装包。  
  
## 语法  
  
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
  
## 元素和特性  
 `PackageFiles` 元素具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`CopyAllPackageFiles`|可选。  如果设置为 `false`，安装程序将仅下载从 `Command` 元素引用的文件。  如果设置为 `true`，则将下载所有文件。<br /><br /> 如果设置为 `IfNotHomesite`，则在 `ComponentsLocation` 设置为 `HomeSite` 的情况下，安装程序的行为将与设置为 `False` 的行为相同，其他情况下，安装程序的行为将与设置为 `True` 的行为相同。  此设置对于允许自身为引导程序的程序包在 HomeSite 方案中执行自己的行为是非常有用的。<br /><br /> 默认值为 `true`。|  
  
## PackageFile  
 `PackageFile` 元素是 `PackageFiles` 元素的子元素。  `PackageFiles` 元素必须至少有一个 `PackageFile` 元素。  
  
 `PackageFile` 具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Name`|必选。  包文件的名称。  这是 `Command` 元素在定义包的安装条件时将引用的名称。  该值还可以用作 `Strings` 表中的键，以检索工具（例如 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]）将用来描述包的本地化名称。|  
|`HomeSite`|可选。  远程服务器上的包的位置（如果安装程序不附带该包）。|  
|`CopyOnBuild`|可选。  指定在生成时，引导程序是否应将包文件复制到磁盘上。  默认值为 true。|  
|`PublicKey`|包的证书签名者的加密公钥。  如果使用了 `HomeSite`，此特性是必需的；否则，是可选的。|  
|`Hash`|可选。  包文件的一个 SHA1 哈希。  用于在安装时验证文件的完整性。  如果无法从包文件计算相同的哈希，则不会安装此包。|  
  
## 示例  
 下面的代码示例为 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 可再发行组件包及其依赖项（例如 Windows Installer）定义了各种包。  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## 请参阅  
 [\<Product\> 元素](../deployment/product-element-bootstrapper.md)   
 [\<Package\> 元素](../deployment/package-element-bootstrapper.md)   
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)