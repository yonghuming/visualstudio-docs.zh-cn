---
title: "在防火墙或代理服务器后安装 Visual Studio | Microsoft Docs"
description: 
ms.custom: 
ms.date: 08/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 1e017806ca7bf3d23410ba3a2f999dca0b78f240
ms.openlocfilehash: cb2ef641cb5b9b6efbd1aeb539154da1e4082b51
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>在防火墙或代理服务器后安装 Visual Studio

Visual Studio 安装程序从各种域及其下载服务器下载文件。 此页列出了你希望在部署脚本中作为受信任的项列入“白名单”的域 URL。

如果适用于环境，请考虑添加同时使用 HTTP 和 HTTPS 协议的以下域。

## <a name="microsoft-domains"></a>Microsoft 域
| Domain | 用途 |
| ------ | ------- |
| go.microsoft.com | 安装程序 URL 解析 |
| aka.ms | 安装程序 URL 解析 |
| download.visualstudio.microsoft.com | 安装包下载位置 |
| download.microsoft.com | 安装包下载位置 |
| download.visualstudio.com | 安装包下载位置 |
| dl.xamarin.com | 安装包下载位置 |
| visualstudiogallery.msdn.microsoft.com | Visual Studio 扩展下载位置 |
| www.visualstudio.com | 文档位置 |
| docs.microsoft.com | 文档位置 |
| msdn.microsoft.com | 文档位置 |
| www.microsoft.com | 文档位置 |
| *.windows.net | 登录位置 |
| *.microsoftonline.com | 登录位置 |
| *.live.com | 登录位置 |


## <a name="non-microsoft-domains"></a>非 Microsoft 域
| Domain | 安装这些工作负载 |
| ------ | ------- |
| archive.apache.org |  使用 JavaScript 的移动开发 <br />(Cordova) |
| cocos2d-x.org | 使用 C++ 的游戏开发 <br />(Cocos) |
| download.epicgames.com | 使用 C++ 的游戏开发 <br />(Unreal Engine) |
| download.oracle.com | 使用 JavaScript 的移动开发 <br />(Java SDK) <br /><br />使用 .NET 的移动开发 <br />(Java SDK) |
| download.unity3d.com | 使用 Unity 的游戏开发 <br />(Unity) |
| netstorage.unity3d.com | 使用 Unity 的游戏开发 <br /> (Unity) |
| dl.google.com | 使用 JavaScript 的移动开发 <br />（Android SDK 和 NDK，仿真器） <br /><br />使用 .NET 的移动开发 <br />（Android SDK 和 NDK，仿真器） |
| www.incredibuild.com | 使用 C++ 的游戏开发 <br />(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | 使用 C++ 的游戏开发 <br />(IncrediBuild) |
| www.python.org | Python 开发 <br />(Python) <br /><br />数据科学和分析应用程序 <br />(Python) |

## <a name="see-also"></a>另请参阅
* [安装 Visual Studio 2017](install-visual-studio.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
  * [使用命令行参数安装 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
    * [命令行参数示例](command-line-parameter-examples.md)
    * [工作负载和组件 ID 参考](workload-and-component-ids.md)
  * [创建基于网络的 Visual Studio 安装](create-a-network-installation-of-visual-studio.md)
    * [在脱机环境中安装 Visual Studio 的特别注意事项](install-visual-studio-in-offline-environment.md)
  * [通过响应文件自动执行 Visual Studio](automated-installation-with-response-file.md)
  * [在部署 Visual Studio 时自动应用产品密钥](automatically-apply-product-keys-when-deploying-visual-studio.md)
  * [为 Visual Studio 企业部署设置默认值](set-defaults-for-enterprise-deployments.md)
  * [禁用或移动包缓存](disable-or-move-the-package-cache.md)
  * [更新基于网络的 Visual Studio 安装](update-a-network-installation-of-visual-studio.md)
  * [控制 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
  * [用于检测和管理 Visual Studio 实例的工具](tools-for-managing-visual-studio-instances.md)
  * [报告 Visual Studio 2017 的问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

