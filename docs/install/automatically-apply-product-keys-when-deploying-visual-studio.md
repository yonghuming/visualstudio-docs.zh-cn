---
title: "在部署 Visual Studio 时自动应用产品密钥 | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 493ea235a3d89a04a4c6accfa491e622792e4397
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>在部署 Visual Studio 时自动应用产品密钥
你可以采用编程方式将你的产品密钥作为用于自动化 Visual Studio 的部署的脚本的一部分应用。 在安装 Visual Studio 期间或安装已完成后，产品密钥可以以编程方式在设备上设置。

## <a name="apply-the-license-after-installation"></a>安装完成后应用许可证
 可以在静默模式下在目标计算机上使用 `StorePID.exe` 实用工具，从而使用产品密钥激活 Visual Studio 的已安装版本。 `StorePID.exe` 是在以下默认位置随 Visual Studio 2017 一起安装的实用工具程序： <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 通过提升的权限（使用系统中心代理或提升的命令提示符）运行 `StorePID.exe`，后跟产品密钥（包含短划线）和 Microsoft 产品代码 (MPC)。 请务必在产品密钥中添加短划线。

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 下面展示了用于应用 Visual Studio 2017 Enterprise 许可证（其中 MPC 为 08860，产品密钥为 `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`）的示例命令行（假设是在默认位置上安装）：

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 下表列出了 Visual Studio 的每个版本的 MPC 代码：

| Visual Studio 版本                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

如果 `StorePID.exe` 成功应用产品密钥，则会返回值为 0 的 `%ERRORLEVEL%`。 如果遇到错误，则会返回代码，具体视错误条件而定：

| 错误                     | 代码 |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="see-also"></a>另请参阅
 * [安装 Visual Studio](../install/install-visual-studio.md)
 * [创建 Visual Studio 的脱机安装](../install/create-an-offline-installation-of-visual-studio.md)

