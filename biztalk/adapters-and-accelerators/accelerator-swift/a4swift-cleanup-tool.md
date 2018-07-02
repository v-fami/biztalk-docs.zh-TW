---
title: A4SWIFT 清理工具 |Microsoft Docs
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
ms.openlocfilehash: db6e9f6f6ec25762abc4416bc18f0955055b7e70
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983615"
---
# <a name="a4swift-cleanup-tool"></a><span data-ttu-id="2a15b-102">A4SWIFT 清理工具</span><span class="sxs-lookup"><span data-stu-id="2a15b-102">A4SWIFT Cleanup Tool</span></span>
<span data-ttu-id="2a15b-103">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]清理工具可讓您準備具有 Microsoft 的伺服器[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]新安裝在其上安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a15b-103">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] cleanup tool enables you to prepare a server that has the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] installed on it for a new installation of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span> <span data-ttu-id="2a15b-104">此工具會移除 A4SWIFT 成品，例如合約、 部門及商務規則引擎 (BRE) 原則，並解除部署組件。</span><span class="sxs-lookup"><span data-stu-id="2a15b-104">The tool removes A4SWIFT artifacts such as agreements, departments, and Business Rule Engine (BRE) policies, and undeploys assemblies.</span></span> <span data-ttu-id="2a15b-105">執行此工具可讓您避免以手動方式移除許多 A4SWIFT 成品，並解決可能與其他組件參考的解除部署組件的問題。</span><span class="sxs-lookup"><span data-stu-id="2a15b-105">Running the tool enables you to avoid manually removing many A4SWIFT artifacts, and resolves problems with undeploying assemblies that might be referenced from other assemblies.</span></span>  
  
 <span data-ttu-id="2a15b-106">當您執行清理工具時，您可以選擇離開 A4SWIFT 安裝在電腦 （預設值） 或解除安裝 A4SWIFT 之後移除成品。</span><span class="sxs-lookup"><span data-stu-id="2a15b-106">When you run the cleanup tool, you have the choice of leaving A4SWIFT installed on the computer (the default), or uninstalling A4SWIFT after removing the artifacts.</span></span> <span data-ttu-id="2a15b-107">您應該執行此工具，然後再解除 A4SWIFT 安裝。</span><span class="sxs-lookup"><span data-stu-id="2a15b-107">You should run the tool before uninstalling A4SWIFT.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2a15b-108">請勿在生產環境中使用 A4SWIFT 清理工具。</span><span class="sxs-lookup"><span data-stu-id="2a15b-108">Do not use the A4SWIFT cleanup tool in a production environment.</span></span> <span data-ttu-id="2a15b-109">此工具是用於在單一伺服器的開發環境中，不會在多伺服器部署。</span><span class="sxs-lookup"><span data-stu-id="2a15b-109">The tool is intended to be used in a single-server development environment, not in a multiserver deployment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a15b-110">根據預設，清理工具不適用於其他任何語言比英文。</span><span class="sxs-lookup"><span data-stu-id="2a15b-110">By default, the cleanup tool does not work for any other language than English.</span></span> <span data-ttu-id="2a15b-111">使清理工具可當地語系化的電腦上，不過，可以修改環境。</span><span class="sxs-lookup"><span data-stu-id="2a15b-111">You can, however, modify the environment so that the cleanup tool works on a localized computer.</span></span> <span data-ttu-id="2a15b-112">範本文件庫，例如，當地語系化的字串與 t 參數執行 FormPublish 工具**t:VorLagen**德文的環境中。</span><span class="sxs-lookup"><span data-stu-id="2a15b-112">Run the FormPublish tool with the t parameter and the localized string for the Templates document library, for example, **t:VorLagen** in a German environment.</span></span> <span data-ttu-id="2a15b-113">您接著可以在當地語系化的環境中執行清理工具。</span><span class="sxs-lookup"><span data-stu-id="2a15b-113">You can then run the cleanup tool in a localized environment.</span></span>  
  
 <span data-ttu-id="2a15b-114">下列條件必須為要執行清除工具，則為 true:</span><span class="sxs-lookup"><span data-stu-id="2a15b-114">The following must be true for the cleanup tool to run:</span></span>  
  
