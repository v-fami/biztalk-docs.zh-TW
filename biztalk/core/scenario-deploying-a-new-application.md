---
title: "案例： 將新的應用程式部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, applications
- applications, deploying
- deploying [applications], examples
- applications, examples
- examples, deploying
ms.assetid: 6d34a626-9fd4-4c33-a067-b66333eec01f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 938767237d21b74829c786bdd5d57c7d9df15c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-deploying-a-new-application"></a><span data-ttu-id="31aac-102">案例： 部署新的應用程式</span><span class="sxs-lookup"><span data-stu-id="31aac-102">Scenario: Deploying a New Application</span></span>
<span data-ttu-id="31aac-103">本主題說明將應用程式部署至從未部署之新環境的實例，例如，將執行環境中設定的應用程式部署至實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="31aac-103">This topic describes the scenario of deploying an application into a new environment where it has not been deployed before; for example, deploying an application that has been configured in a staging environment into a production environment.</span></span>  
  
 <span data-ttu-id="31aac-104">中所述[應用程式部署程序](../core/the-application-deployment-process.md)，當您想要將應用程式從一個環境移到另一個，匯出至.msi 檔案的應用程式。</span><span class="sxs-lookup"><span data-stu-id="31aac-104">As described in [The Application Deployment Process](../core/the-application-deployment-process.md), when you want to move an application from one environment to another, you export the application into an .msi file.</span></span> <span data-ttu-id="31aac-105">接著將 .msi 檔案匯入至新環境的 BizTalk 群組中。</span><span class="sxs-lookup"><span data-stu-id="31aac-105">You then import the .msi file into the BizTalk group in the new environment.</span></span> <span data-ttu-id="31aac-106">您也可以在該群組中將會執行應用程式的電腦中安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="31aac-106">You also install the application on the computers in that group that will run the application.</span></span> <span data-ttu-id="31aac-107">您必須先將應用程式安裝在即將執行的每部電腦中，並且啟動應用程式，應用程式才能開始運作。</span><span class="sxs-lookup"><span data-stu-id="31aac-107">Before it can begin functioning, you must install the application on each computer that will run it and also start the application.</span></span>  
  
 <span data-ttu-id="31aac-108">在下列圖表中，Application1 會從 .msi 檔案匯入至 BizTalk 群組 B。</span><span class="sxs-lookup"><span data-stu-id="31aac-108">In the following diagram, Application1 is imported from an .msi file into BizTalk Group B.</span></span>  
  
 <span data-ttu-id="31aac-109">![BizTalk 應用程式部署](../core/media/deployapplication.gif "DeployApplication")</span><span class="sxs-lookup"><span data-stu-id="31aac-109">![Deploying a BizTalk application](../core/media/deployapplication.gif "DeployApplication")</span></span>  
  
 <span data-ttu-id="31aac-110">這會將成品匯入至各種 BizTalk Server 資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="31aac-110">This imports artifacts into the various BizTalk Server databases as follows:</span></span>  
  
-   <span data-ttu-id="31aac-111">BizTalk 組件、.NET 組件、繫結、繫結檔案、BAM 範本、COM 元件、憑證和文字檔案都會加入 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="31aac-111">The BizTalk assembly, .NET assembly, bindings, binding file, BAM template, COM component, certificate, and text file are all added to the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="31aac-112">原則和詞彙會加入至「規則引擎」資料庫。</span><span class="sxs-lookup"><span data-stu-id="31aac-112">The policy and vocabulary are added to the Rule Engine database.</span></span>  
  
-   <span data-ttu-id="31aac-113">BAM 範本和 BAM 定義檔案都會加入至「BAM 主要匯入」資料庫。</span><span class="sxs-lookup"><span data-stu-id="31aac-113">The BAM template and BAM definition file are both added to the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="31aac-114">每個成品也會與 BizTalk 管理資料庫的 Application1 相關聯。</span><span class="sxs-lookup"><span data-stu-id="31aac-114">Each of these artifacts is also associated with Application1 in the BizTalk Management database.</span></span>  
  
 <span data-ttu-id="31aac-115">此應用程式也會在本機電腦中從 .msi 檔案進行安裝。</span><span class="sxs-lookup"><span data-stu-id="31aac-115">The application is also installed on a local computer from the .msi file.</span></span> <span data-ttu-id="31aac-116">這會安裝 .msi 檔案中包含的各種成品，如下所示：</span><span class="sxs-lookup"><span data-stu-id="31aac-116">This installs various artifacts that are included in the .msi file, as follows:</span></span>  
  
-   <span data-ttu-id="31aac-117">在 Internet Information Services (IIS) Metabase 中建立名為 VirtualDirectory 的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="31aac-117">The virtual directory, named VirtualDirectory, is created in the Internet Information Services (IIS) metabase.</span></span>  
  
-   <span data-ttu-id="31aac-118">憑證會加入至本機憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="31aac-118">The certificate is added to the local certificate store.</span></span>  
  
-   <span data-ttu-id="31aac-119">文字檔案和 COM 元件會複製到本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="31aac-119">The text file and COM component are copied to the local file system.</span></span>  
  
-   <span data-ttu-id="31aac-120">BizTalk 組件和 .NET 組件會加入至全域組件快取 (GAC) 中 (如果已針對這些組件選取這個部署選項)。</span><span class="sxs-lookup"><span data-stu-id="31aac-120">The BizTalk assembly and .NET assembly are added to the global assembly cache (GAC), if this deployment option was selected for them.</span></span>  
  
-   <span data-ttu-id="31aac-121">.NET 組件和 COM 元件會加入至 Windows 登錄中 (如果已針對這些組件和元件選取這個部署選項)。</span><span class="sxs-lookup"><span data-stu-id="31aac-121">The .NET assembly and COM component are added to the Windows registry, if that deployment option was selected for them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31aac-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31aac-122">See Also</span></span>  
 <span data-ttu-id="31aac-123">[應用程式部署和管理案例](../core/application-deployment-and-management-scenarios.md) </span><span class="sxs-lookup"><span data-stu-id="31aac-123">[Application Deployment and Management Scenarios](../core/application-deployment-and-management-scenarios.md) </span></span>  
 [<span data-ttu-id="31aac-124">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="31aac-124">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)