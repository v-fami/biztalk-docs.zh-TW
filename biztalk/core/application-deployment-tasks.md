---
title: "應用程式部署工作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, deploying
- applications, tasks
- deploying [applications], tasks
ms.assetid: 8cb29292-9868-41fa-9f2c-d1c20dfdddbb
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed5dd5b2a15bd8408ee11934d7dd6274e81651b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="application-deployment-tasks"></a><span data-ttu-id="d6c79-102">應用程式部署工作</span><span class="sxs-lookup"><span data-stu-id="d6c79-102">Application Deployment Tasks</span></span>
<span data-ttu-id="d6c79-103">本節中的主題提供了下列與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式部署程序的每一個階段有關之工作的詳細資料：</span><span class="sxs-lookup"><span data-stu-id="d6c79-103">The topics in this section provide details about the following tasks involved in each phase of the application deployment process for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:</span></span>  
  
1.  <span data-ttu-id="d6c79-104">**開發。**</span><span class="sxs-lookup"><span data-stu-id="d6c79-104">**Development.**</span></span> <span data-ttu-id="d6c79-105">開發人員要從 BizTalk 應用程式中包含的 BizTalk 組件部署[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]開發電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="d6c79-105">The developer deploys the BizTalk assemblies that are to be included in the BizTalk application from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] running on the development computer.</span></span> <span data-ttu-id="d6c79-106">這樣會自動建立應用程式，並將組件中所包含的成品填入其中。</span><span class="sxs-lookup"><span data-stu-id="d6c79-106">This automatically creates the application and populates it with the artifacts contained in the assemblies.</span></span> <span data-ttu-id="d6c79-107">成品是指組成 BizTalk 商務解決方案的所有項目，包括 BizTalk 組件、.NET 組件、結構描述、對應、繫結、憑證等等。</span><span class="sxs-lookup"><span data-stu-id="d6c79-107">Artifacts are all of the items that comprise a BizTalk business solution, including BizTalk assemblies, .NET assemblies, schemas, maps, bindings, certificates, and so forth.</span></span> <span data-ttu-id="d6c79-108">開發人員會在應用程式中加入任何其他的成品或是執行其他組態工作，即可完成應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="d6c79-108">The developer completes the application by adding any additional artifacts to it or performing additional configuration.</span></span> <span data-ttu-id="d6c79-109">然後，開發人員會從 .msi 檔案安裝此應用程式、測試它來驗證功能、修正任何問題，然後從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將此應用程式匯出為 .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="d6c79-109">The developer then installs the application from the .msi file, tests it to verify functionality, fixes any issues, and then exports the application from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as an .msi file.</span></span>  
  
2.  <span data-ttu-id="d6c79-110">**測試。**</span><span class="sxs-lookup"><span data-stu-id="d6c79-110">**Testing.**</span></span> <span data-ttu-id="d6c79-111">測試人員會將.msi 檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上執行測試，這樣會建立在應用程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d6c79-111">The tester imports the .msi file into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] running on a test computer, which creates the application in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d6c79-112">測試人員也會在主控件電腦上從 .msi 檔案安裝此應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6c79-112">The tester also installs the application on the host computers from the .msi file.</span></span> <span data-ttu-id="d6c79-113">當測試及 BUG 修正完畢後，測試人員會從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將此應用程式匯出為 .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="d6c79-113">After testing and bug-fixing is complete, the tester exports the application from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as an .msi file.</span></span>  
  
3.  <span data-ttu-id="d6c79-114">**預備環境。**</span><span class="sxs-lookup"><span data-stu-id="d6c79-114">**Staging.**</span></span> <span data-ttu-id="d6c79-115">IT 系統管理員會將.msi 檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]臨時伺服器上所執行的生產環境中設定它、 將它安裝在主機電腦上、 驗證其功能，然後將完成的應用程式匯出為.msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="d6c79-115">The IT administrator imports the .msi file into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] running on a staging server, configures it for the production environment, installs it on host computers, verifies the functionality, and then exports the finished application as an .msi file.</span></span>  
  
4.  <span data-ttu-id="d6c79-116">**生產環境。**</span><span class="sxs-lookup"><span data-stu-id="d6c79-116">**Production.**</span></span> <span data-ttu-id="d6c79-117">IT 系統管理員會將.msi 檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行在實際執行環境中，主機電腦上安裝應用程式，然後啟動 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6c79-117">The IT administrator imports the .msi file into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] running in a production environment, installs the application on the host computers, and then starts the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6c79-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="d6c79-118">In This Section</span></span>  
  
-   [<span data-ttu-id="d6c79-119">BizTalk 應用程式部署的開發工作</span><span class="sxs-lookup"><span data-stu-id="d6c79-119">Development Tasks for BizTalk Application Deployment</span></span>](../core/development-tasks-for-biztalk-application-deployment.md)  
  
-   [<span data-ttu-id="d6c79-120">BizTalk 應用程式部署的測試工作</span><span class="sxs-lookup"><span data-stu-id="d6c79-120">Testing Tasks for BizTalk Application Deployment</span></span>](../core/testing-tasks-for-biztalk-application-deployment.md)  
  
-   [<span data-ttu-id="d6c79-121">BizTalk 應用程式部署的預備工作</span><span class="sxs-lookup"><span data-stu-id="d6c79-121">Staging Tasks for BizTalk Application Deployment</span></span>](../core/staging-tasks-for-biztalk-application-deployment.md)  
  
-   [<span data-ttu-id="d6c79-122">BizTalk 應用程式部署的實際執行工作</span><span class="sxs-lookup"><span data-stu-id="d6c79-122">Production Tasks for BizTalk Application Deployment</span></span>](../core/production-tasks-for-biztalk-application-deployment.md)