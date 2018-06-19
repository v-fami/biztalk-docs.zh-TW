---
title: A4SWIFT 清理工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- A4SWIFT Cleanup tool
ms.assetid: e694f824-6097-4d60-bc7b-b4f1a40acea0
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b2d0e251bf5e8a4169ff0d86cc6635944ca12e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965596"
---
# <a name="a4swift-cleanup-tool"></a><span data-ttu-id="4c37d-102">A4SWIFT 清理工具</span><span class="sxs-lookup"><span data-stu-id="4c37d-102">A4SWIFT Cleanup Tool</span></span>
<span data-ttu-id="4c37d-103">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]清理工具可讓您準備伺服器具有[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]在其上安裝適用於新安裝的[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4c37d-103">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] cleanup tool enables you to prepare a server that has the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] installed on it for a new installation of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span> <span data-ttu-id="4c37d-104">此工具會移除 A4SWIFT 的成品，例如合約、 部門和商務規則引擎 (BRE) 原則，並解除部署組件。</span><span class="sxs-lookup"><span data-stu-id="4c37d-104">The tool removes A4SWIFT artifacts such as agreements, departments, and Business Rule Engine (BRE) policies, and undeploys assemblies.</span></span> <span data-ttu-id="4c37d-105">執行此工具可讓您避免手動移除許多 A4SWIFT 成品，以及解決問題的可能參考其他組件中解除部署組件。</span><span class="sxs-lookup"><span data-stu-id="4c37d-105">Running the tool enables you to avoid manually removing many A4SWIFT artifacts, and resolves problems with undeploying assemblies that might be referenced from other assemblies.</span></span>  
  
 <span data-ttu-id="4c37d-106">當您執行 「 清除 」 工具時，您可以選擇離開 A4SWIFT 的電腦 （預設值） 或解除安裝 A4SWIFT 安裝之後移除成品。</span><span class="sxs-lookup"><span data-stu-id="4c37d-106">When you run the cleanup tool, you have the choice of leaving A4SWIFT installed on the computer (the default), or uninstalling A4SWIFT after removing the artifacts.</span></span> <span data-ttu-id="4c37d-107">您應該執行此工具，然後再解除 A4SWIFT 安裝。</span><span class="sxs-lookup"><span data-stu-id="4c37d-107">You should run the tool before uninstalling A4SWIFT.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4c37d-108">請勿在生產環境中使用 A4SWIFT 清理工具。</span><span class="sxs-lookup"><span data-stu-id="4c37d-108">Do not use the A4SWIFT cleanup tool in a production environment.</span></span> <span data-ttu-id="4c37d-109">此工具是用於在單一伺服器開發環境中，不能在多伺服器部署。</span><span class="sxs-lookup"><span data-stu-id="4c37d-109">The tool is intended to be used in a single-server development environment, not in a multiserver deployment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c37d-110">根據預設，「 清理 」 工具不適用於英文的任何其他語言。</span><span class="sxs-lookup"><span data-stu-id="4c37d-110">By default, the cleanup tool does not work for any other language than English.</span></span> <span data-ttu-id="4c37d-111">不過，使 「 清理 」 工具可當地語系化的電腦上，您可以修改環境。</span><span class="sxs-lookup"><span data-stu-id="4c37d-111">You can, however, modify the environment so that the cleanup tool works on a localized computer.</span></span> <span data-ttu-id="4c37d-112">範本文件庫，例如，當地語系化的字串與 t 參數執行 FormPublish 工具**t:VorLagen**德文的環境中。</span><span class="sxs-lookup"><span data-stu-id="4c37d-112">Run the FormPublish tool with the t parameter and the localized string for the Templates document library, for example, **t:VorLagen** in a German environment.</span></span> <span data-ttu-id="4c37d-113">您接著可以當地語系化的環境中執行清理工具。</span><span class="sxs-lookup"><span data-stu-id="4c37d-113">You can then run the cleanup tool in a localized environment.</span></span>  
  
 <span data-ttu-id="4c37d-114">下列條件必須為要執行清除工具，則為 true:</span><span class="sxs-lookup"><span data-stu-id="4c37d-114">The following must be true for the cleanup tool to run:</span></span>  
  
-   <span data-ttu-id="4c37d-115">您必須是成員[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="4c37d-115">You must be a member the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators groups.</span></span>  
  
-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]<span data-ttu-id="4c37d-116">必須安裝在執行此工具的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="4c37d-116"> must be installed on the server on which you run the tool.</span></span>  
  
-   <span data-ttu-id="4c37d-117">MrsrConfiguration.dll、 Shared.dll，RuleEngineExtension.dll 必須部署和執行此工具的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="4c37d-117">MrsrConfiguration.dll, Shared.dll, and RuleEngineExtension.dll must be deployed on the server on which you run the tool.</span></span>  
  
## <a name="what-the-cleanup-tool-does"></a><span data-ttu-id="4c37d-118">[清理] 工具的用途</span><span class="sxs-lookup"><span data-stu-id="4c37d-118">What the cleanup tool does</span></span>  
 <span data-ttu-id="4c37d-119">A4SWIFT 清理工具會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="4c37d-119">The A4SWIFT cleanup tool performs the following operations:</span></span>  
  
-   <span data-ttu-id="4c37d-120">執行**BM 解除部署**ForActivities.xml 和 MRSRBAM.xml</span><span class="sxs-lookup"><span data-stu-id="4c37d-120">Runs **BM Undeploy** against ForActivities.xml and MRSRBAM.xml</span></span>  
  
-   <span data-ttu-id="4c37d-121">FrrActivities_ConnectionStrings.xml 和 MRSRActivities_ConnectionStrings.xml 檔案移除，如果有的話</span><span class="sxs-lookup"><span data-stu-id="4c37d-121">Removes the FrrActivities_ConnectionStrings.xml and MRSRActivities_ConnectionStrings.xml files, if they exist</span></span>  
  
-   <span data-ttu-id="4c37d-122">如果存在的話，移除 A4SWIFT 2.1 (如果您已升級伺服器[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，但安裝程式已離開 A4SWIFT 2.1 安裝)，並刪除 A4SWIFT 2.1 資料夾</span><span class="sxs-lookup"><span data-stu-id="4c37d-122">Removes A4SWIFT 2.1 if it exists (if you have upgraded the server to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], but Setup has left A4SWIFT 2.1 installed) and deletes the A4SWIFT 2.1 folder</span></span>  
  
-   <span data-ttu-id="4c37d-123">解除部署所有 A4SWIFT 組件</span><span class="sxs-lookup"><span data-stu-id="4c37d-123">Undeploys all A4SWIFT assemblies</span></span>  
  
-   <span data-ttu-id="4c37d-124">刪除 A4SWIFT 系統管理員群組和 A4SWIFT Users 群組</span><span class="sxs-lookup"><span data-stu-id="4c37d-124">Deletes the A4SWIFT Administrator group and the A4SWIFT Users group</span></span>  
  
-   <span data-ttu-id="4c37d-125">刪除 A4SWIFT 資料庫</span><span class="sxs-lookup"><span data-stu-id="4c37d-125">Deletes the A4SWIFT database</span></span>  
  
-   <span data-ttu-id="4c37d-126">刪除 A4SWIFT 虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="4c37d-126">Deletes the A4SWIFT virtual directory</span></span>  
  
-   <span data-ttu-id="4c37d-127">執行完整無訊息解除安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]並刪除[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]資料夾 （如果已選取）</span><span class="sxs-lookup"><span data-stu-id="4c37d-127">Runs a complete silent uninstall of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] and deletes the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] folder (if selected)</span></span>  
  
 <span data-ttu-id="4c37d-128">因為它會移除成品，並解除部署組件，清理工具也會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="4c37d-128">As it removes artifacts and undeploys assemblies, the cleanup tool also does the following:</span></span>  
  
