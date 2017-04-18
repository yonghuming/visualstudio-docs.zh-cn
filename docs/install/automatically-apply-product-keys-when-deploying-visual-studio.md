---
title: "在部署 Visual Studio 时自动应用产品密钥 | Microsoft Docs"
ms.custom: 
ms.date: 3/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: 36a774583f5125ecc09210c9ad5da15ec800f870
ms.lasthandoff: 04/03/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>在部署 Visual Studio 时自动应用产品密钥
你可以采用编程方式将你的产品密钥作为用于自动化 Visual Studio 的部署的脚本的一部分应用。 在安装 Visual Studio 期间或安装已完成后，产品密钥可以以编程方式在设备上设置。  

## <a name="apply-the-license-during-installation"></a>在安装过程中应用许可证  
 使用 `--productKey` 参数可在 Visual Studio 的安装过程中应用产品密钥。 此安装程序参数可与 `--quiet parameter` 结合使用，为最终用户安装处于已授权状态的 Visual Studio。 若要使用 `--productKey` 参数，请打开命令提示符。 运行安装程序（例如，vs_enterprise.exe 或 vs_professional.exe），然后使用带或不带短划线的产品密钥（25 个字符）设置 `--productKey` 参数：  

 这是使用产品密钥 AAAAABBBBBCCCCCDDDDDEEEEEEE 安装 Visual Studio 2015 Enterprise 的示例命令：  

 `vs_enterprise.exe [any other setup parameters] --productKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  

## <a name="apply-the-license-after-installation"></a>安装完成后应用许可证  
 可以通过在无提示模式下使用目标计算机上的 storePID.exe 实用工具来使用产品密钥激活 Visual Studio 的已安装版本。 StorePID.exe 是随 Visual Studio 安装于 **\<drive>:\\\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe** 的实用程序。  

 通过使用“系统中心”代理或提升的命令提示符，后跟产品密钥（包含短划线）和 Microsoft 产品代码 (MPC)，运行具有提升的权限的 storePID.exe。 请务必在产品密钥中包括短划线！  

 `StorePID.exe [product key including the dashes] [MPC]`  

 这是用于安装 Visual Studio 2017 Enterprise 的示例命令行，具有 08860 的 MPC 和 产品密钥“AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE”：  

 `C:\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860`  

 下表列出了 Visual Studio 的每个版本的 MPC 代码：  

|Visual Studio 版本 | MPC |  
|---------------------------|---------|
|Visual Studio Enterprise 2017|08860|  
|Visual Studio Professional 2017|08862|  
|Visual Studio Test Professional 2017|08866|
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  

如果 StorePID.exe 成功应用产品密钥，则它将返回 0。 如果遇到错误，它将返回 1 到 6 之间的一个数字。  

## <a name="see-also"></a>另请参阅  
 * [安装 Visual Studio](../install/install-visual-studio.md)
 * [创建 Visual Studio 的脱机安装](../install/create-an-offline-installation-of-visual-studio.md)

