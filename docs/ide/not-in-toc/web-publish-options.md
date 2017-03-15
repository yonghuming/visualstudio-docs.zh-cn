---
title: "哪些发布选项适合我？ | Microsoft Docs"
ms.custom: 
ms.date: 1/31/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 85a7f3ef705d3b110ab0dc39d08d0cee235bf307
ms.openlocfilehash: 1ecb87d748a7770101bdf6e0ffe34250a36c97a8

---

# <a name="what-publishing-options-are-right-for-me"></a>哪些发布选项适合我？

在 Visual Studio 中，Web 应用程序可以直接发布到以下目标：

- [Azure 应用服务](#azure-app-service)
- [Azure 虚拟机](#azure-virtual-machines)
- [文件系统](#file-system)
- [自定义目标（如 IIS、FTP 等）](#custom-targets)，包括所有任意的 Web 服务器。

在“发布”选项卡上，可以选择现有发布配置文件、导入现有发布配置文件或使用此处所述的选项新建发布配置文件。 

## <a name="azure-app-service"></a>Azure 应用服务

[Azure 应用服务](https://azure.microsoft.com/documentation/articles/app-service-value-prop-what-is/)帮助开发人员快速创建各种可缩放的 Web 应用程序和服务，而无需维护基础结构。

尤其对于 Web 应用程序而言，应用服务就是一个用于 [*Web 应用*](https://azure.microsoft.com/en-us/documentation/articles/app-service-web-overview/)的容器，Web 应用的作用非常接近于传统的 Web 主机。 也就是说，Web 应用提供可以运行服务器端代码并使其可供 Internet 访问的必要计算资源。

用户可通过为包含的应用服务选择[定价层或计划](https://azure.microsoft.com/documentation/articles/azure-web-sites-web-hosting-plans-in-depth-overview/)来确定 Web 应用具有的计算能力。 而且不必更改定价层就能让多个 Web 应用（和其他应用类型）共享同一个应用服务。 例如，可以在同一个应用服务上同时托管开发、过渡和生产 Web 应用。 

应用服务在 Azure 的云托管虚拟机上运行，但这些虚拟机是为你而托管的。 应用服务中的每个 Web 应用均分配有一个唯一的 *.azurewebsites.net URL；除免费层以外的所有定价层还允许向站点分配自定义域名。  

### <a name="when-to-choose-azure-app-service"></a>何时选用 Azure 应用服务

- 希望部署可通过 Internet 访问的 Web 应用程序。
- 希望根据需求自动缩放 Web 应用程序，而无需重新部署。
- 不想维护服务器基础结构（包括所有软件更新）。
- 不需要在托管 Web 应用程序的服务器上进行任何计算机级别的自定义设置。


> 如果想在自己的数据中心或其他本地计算机中使用 Azure 应用服务，可以使用 [Azure 堆栈](https://azure.microsoft.com/overview/azure-stack/)来实现。


## <a name="azure-virtual-machines"></a>Azure 虚拟机

[Azure 虚拟机 (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) 可用于在云中创建和管理任意数量的计算资源。 通过负责 VM 上的所有软件和更新，你可以根据 Web 应用程序的需求尽可能地对这些 VM 进行自定义。 此外，还可以通过远程桌面直接访问服务器，只要需要，各服务器就会一直维持分配给它的 IP 地址。

缩放虚拟机上托管的 Web 应用程序时，需要根据需求起转额外的 VM，然后部署必要的软件。 利用这种额外的控制能力，可以在全球不同区域以不同方式进行缩放。 例如，如果应用程序要为多个地区办事处的员工提供服务，则可以根据这些地区的员工人数来缩放 VM，从而潜在地降低成本。 

有关其他信息，请参阅 Azure 应用服务、Azure 虚拟机以及可通过 Visual Studio 中的“自定义”选项设置为部署目标的其他 Azure 服务之间的[详细比较](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/)。

### <a name="when-to-choose-azure-app-virtual-machines"></a>何时选用 Azure 应用虚拟机

- 希望部署可通过 Internet 访问的 Web 应用程序，并能完全控制所分配 IP 地址的生存期。
- 需要在服务器上进行计算机级别的自定义设置，其中包括诸如专用数据库系统、特定网络配置、磁盘分区之类的附加软件。
- 希望精细地控制 Web 应用程序的缩放。
- 出于任何其他原因，需要直接访问托管应用程序的服务器。

> 如果想在自己的数据中心或其他本地计算机中使用 Azure 虚拟机，可以使用 [Azure 堆栈](https://azure.microsoft.com/overview/azure-stack/)来实现。


## <a name="file-system"></a>文件系统

部署到文件系统意味着只需将 Web 应用程序文件复制到你自己的计算机上的特定文件夹中。 这种部署方式最常用于测试目的，如果计算机还运行 Web 服务器，则可以通过这种方式将应用程序部署为供数量有限的人员使用。 如果目标文件夹在网络上共享，那么，通过部署到文件系统还能使 Web 应用程序文件可供其他人访问，这些人随后可将其部署到特定服务器。  

任何运行 Web 服务器的本地计算机都可以使应用程序能够通过 Internet 或 Intranet（取决于其配置方式和所连接的网络）访问。 （如果将计算机直接连接到 Internet，应特别小心，以免其受到外部安全威胁。）这些计算机由你管理，因此你可以完全控制软件和硬件配置。 

请注意，如果出于任何原因（如计算机访问权限）不能使用云服务，例如 Azure 应用服务或 Azure 虚拟机，可以在自己的数据中心使用 [Azure 堆栈](https://azure.microsoft.com/overview/azure-stack/)。 Azure 堆栈可用于通过 Azure 应用服务和 Azure 虚拟机来管理并使用计算资源，并且让所有资源仍然保留在本地。  

### <a name="when-to-choose-file-system-deployment"></a>何时选用文件系统部署

- 仅需要将应用程序部署到文件共享，其他人可从中将其部署到不同的服务器。
- 仅需要本地测试部署。
- 在将应用程序文件发送到另一个部署目标之前，想单独对文件进行检查并在必要时进行修改。



## <a name="custom-targets"></a>自定义目标

利用自定义目标，可以将 Web 应用程序部署到 Azure 应用服务、Azure 虚拟机或本地文件系统以外的目标。 它可以部署到你有权访问的文件系统或任何其他服务器（Internet 或 Intranet），包括其他云服务上的服务器。 它可以与 Web 部署（文件或 .ZIP）和 FTP 配合使用。 

如果选择自定义目标，Visual Studio 会提示输入配置文件名称，然后收集包括目标服务器或位置、站点名称和凭据在内的其他**连接**信息。 你还可以控制“设置”选项卡上的某些行为，例如要部署的配置，是否从目标中删除现有文件，是否在发布期间预编译，以及是否从部署中排除 App_Data 文件夹中的文件。 

可以在 Visual Studio 中创建任意数量的自定义部署配置文件，从而使得能够根据需要管理设置略有不同的配置文件。

### <a name="when-to-choose-custom-deployment"></a>何时选用自定义部署

- 在除 Azure 以外的可通过 URL 访问的提供程序上使用云服务。
- 希望用来进行部署的凭据不是在 Visual Studio 中所用的凭据或直接与 Azure 帐户相关联的凭据。
- 希望在每次部署时从目标中删除文件。 




<!--HONumber=Feb17_HO4-->


