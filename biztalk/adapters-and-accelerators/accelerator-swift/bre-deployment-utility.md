---
title: BRE 部署公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BRE Deployment utility
- deploying, BRE Deployment utility
ms.assetid: 5b04592c-ea1e-4ded-8ca4-dcd051d6375e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b2449795a52bd26bed0326a3aa2fcf57f8bb552
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010151"
---
# <a name="bre-deployment-utility"></a><span data-ttu-id="7723d-102">BRE 部署公用程式</span><span class="sxs-lookup"><span data-stu-id="7723d-102">BRE Deployment Utility</span></span>
<span data-ttu-id="7723d-103">您可以使用 BRE 部署公用程式來發佈和部署的商務規則引擎 (BRE) 詞彙和原則所需的 SWIFT 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7723d-103">You can use the BRE Deployment Utility to publish and deploy the Business Rule Engine (BRE) vocabularies and policies required for a SWIFT schema.</span></span> <span data-ttu-id="7723d-104">發行和部署這些詞彙和原則，才能啟用 BRE 驗證之訊息類型。</span><span class="sxs-lookup"><span data-stu-id="7723d-104">Publishing and deploying these vocabularies and policies is required to enable BRE validation for the message type.</span></span>  
  
 <span data-ttu-id="7723d-105">您也可以部署 商務規則來識別所需的規則，使用 SWIFT 標準版指南 (SRGs)，然後使用 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]部署原則與詞彙的商務規則編輯器 」 工具。</span><span class="sxs-lookup"><span data-stu-id="7723d-105">You can also deploy business rules by using the SWIFT Standards Release Guides (SRGs) to identify the required rules, and then using the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Business Rule Composer tool to deploy the vocabularies and policies.</span></span> <span data-ttu-id="7723d-106">不過，使用 BRE 部署公用程式會更加容易。</span><span class="sxs-lookup"><span data-stu-id="7723d-106">However, using the BRE Deployment Utility is much easier.</span></span>  
  
 <span data-ttu-id="7723d-107">BRE 部署公用程式會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="7723d-107">The BRE Deployment Utility accomplishes the following:</span></span>  
  
- <span data-ttu-id="7723d-108">檢查您指定的部署組件，並判斷您部署組件的訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="7723d-108">Examines the deployed assembly that you specify and determines the message schemas that you deployed for the assembly.</span></span>  
  
- <span data-ttu-id="7723d-109">發佈[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_CodeLists.xml 並[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Functions.xml 詞彙所需的 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]商務規則處理。</span><span class="sxs-lookup"><span data-stu-id="7723d-109">Publishes the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_CodeLists.xml and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Functions.xml vocabularies required for Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] business rules processing.</span></span>  
  
- <span data-ttu-id="7723d-110">發佈和部署 SWIFT 基底 （參考原則、 合作對象識別項原則，以及網路規則原則） 相關聯的原則與訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="7723d-110">Publishes and deploys the SWIFT base policies (reference policy, party identifier policy, and network rule policies) associated with the message schemas.</span></span>  
  
- <span data-ttu-id="7723d-111">發佈和部署的主要原則和與每個訊息結構描述相關聯的驗證原則。</span><span class="sxs-lookup"><span data-stu-id="7723d-111">Publishes and deploys the master policy and validation policy associated with each message schema.</span></span>  
  
- <span data-ttu-id="7723d-112">產生記錄檔，指出所需的所有步驟。</span><span class="sxs-lookup"><span data-stu-id="7723d-112">Generates a log file that indicates all the steps that it takes.</span></span> <span data-ttu-id="7723d-113">這個檔案是在 BREDeploymentLog.txt \<*磁碟機*\>: \Documents and Settings\All Users\Application Data 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7723d-113">This file is BREDeploymentLog.txt in the \<*drive*\>:\Documents and Settings\All Users\Application Data folder.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="7723d-114">BRE 部署公用程式不會部署 BIC 主要原則和 BIC 驗證原則。</span><span class="sxs-lookup"><span data-stu-id="7723d-114">The BRE Deployment Utility does not deploy the BIC Master Policy and BIC Validation Policy.</span></span> <span data-ttu-id="7723d-115">您必須部署這些使用規則引擎部署精靈。</span><span class="sxs-lookup"><span data-stu-id="7723d-115">You must deploy these using the Rule Engine Deployment wizard.</span></span>  
  > 
  > [!NOTE]
  >  <span data-ttu-id="7723d-116">如果您已安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]在非預設目錄 (C:\Program Files\Microsoft 以外[!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)])，或您正在 64 位元電腦上，BRE 部署公用程式將無法正常運作之前變更中的路徑過的 BREDeployment.exe.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="7723d-116">If you have installed [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] in a non-default directory (other than C:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]), or you are working on a 64-bit computer, the BRE Deployment Utility will not work correctly until you change the paths in the BREDeployment.exe.config file.</span></span> <span data-ttu-id="7723d-117">此組態檔位於\<*磁碟機*\>: \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\SDK\Tools 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7723d-117">This configuration file is located in the \<*drive*\>:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\SDK\Tools folder.</span></span> <span data-ttu-id="7723d-118">若要更新公用程式的組態，在 [記事本] 開啟過的 BREDeployment.exe.config 並變更詞彙目錄、 結構描述，以及基底原則的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7723d-118">To update the utility's configuration, open BREDeployment.exe.config in Notepad, and change the folders for the base policies, schemas, and vocabulary directories.</span></span>  
  
  <span data-ttu-id="7723d-119">您也可以使用部署公用程式，若要反轉此程序，解除部署和取消發佈原則和詞彙。</span><span class="sxs-lookup"><span data-stu-id="7723d-119">You can also use the deployment utility to reverse this process, undeploying and unpublishing the policies and vocabularies.</span></span> <span data-ttu-id="7723d-120">公用程式都已部署，並解除部署功能。</span><span class="sxs-lookup"><span data-stu-id="7723d-120">The utility has both deploy and undeploy functionality.</span></span>  
  