-   <span data-ttu-id="4c37d-129">啟動 Internet Information Services (IIS) 管理服務，才能執行</span><span class="sxs-lookup"><span data-stu-id="4c37d-129">Starts Internet Information Services (IIS) Admin Service in order to run</span></span>  
  
-   <span data-ttu-id="4c37d-130">停止並重新啟動 MSSQLSERVER、 SQLSERVERAGENT、 BizTalk 和企業單一登入服務</span><span class="sxs-lookup"><span data-stu-id="4c37d-130">Stops and then restarts the MSSQLSERVER, SQLSERVERAGENT, BizTalk, and Enterprise Single Sign-On services</span></span>  
  
#### <a name="to-run-the-a4swift-cleanup-tool"></a><span data-ttu-id="4c37d-131">若要執行 A4SWIFT 清理工具</span><span class="sxs-lookup"><span data-stu-id="4c37d-131">To run the A4SWIFT cleanup tool</span></span>  
  
1.  <span data-ttu-id="4c37d-132">在之前執行 A4SWIFT 清理工具，解除部署任何 A4SWIFT 預設組件是指任何專案。</span><span class="sxs-lookup"><span data-stu-id="4c37d-132">Prior to running the A4SWIFT cleanup tool, undeploy any project that refers to any of the A4SWIFT default assemblies.</span></span>  
  
