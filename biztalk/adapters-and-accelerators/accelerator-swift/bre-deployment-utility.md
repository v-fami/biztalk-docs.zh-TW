---
title: "BRE 部署公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BRE Deployment utility
- deploying, BRE Deployment utility
ms.assetid: 5b04592c-ea1e-4ded-8ca4-dcd051d6375e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 731f40a75d898369cfc730ba5cb4f25c199e1333
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bre-deployment-utility"></a><span data-ttu-id="909e6-102">BRE 部署公用程式</span><span class="sxs-lookup"><span data-stu-id="909e6-102">BRE Deployment Utility</span></span>
<span data-ttu-id="909e6-103">您可以使用 BRE 部署公用程式來發佈和部署的商務規則引擎 (BRE) 詞彙和 SWIFT 的結構描述所需的原則。</span><span class="sxs-lookup"><span data-stu-id="909e6-103">You can use the BRE Deployment Utility to publish and deploy the Business Rule Engine (BRE) vocabularies and policies required for a SWIFT schema.</span></span> <span data-ttu-id="909e6-104">發行和部署這些詞彙和原則，才能啟用 BRE 驗證之訊息類型。</span><span class="sxs-lookup"><span data-stu-id="909e6-104">Publishing and deploying these vocabularies and policies is required to enable BRE validation for the message type.</span></span>  
  
 <span data-ttu-id="909e6-105">您也可以部署商務規則，以識別所需的規則，使用 SWIFT 標準發行指南 (SRGs)，然後使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]商務規則編輯器 」 工具來部署原則與詞彙。</span><span class="sxs-lookup"><span data-stu-id="909e6-105">You can also deploy business rules by using the SWIFT Standards Release Guides (SRGs) to identify the required rules, and then using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Business Rule Composer tool to deploy the vocabularies and policies.</span></span> <span data-ttu-id="909e6-106">不過，使用 BRE 部署公用程式會比較容易。</span><span class="sxs-lookup"><span data-stu-id="909e6-106">However, using the BRE Deployment Utility is much easier.</span></span>  
  
 <span data-ttu-id="909e6-107">BRE 部署公用程式會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="909e6-107">The BRE Deployment Utility accomplishes the following:</span></span>  
  
-   <span data-ttu-id="909e6-108">檢查您指定的已部署組件，並判斷您部署組件的訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="909e6-108">Examines the deployed assembly that you specify and determines the message schemas that you deployed for the assembly.</span></span>  
  
-   <span data-ttu-id="909e6-109">發行[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_CodeLists.xml 和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Functions.xml 詞彙所需的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]商務規則處理。</span><span class="sxs-lookup"><span data-stu-id="909e6-109">Publishes the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_CodeLists.xml and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Functions.xml vocabularies required for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] business rules processing.</span></span>  
  
-   <span data-ttu-id="909e6-110">發行和部署 SWIFT 基底 （參考原則、 合作對象識別項原則，以及網路規則原則） 相關聯的原則與訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="909e6-110">Publishes and deploys the SWIFT base policies (reference policy, party identifier policy, and network rule policies) associated with the message schemas.</span></span>  
  
-   <span data-ttu-id="909e6-111">部署主要原則和每個訊息結構描述相關聯的驗證原則和發佈。</span><span class="sxs-lookup"><span data-stu-id="909e6-111">Publishes and deploys the master policy and validation policy associated with each message schema.</span></span>  
  
-   <span data-ttu-id="909e6-112">產生記錄檔，指出所需的所有步驟。</span><span class="sxs-lookup"><span data-stu-id="909e6-112">Generates a log file that indicates all the steps that it takes.</span></span> <span data-ttu-id="909e6-113">這個檔案是在 BREDeploymentLog.txt \<*磁碟機*>: \Documents and Settings\All Users\Application Data 資料夾。</span><span class="sxs-lookup"><span data-stu-id="909e6-113">This file is BREDeploymentLog.txt in the \<*drive*>:\Documents and Settings\All Users\Application Data folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="909e6-114">BRE 部署公用程式不會部署 BIC 主要原則和 BIC 驗證原則。</span><span class="sxs-lookup"><span data-stu-id="909e6-114">The BRE Deployment Utility does not deploy the BIC Master Policy and BIC Validation Policy.</span></span> <span data-ttu-id="909e6-115">您必須部署這些使用規則引擎部署精靈。</span><span class="sxs-lookup"><span data-stu-id="909e6-115">You must deploy these using the Rule Engine Deployment wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="909e6-116">如果您已安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]非預設的目錄 (C:\Program Files\Microsoft 以外[!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)])，或您使用 64 位元電腦上，BRE 部署公用程式將無法正常運作之前變更中的路徑過的 BREDeployment.exe.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="909e6-116">If you have installed [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] in a non-default directory (other than C:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]), or you are working on a 64-bit computer, the BRE Deployment Utility will not work correctly until you change the paths in the BREDeployment.exe.config file.</span></span> <span data-ttu-id="909e6-117">此組態檔位於\<*磁碟機*>: \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\SDK\Tools 資料夾。</span><span class="sxs-lookup"><span data-stu-id="909e6-117">This configuration file is located in the \<*drive*>:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\SDK\Tools folder.</span></span> <span data-ttu-id="909e6-118">若要更新公用程式的組態，在 [記事本] 中開啟過的 BREDeployment.exe.config 並變更詞彙目錄、 結構描述，以及基底原則資料夾。</span><span class="sxs-lookup"><span data-stu-id="909e6-118">To update the utility's configuration, open BREDeployment.exe.config in Notepad, and change the folders for the base policies, schemas, and vocabulary directories.</span></span>  
  
 <span data-ttu-id="909e6-119">您也可以使用部署公用程式可反轉程序中，解除部署和取消發佈原則和詞彙。</span><span class="sxs-lookup"><span data-stu-id="909e6-119">You can also use the deployment utility to reverse this process, undeploying and unpublishing the policies and vocabularies.</span></span> <span data-ttu-id="909e6-120">公用程式都有部署和解除部署功能。</span><span class="sxs-lookup"><span data-stu-id="909e6-120">The utility has both deploy and undeploy functionality.</span></span>  
  