### <a name="to-use-the-bre-deployment-utility"></a><span data-ttu-id="7723d-121">若要使用 BRE 部署公用程式</span><span class="sxs-lookup"><span data-stu-id="7723d-121">To use the BRE Deployment Utility</span></span>  
  
1.  <span data-ttu-id="7723d-122">按一下 **開始**，指向**程式**，指向**Microsoft BizTalk Accelerator for SWIFT**，然後按一下**BRE 部署公用程式**。</span><span class="sxs-lookup"><span data-stu-id="7723d-122">Click **Start**, point to **Programs**, point to **Microsoft BizTalk Accelerator for SWIFT**, and then click **BRE Deployment Utility**.</span></span>  
  
2.  <span data-ttu-id="7723d-123">BRE 部署公用程式中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="7723d-123">In the BRE Deployment Utility, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="7723d-124">選取您要發行部署的詞彙和原則]，然後按一下 [組件的已部署的組件**確定**。</span><span class="sxs-lookup"><span data-stu-id="7723d-124">Select the deployed assembly or assemblies for which you want to publish and deploy vocabularies and policies, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="7723d-125">按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="7723d-125">Click **Deploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7723d-126">根據您部署與該組件的結構描述，BRE 部署公用程式會經歷找出相關的規則，並將其發佈用於 BRE 的程序。</span><span class="sxs-lookup"><span data-stu-id="7723d-126">Based on the schemas that you deployed with that assembly, the BRE Deployment Utility goes through the process of identifying the related rules and publishing them for use with the BRE.</span></span> <span data-ttu-id="7723d-127">完成時，BRE 部署公用程式會顯示下列訊息：**完成部署之後**。</span><span class="sxs-lookup"><span data-stu-id="7723d-127">When complete, the BRE Deployment Utility displays the following message: **Deployment has completed**.</span></span> <span data-ttu-id="7723d-128">若要確認成功部署使用 「 商務規則編輯器 」。</span><span class="sxs-lookup"><span data-stu-id="7723d-128">Use the Business Rule Composer to verify successful deployment.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7723d-129">若要解除部署原則和詞彙，按一下**Undeploy**。</span><span class="sxs-lookup"><span data-stu-id="7723d-129">To undeploy the policies and vocabularies, click **Undeploy**.</span></span> <span data-ttu-id="7723d-130">解除部署處理程序不會不會解除部署 A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml 詞彙，這可能會由其他已部署的原則。</span><span class="sxs-lookup"><span data-stu-id="7723d-130">The undeploy process does not undeploy the A4SWIFT_CodeLists.xml and A4SWIFT_Functions.xml vocabularies, which might be used by other deployed policies.</span></span>  
  
5.  <span data-ttu-id="7723d-131">找出\<*磁碟機*\>: \Documents and Settings\All Users\Application Data，若要確認此公用程式建立記錄檔檔案 BREDeploymentLog.txt。</span><span class="sxs-lookup"><span data-stu-id="7723d-131">Locate \<*drive*\>:\Documents and Settings\All Users\Application Data to confirm that the utility created the log file BREDeploymentLog.txt.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7723d-132">您可以確認每個部署步驟中使用文字編輯器中開啟記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7723d-132">You can open the log file by using a text editor to confirm each deployment step.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7723d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7723d-133">See Also</span></span>  
 [<span data-ttu-id="7723d-134">工具</span><span class="sxs-lookup"><span data-stu-id="7723d-134">Tools</span></span>](../../adapters-and-accelerators/accelerator-swift/tools.md)