- <span data-ttu-id="2a15b-115">您必須是成員[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="2a15b-115">You must be a member the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators groups.</span></span>  
  
- [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]<span data-ttu-id="2a15b-116"> 必須安裝在您用來執行此工具的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="2a15b-116"> must be installed on the server on which you run the tool.</span></span>  
  
- <span data-ttu-id="2a15b-117">MrsrConfiguration.dll、 Shared.dll 和 RuleEngineExtension.dll 必須部署在您用來執行此工具的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="2a15b-117">MrsrConfiguration.dll, Shared.dll, and RuleEngineExtension.dll must be deployed on the server on which you run the tool.</span></span>  
  
## <a name="what-the-cleanup-tool-does"></a><span data-ttu-id="2a15b-118">清理工具的用途</span><span class="sxs-lookup"><span data-stu-id="2a15b-118">What the cleanup tool does</span></span>  
 <span data-ttu-id="2a15b-119">A4SWIFT 清理工具會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="2a15b-119">The A4SWIFT cleanup tool performs the following operations:</span></span>  
  
- <span data-ttu-id="2a15b-120">回合**BM 解除部署**ForActivities.xml 和 MRSRBAM.xml</span><span class="sxs-lookup"><span data-stu-id="2a15b-120">Runs **BM Undeploy** against ForActivities.xml and MRSRBAM.xml</span></span>  
  
- <span data-ttu-id="2a15b-121">如果有的話，移除 FrrActivities_ConnectionStrings.xml 和 MRSRActivities_ConnectionStrings.xml 檔案，</span><span class="sxs-lookup"><span data-stu-id="2a15b-121">Removes the FrrActivities_ConnectionStrings.xml and MRSRActivities_ConnectionStrings.xml files, if they exist</span></span>  
  
- <span data-ttu-id="2a15b-122">若有的話，移除 A4SWIFT 2.1 (如果您已升級伺服器[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，但安裝程式已離開 A4SWIFT 2.1 安裝)，並刪除 A4SWIFT 2.1 資料夾</span><span class="sxs-lookup"><span data-stu-id="2a15b-122">Removes A4SWIFT 2.1 if it exists (if you have upgraded the server to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], but Setup has left A4SWIFT 2.1 installed) and deletes the A4SWIFT 2.1 folder</span></span>  
  
- <span data-ttu-id="2a15b-123">解除部署 A4SWIFT 的所有組件</span><span class="sxs-lookup"><span data-stu-id="2a15b-123">Undeploys all A4SWIFT assemblies</span></span>  
  
- <span data-ttu-id="2a15b-124">刪除 A4SWIFT 系統管理員群組和 A4SWIFT 使用者群組</span><span class="sxs-lookup"><span data-stu-id="2a15b-124">Deletes the A4SWIFT Administrator group and the A4SWIFT Users group</span></span>  
  
- <span data-ttu-id="2a15b-125">刪除 A4SWIFT 資料庫</span><span class="sxs-lookup"><span data-stu-id="2a15b-125">Deletes the A4SWIFT database</span></span>  
  
- <span data-ttu-id="2a15b-126">刪除 A4SWIFT 虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="2a15b-126">Deletes the A4SWIFT virtual directory</span></span>  
  
- <span data-ttu-id="2a15b-127">執行的完整無訊息解除安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，並刪除[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]資料夾 （如果已選取）</span><span class="sxs-lookup"><span data-stu-id="2a15b-127">Runs a complete silent uninstall of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] and deletes the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] folder (if selected)</span></span>  
  
  <span data-ttu-id="2a15b-128">因為它會移除成品，並解除部署組件，清理工具也會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="2a15b-128">As it removes artifacts and undeploys assemblies, the cleanup tool also does the following:</span></span>  
  
- <span data-ttu-id="2a15b-129">若要執行的啟動 Internet Information Services (IIS) 管理員服務</span><span class="sxs-lookup"><span data-stu-id="2a15b-129">Starts Internet Information Services (IIS) Admin Service in order to run</span></span>  
  