### <a name="to-use-the-bre-deployment-utility"></a><span data-ttu-id="909e6-121">若要使用 BRE 部署公用程式</span><span class="sxs-lookup"><span data-stu-id="909e6-121">To use the BRE Deployment Utility</span></span>  
  
1.  <span data-ttu-id="909e6-122">按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk Accelerator for SWIFT**，然後按一下  **BRE 部署公用程式**。</span><span class="sxs-lookup"><span data-stu-id="909e6-122">Click **Start**, point to **Programs**, point to **Microsoft BizTalk Accelerator for SWIFT**, and then click **BRE Deployment Utility**.</span></span>  
  
2.  <span data-ttu-id="909e6-123">BRE 部署公用程式中，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="909e6-123">In the BRE Deployment Utility, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="909e6-124">選取您要發佈的詞彙和原則，部署，然後按一下 組件的部署的組件**確定**。</span><span class="sxs-lookup"><span data-stu-id="909e6-124">Select the deployed assembly or assemblies for which you want to publish and deploy vocabularies and policies, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="909e6-125">按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="909e6-125">Click **Deploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="909e6-126">根據您部署與該組件的結構描述，BRE 部署公用程式就會進行識別相關的規則，然後發行 BRE 搭配使用的程序。</span><span class="sxs-lookup"><span data-stu-id="909e6-126">Based on the schemas that you deployed with that assembly, the BRE Deployment Utility goes through the process of identifying the related rules and publishing them for use with the BRE.</span></span> <span data-ttu-id="909e6-127">完成時，BRE 部署公用程式會顯示下列訊息：**完成部署之後**。</span><span class="sxs-lookup"><span data-stu-id="909e6-127">When complete, the BRE Deployment Utility displays the following message: **Deployment has completed**.</span></span> <span data-ttu-id="909e6-128">若要確認成功部署使用 「 商務規則編輯器 」。</span><span class="sxs-lookup"><span data-stu-id="909e6-128">Use the Business Rule Composer to verify successful deployment.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="909e6-129">若要解除部署原則和詞彙，請按一下**解除部署**。</span><span class="sxs-lookup"><span data-stu-id="909e6-129">To undeploy the policies and vocabularies, click **Undeploy**.</span></span> <span data-ttu-id="909e6-130">解除部署處理程序解除 A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml 詞彙，這可能需要使用其他已部署的原則未部署。</span><span class="sxs-lookup"><span data-stu-id="909e6-130">The undeploy process does not undeploy the A4SWIFT_CodeLists.xml and A4SWIFT_Functions.xml vocabularies, which might be used by other deployed policies.</span></span>  
  
5.  <span data-ttu-id="909e6-131">找出\<*磁碟機*>: \Documents and Settings\All Users\Application 資料，以確認公用程式建立記錄檔檔案 BREDeploymentLog.txt。</span><span class="sxs-lookup"><span data-stu-id="909e6-131">Locate \<*drive*>:\Documents and Settings\All Users\Application Data to confirm that the utility created the log file BREDeploymentLog.txt.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="909e6-132">您可以使用文字編輯器，以確認每個部署步驟來開啟記錄檔。</span><span class="sxs-lookup"><span data-stu-id="909e6-132">You can open the log file by using a text editor to confirm each deployment step.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="909e6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="909e6-133">See Also</span></span>  
 [<span data-ttu-id="909e6-134">工具</span><span class="sxs-lookup"><span data-stu-id="909e6-134">Tools</span></span>](../../adapters-and-accelerators/accelerator-swift/tools.md)