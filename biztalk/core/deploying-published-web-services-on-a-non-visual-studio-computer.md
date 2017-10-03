---
title: "部署已發佈 Web 服務，在非 Visual Studio 電腦上的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- deploying, Web services
- Web services, planning
- Web services, deploying
ms.assetid: e9f8e801-21f3-4458-b05c-206b72868916
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad894c257bdd2eed6462b63c0e921f78ca13c17e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-published-web-services-on-a-non-visual-studio-computer"></a><span data-ttu-id="43640-102">在非 Visual Studio 電腦上部署已發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="43640-102">Deploying Published Web Services on a Non-Visual Studio Computer</span></span>
<span data-ttu-id="43640-103">若要將已發佈的 Web 服務部署到沒有安裝 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的電腦，您需要建立 Web 安裝專案、散發 Web 安裝套件 (.msi 檔案)、將套件安裝在非 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 電腦上，並設定所安裝的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="43640-103">To deploy your published Web service on a computer that does not have [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] installed, you need to create a Web setup project, distribute the Web setup package (.msi file), install the package on the non-[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] computer, and configure the installed Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43640-104">您也可以使用 BizTalk Server 管理主控台來建立 MSI 檔案，這類檔案可封裝包含有已發佈之 Web 服務專案的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="43640-104">You can also use BizTalk Server Administration Console to create MSI files packaging BizTalk Applications containing the published Web service projects.</span></span> <span data-ttu-id="43640-105">這個 MSI 檔案可以用來在非 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 電腦上部署 Web 服務專案。</span><span class="sxs-lookup"><span data-stu-id="43640-105">This MSI files can be used to deploy the Web service projects on a Non [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Computer.</span></span> <span data-ttu-id="43640-106">如需如何使用 BizTalk Server 管理主控台建立 MSI 檔案的詳細資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="43640-106">For more information about how to create MSI files using BizTalk Server Administration console, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43640-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="43640-107">In This Section</span></span>  
  
-   [<span data-ttu-id="43640-108">如何為您的已發佈的 Web 服務建立 Web 安裝程式</span><span class="sxs-lookup"><span data-stu-id="43640-108">How to Create a Web Setup for Your Published Web Service</span></span>](../core/how-to-create-a-web-setup-for-your-published-web-service.md)  
  
-   [<span data-ttu-id="43640-109">如何發佈 Web 安裝套件</span><span class="sxs-lookup"><span data-stu-id="43640-109">How to Distribute the Web Setup Package</span></span>](../core/how-to-distribute-the-web-setup-package.md)  
  
-   [<span data-ttu-id="43640-110">如何安裝 Web 安裝套件</span><span class="sxs-lookup"><span data-stu-id="43640-110">How to Install the Web Setup Package</span></span>](../core/how-to-install-the-web-setup-package.md)  
  
-   [<span data-ttu-id="43640-111">如何設定已安裝的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="43640-111">How to Configure the Installed Web Service</span></span>](../core/how-to-configure-the-installed-web-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="43640-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43640-112">See Also</span></span>  
 [<span data-ttu-id="43640-113">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="43640-113">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)