- <span data-ttu-id="2a15b-130">會停止，然後重新啟動 MSSQLSERVER、 SQLSERVERAGENT、 BizTalk、 和企業單一登入服務</span><span class="sxs-lookup"><span data-stu-id="2a15b-130">Stops and then restarts the MSSQLSERVER, SQLSERVERAGENT, BizTalk, and Enterprise Single Sign-On services</span></span>  
  
#### <a name="to-run-the-a4swift-cleanup-tool"></a><span data-ttu-id="2a15b-131">若要執行 A4SWIFT 清理工具</span><span class="sxs-lookup"><span data-stu-id="2a15b-131">To run the A4SWIFT cleanup tool</span></span>  
  
1. <span data-ttu-id="2a15b-132">然後再執行 A4SWIFT 清理工具，解除部署是指任何 A4SWIFT 預設組件的任何專案。</span><span class="sxs-lookup"><span data-stu-id="2a15b-132">Prior to running the A4SWIFT cleanup tool, undeploy any project that refers to any of the A4SWIFT default assemblies.</span></span>  
  
2. <span data-ttu-id="2a15b-133">開啟命令提示字元並移至\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools。</span><span class="sxs-lookup"><span data-stu-id="2a15b-133">Open a command prompt and move to \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools.</span></span>  
  
3. <span data-ttu-id="2a15b-134">型別**A4SWIFTCleanupTool.exe** ，然後按**ENTER**。</span><span class="sxs-lookup"><span data-stu-id="2a15b-134">Type **A4SWIFTCleanupTool.exe** and then press **ENTER**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="2a15b-135">當您一開始執行 A4SWIFTCleanupTool.exe 時，此工具會顯示 [說明] 畫面中，並會提示您輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="2a15b-135">When you initially run A4SWIFTCleanupTool.exe, the tool displays a help screen, and prompts you to enter a parameter.</span></span> <span data-ttu-id="2a15b-136">您輸入的參數之前，不會執行此工具。</span><span class="sxs-lookup"><span data-stu-id="2a15b-136">The tool will not run until you enter the parameter.</span></span>  
  
4. <span data-ttu-id="2a15b-137">根據您希望該工具，要採取的動作，請按下列索引鍵，其中，然後按**ENTER**:</span><span class="sxs-lookup"><span data-stu-id="2a15b-137">Depending upon the actions that you want the tool to take, press one of the following keys, and then press **ENTER**:</span></span>  
  
   - <span data-ttu-id="2a15b-138">**0**的 （預設） 沒有動作</span><span class="sxs-lookup"><span data-stu-id="2a15b-138">**0** for no actions taken (the default)</span></span>  
  
   - <span data-ttu-id="2a15b-139">**1**移除所有本機 A4SWIFT 電腦上的資源，包括虛擬目錄和登錄設定</span><span class="sxs-lookup"><span data-stu-id="2a15b-139">**1** to remove all the local A4SWIFT resources on the computer, including the virtual directory and registry settings</span></span>  
  
   - <span data-ttu-id="2a15b-140">**2**移除所有的 BizTalk Server 群組，包括 Sharepoint Web 資料夾、 FIN 訊息範本，BRE 原則和詞彙、 BizTalk 成品和 A4SWIFT 資料庫上的共用的 A4SWIFT 資源</span><span class="sxs-lookup"><span data-stu-id="2a15b-140">**2** to remove all the shared A4SWIFT resources on the BizTalk Server group, including Sharepoint Web folders, FIN message templates, BRE policies and vocabularies, BizTalk artifacts, and the A4SWIFT database</span></span>  
  
   - <span data-ttu-id="2a15b-141">**3**移除所有本機和共用資源</span><span class="sxs-lookup"><span data-stu-id="2a15b-141">**3** to remove all the local and shared resources</span></span>  
  
   - <span data-ttu-id="2a15b-142">**4**來移除所有本機和共用資源和解除安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]產品。</span><span class="sxs-lookup"><span data-stu-id="2a15b-142">**4** to remove all the local and shared resources and uninstall the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] product.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a15b-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a15b-143">See Also</span></span>  
 [<span data-ttu-id="2a15b-144">工具</span><span class="sxs-lookup"><span data-stu-id="2a15b-144">Tools</span></span>](../../adapters-and-accelerators/accelerator-swift/tools.md)