2.  <span data-ttu-id="4c37d-133">開啟命令提示字元並移至\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools。</span><span class="sxs-lookup"><span data-stu-id="4c37d-133">Open a command prompt and move to \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools.</span></span>  
  
3.  <span data-ttu-id="4c37d-134">型別**A4SWIFTCleanupTool.exe** ，然後按**ENTER**。</span><span class="sxs-lookup"><span data-stu-id="4c37d-134">Type **A4SWIFTCleanupTool.exe** and then press **ENTER**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4c37d-135">當您一開始執行 A4SWIFTCleanupTool.exe 時，此工具會顯示說明畫面，並會提示您輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="4c37d-135">When you initially run A4SWIFTCleanupTool.exe, the tool displays a help screen, and prompts you to enter a parameter.</span></span> <span data-ttu-id="4c37d-136">在您輸入的參數之前，不會執行此工具。</span><span class="sxs-lookup"><span data-stu-id="4c37d-136">The tool will not run until you enter the parameter.</span></span>  
  
4.  <span data-ttu-id="4c37d-137">您希望該工具来採取的動作而定，按下列機碼，然後再按**ENTER**:</span><span class="sxs-lookup"><span data-stu-id="4c37d-137">Depending upon the actions that you want the tool to take, press one of the following keys, and then press **ENTER**:</span></span>  
  
    -   <span data-ttu-id="4c37d-138">**0**的任何動作 （預設值）</span><span class="sxs-lookup"><span data-stu-id="4c37d-138">**0** for no actions taken (the default)</span></span>  
  
    -   <span data-ttu-id="4c37d-139">**1**移除所有本機 A4SWIFT 電腦上的資源，包括虛擬目錄和登錄設定</span><span class="sxs-lookup"><span data-stu-id="4c37d-139">**1** to remove all the local A4SWIFT resources on the computer, including the virtual directory and registry settings</span></span>  
  
    -   <span data-ttu-id="4c37d-140">**2**移除所有 BizTalk Server 群組，包括 Sharepoint Web 資料夾、 FIN 訊息範本、 BRE 原則和詞彙、 BizTalk 成品和 A4SWIFT 資料庫上的共用的 A4SWIFT 資源</span><span class="sxs-lookup"><span data-stu-id="4c37d-140">**2** to remove all the shared A4SWIFT resources on the BizTalk Server group, including Sharepoint Web folders, FIN message templates, BRE policies and vocabularies, BizTalk artifacts, and the A4SWIFT database</span></span>  
  
    -   <span data-ttu-id="4c37d-141">**3**移除所有本機和共用資源</span><span class="sxs-lookup"><span data-stu-id="4c37d-141">**3** to remove all the local and shared resources</span></span>  
  
    -   <span data-ttu-id="4c37d-142">**4**來移除所有本機和共用資源和解除安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]產品。</span><span class="sxs-lookup"><span data-stu-id="4c37d-142">**4** to remove all the local and shared resources and uninstall the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] product.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c37d-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c37d-143">See Also</span></span>  
 [<span data-ttu-id="4c37d-144">工具</span><span class="sxs-lookup"><span data-stu-id="4c37d-144">Tools</span></span>](../../adapters-and-accelerators/accelerator-swift/tools.md)