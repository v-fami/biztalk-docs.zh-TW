---
title: 部署 BRE 規則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, BRE policies
- BRE policies, deploying
ms.assetid: 3a66aa57-e7f9-400f-963c-eda12fb1e659
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5627731bd84a761ffb62b95646876c768e3298ea
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967889"
---
# <a name="deploying-bre-rules"></a><span data-ttu-id="b996f-102">部署 BRE 規則</span><span class="sxs-lookup"><span data-stu-id="b996f-102">Deploying BRE Rules</span></span>
<span data-ttu-id="b996f-103">您必須部署所用的 BRE 規則[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]處理 SWIFT 訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="b996f-103">You must deploy the BRE rules used by [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] orchestrations to process SWIFT messages.</span></span>  
  
 <span data-ttu-id="b996f-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="b996f-104">**Summary**</span></span>  
  
 <span data-ttu-id="b996f-105">發行下列詞彙：</span><span class="sxs-lookup"><span data-stu-id="b996f-105">Publish the following vocabularies:</span></span>  
  
-   <span data-ttu-id="b996f-106">A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml 詞彙。</span><span class="sxs-lookup"><span data-stu-id="b996f-106">A4SWIFT_CodeLists.xml and A4SWIFT_Functions.xml vocabularies.</span></span> <span data-ttu-id="b996f-107">這些都位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base Policies\Vocabulary。</span><span class="sxs-lookup"><span data-stu-id="b996f-107">These are located in *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies\Vocabulary.</span></span> <span data-ttu-id="b996f-108">發行和部署這些使用 BRE 部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="b996f-108">Publish and deploy these using the BRE Deployment Utility.</span></span>  
  
 <span data-ttu-id="b996f-109">發佈和部署下列原則：</span><span class="sxs-lookup"><span data-stu-id="b996f-109">Publish and deploy the following policies:</span></span>  
  
-   <span data-ttu-id="b996f-110">SWIFT 訊息結構描述的基底原則，包括 SWIFT_Reference_Policy.xml、 SWIFT_PartyIdentifier_Policy.xml，以及網路規則原則 (SWIFT_NetworkRulexxx_Policy.xml) 部署結構描述。</span><span class="sxs-lookup"><span data-stu-id="b996f-110">SWIFT base policies for message schema, including SWIFT_Reference_Policy.xml, SWIFT_PartyIdentifier_Policy.xml, and network rule policies (SWIFT_NetworkRulexxx_Policy.xml) for deployed schemas.</span></span> <span data-ttu-id="b996f-111">這些都位於\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則。</span><span class="sxs-lookup"><span data-stu-id="b996f-111">These are located in \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies.</span></span> <span data-ttu-id="b996f-112">發行和部署這些使用 BRE 部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="b996f-112">Publish and deploy these using the BRE Deployment Utility.</span></span>  
  
-   <span data-ttu-id="b996f-113">與已部署的訊息結構描述 （MTxxx_Master_Policy.xml 和 MTxxx_Validation_Policy.xml） 相關聯的主要和驗證原則。</span><span class="sxs-lookup"><span data-stu-id="b996f-113">Master and validation policies associated with deployed message schemas (MTxxx_Master_Policy.xml and MTxxx_Validation_Policy.xml).</span></span> <span data-ttu-id="b996f-114">這些都位於\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category 1\MTxxx。</span><span class="sxs-lookup"><span data-stu-id="b996f-114">These are located in \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MTxxx.</span></span> <span data-ttu-id="b996f-115">發行和部署這些使用 BRE 部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="b996f-115">Publish and deploy these using the BRE Deployment Utility.</span></span>  
  
-   <span data-ttu-id="b996f-116">若需要 BIC 驗證 BIC 驗證 （BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml） 與相關聯的主要和驗證原則。</span><span class="sxs-lookup"><span data-stu-id="b996f-116">Master and validation policies associated with BIC validation (BIC_Master_Policy.xml and BIC_Validation_Policy.xml), if BIC validation is required.</span></span> <span data-ttu-id="b996f-117">這些都位於\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則。</span><span class="sxs-lookup"><span data-stu-id="b996f-117">These are located in \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies.</span></span> <span data-ttu-id="b996f-118">發佈和部署這些原則，您必須自訂 BIC_Master_Policy.xml 的 SQL Server、 BIC 資料庫名稱，名稱前後整合安全性值。</span><span class="sxs-lookup"><span data-stu-id="b996f-118">Before publishing and deploying these policies, you must customize BIC_Master_Policy.xml with the names of the SQL Server, the BIC database name, and integrated security value.</span></span> <span data-ttu-id="b996f-119">如需詳細資訊，請參閱[啟用驗證的銀行識別項代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)。</span><span class="sxs-lookup"><span data-stu-id="b996f-119">For more information, see [Enabling Validation of Bank Identifier Codes](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md).</span></span> <span data-ttu-id="b996f-120">發行和部署這些使用規則引擎部署精靈。</span><span class="sxs-lookup"><span data-stu-id="b996f-120">Publish and deploy these using the Rules Engine Deployment Wizard.</span></span>  
  
### <a name="to-deploy-bre-rules"></a><span data-ttu-id="b996f-121">若要部署 BRE 規則</span><span class="sxs-lookup"><span data-stu-id="b996f-121">To deploy BRE rules</span></span>  
  
1.  <span data-ttu-id="b996f-122">執行 BRE 部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="b996f-122">Run the BRE Deployment Utility.</span></span> <span data-ttu-id="b996f-123">如需詳細資訊，請參閱 「 部署 BRE 規則所有在一次 」 底下。</span><span class="sxs-lookup"><span data-stu-id="b996f-123">For more information, see "Deploying BRE Rules All at Once" below.</span></span> <span data-ttu-id="b996f-124">此公用程式將會發行，並部署下列：</span><span class="sxs-lookup"><span data-stu-id="b996f-124">This utility will publish and deploy the following:</span></span>  
  
    -   <span data-ttu-id="b996f-125">A4SWIFT_CodeLists.xml 和 A4SWIFT_Functions.xml 詞彙</span><span class="sxs-lookup"><span data-stu-id="b996f-125">A4SWIFT_CodeLists.xml and A4SWIFT_Functions.xml vocabularies</span></span>  
  
    -   <span data-ttu-id="b996f-126">SWIFT 的訊息結構描述，包括 SWIFT_Reference_Policy.xml、 SWIFT_PartyIdentifier_Policy.xml，以及網路規則原則 (SWIFT_NetworkRulexxx_Policy.xml) 的基底原則</span><span class="sxs-lookup"><span data-stu-id="b996f-126">SWIFT base policies for message schema, including SWIFT_Reference_Policy.xml, SWIFT_PartyIdentifier_Policy.xml, and network rule policies (SWIFT_NetworkRulexxx_Policy.xml)</span></span>  
  
    -   <span data-ttu-id="b996f-127">與已部署的訊息結構描述 （MTxxx_Master_Policy.xml 和 MTxxx_Validation_Policy.xml） 相關聯的主要和驗證原則</span><span class="sxs-lookup"><span data-stu-id="b996f-127">Master and validation policies associated with deployed message schemas (MTxxx_Master_Policy.xml and MTxxx_Validation_Policy.xml)</span></span>  
  
2.  <span data-ttu-id="b996f-128">自訂 BIC_Master_Policy.xml SQL server、 BIC 資料庫名稱，以及整合式安全性值的名稱。</span><span class="sxs-lookup"><span data-stu-id="b996f-128">Customize BIC_Master_Policy.xml with the names of the SQL server, the BIC database name, and integrated security value.</span></span> <span data-ttu-id="b996f-129">如需詳細資訊，請參閱[啟用驗證的銀行識別項代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)。</span><span class="sxs-lookup"><span data-stu-id="b996f-129">For more information, see [Enabling Validation of Bank Identifier Codes](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md).</span></span>  
  
3.  <span data-ttu-id="b996f-130">執行規則引擎部署精靈來發行和部署 BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml (在\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則)。</span><span class="sxs-lookup"><span data-stu-id="b996f-130">Run the Rules Engine Deployment Wizard to publish and deploy BIC_Master_Policy.xml and   BIC_Validation_Policy.xml (in \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies).</span></span> <span data-ttu-id="b996f-131">如需詳細資訊，請參閱 「 部署 BRE 規則一個在時間 」 底下。</span><span class="sxs-lookup"><span data-stu-id="b996f-131">For more information, see "Deploying BRE Rules One at a Time" below.</span></span>  
  
## <a name="tools-for-deploying-the-policies"></a><span data-ttu-id="b996f-132">部署原則的工具</span><span class="sxs-lookup"><span data-stu-id="b996f-132">Tools for Deploying the Policies</span></span>  
 <span data-ttu-id="b996f-133">發佈詞彙及部署原則的最簡單方式是使用 「 商務規則引擎 (BRE) 部署公用程式 A4SWIFT 軟體開發套件 (SDK) 中。</span><span class="sxs-lookup"><span data-stu-id="b996f-133">The easiest way to publish the vocabularies and deploy the policies is by using the Business Rule Engine (BRE) Deployment Utility in the A4SWIFT Software Development Kit (SDK).</span></span> <span data-ttu-id="b996f-134">您也可以執行動作，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]規則引擎部署精靈 」 便會執行相同工作的一個詞彙或原則一次。</span><span class="sxs-lookup"><span data-stu-id="b996f-134">You can also do so by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Rule Engine Deployment Wizard, which performs the same task one vocabulary or policy at a time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b996f-135">BRE 部署公用程式不會部署 BIC 主要原則和 BIC 驗證原則。</span><span class="sxs-lookup"><span data-stu-id="b996f-135">The BRE Deployment Utility does not deploy the BIC Master Policy and BIC Validation Policy.</span></span> <span data-ttu-id="b996f-136">您必須部署這些使用規則引擎部署精靈。</span><span class="sxs-lookup"><span data-stu-id="b996f-136">You must deploy these using the Rule Engine Deployment wizard.</span></span>  
  
### <a name="deploying-bre-rules-all-at-once"></a><span data-ttu-id="b996f-137">一次部署 BRE 規則</span><span class="sxs-lookup"><span data-stu-id="b996f-137">Deploying BRE Rules All at Once</span></span>  
 <span data-ttu-id="b996f-138">商務規則引擎 (BRE) 部署公用程式在一個步驟中執行一系列的發行和部署工作。</span><span class="sxs-lookup"><span data-stu-id="b996f-138">The Business Rule Engine (BRE) Deployment Utility performs a series of publishing and deployment tasks in one step.</span></span> <span data-ttu-id="b996f-139">您必須重新執行部署公用程式隨時將結構描述加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="b996f-139">You must rerun the deployment utility any time that you add a schema to your project.</span></span>  
  
##### <a name="to-deploy-bre-rules-using-the-bre-deployment-utility"></a><span data-ttu-id="b996f-140">若要部署使用 BRE 部署公用程式的 BRE 規則</span><span class="sxs-lookup"><span data-stu-id="b996f-140">To deploy BRE rules using the BRE Deployment Utility</span></span>  
  
1.  <span data-ttu-id="b996f-141">按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Accelerator for SWIFT**，然後按一下  **BRE 部署公用程式**.</span><span class="sxs-lookup"><span data-stu-id="b996f-141">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Accelerator for SWIFT**, and then click **BRE Deployment Utility**.</span></span>  
  
2.  <span data-ttu-id="b996f-142">在 BRE 部署公用程式 對話方塊中，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="b996f-142">In the BRE Deployment Utility dialog box, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="b996f-143">在.NET 全域組件快取] 對話方塊中，選取您在部署專案組件[部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="b996f-143">In the .NET Global Assembly Cache dialog box, select the project assembly that you deployed in [Deploying A4SWIFT Schemas](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md), and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="b996f-144">在 BRE 部署公用程式 對話方塊中，按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="b996f-144">In the BRE Deployment Utility dialog box, click **Deploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b996f-145">根據您部署與該組件的結構描述，部署公用程式會識別相關的規則，並將其發行 BRE 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b996f-145">Based on the schemas you deployed with that assembly, the deployment utility identifies the related rules and publishes them for use with the BRE.</span></span> <span data-ttu-id="b996f-146">完成時，BRE 部署公用程式會顯示下列訊息：</span><span class="sxs-lookup"><span data-stu-id="b996f-146">When complete, the BRE Deployment Utility displays the following message:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b996f-147">「 已完成部署。</span><span class="sxs-lookup"><span data-stu-id="b996f-147">"Deployment has completed.</span></span> <span data-ttu-id="b996f-148">檢視記錄檔或商務規則編輯器 」 以取得詳細資料。 」</span><span class="sxs-lookup"><span data-stu-id="b996f-148">View the log file or Business Rule Composer for details."</span></span>  
  
5.  <span data-ttu-id="b996f-149">關閉 [BRE 部署公用程式] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b996f-149">Close the BRE Deployment Utility dialog box.</span></span>  
  
6.  <span data-ttu-id="b996f-150">開啟[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管。</span><span class="sxs-lookup"><span data-stu-id="b996f-150">Open [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer.</span></span> <span data-ttu-id="b996f-151">瀏覽至\<*磁碟機*\>: \Documents and Settings\All Users\Application 資料，並確認記錄檔 BREDeploymentLog.txt 出現在該磁碟機。</span><span class="sxs-lookup"><span data-stu-id="b996f-151">Browse to \<*drive*\>:\Documents and Settings\All Users\Application Data, and confirm that the log file BREDeploymentLog.txt appears in that drive.</span></span>  
  
7.  <span data-ttu-id="b996f-152">重新啟動 「 規則引擎更新服務。</span><span class="sxs-lookup"><span data-stu-id="b996f-152">Restart the Rule Engine Update Service.</span></span> <span data-ttu-id="b996f-153">這樣即可**啟動**，然後按一下**執行**、 輸入**services.msc**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b996f-153">Do so by clicking **Start**, clicking **Run**, entering **services.msc**, and clicking **OK**.</span></span> <span data-ttu-id="b996f-154">在**服務 （本機）** 視窗中，以滑鼠右鍵按一下**規則引擎更新服務**，然後按一下 **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="b996f-154">In the **Services (Local)** window, right-click **Rule Engine Update Service**, and then click **Restart**.</span></span>  
  
### <a name="deploying-bre-rules-one-at-a-time"></a><span data-ttu-id="b996f-155">部署 BRE 規則一次</span><span class="sxs-lookup"><span data-stu-id="b996f-155">Deploying BRE Rules One at a Time</span></span>  
 <span data-ttu-id="b996f-156">您可以使用 「 規則引擎部署精靈 」 來發佈詞彙和部署原則一次。</span><span class="sxs-lookup"><span data-stu-id="b996f-156">You can use the Rules Engine Deployment Wizard to publish vocabularies and deploy policies one at a time.</span></span> <span data-ttu-id="b996f-157">一種詞彙，這個程序牽涉到匯入和資料庫發佈的詞彙，從一個步驟中的檔案。</span><span class="sxs-lookup"><span data-stu-id="b996f-157">For a vocabulary, this process involves importing and publishing the vocabulary to the database from a file in one step.</span></span> <span data-ttu-id="b996f-158">原則的程序牽涉到匯入與發行原則在一個步驟中，然後將其部署在另一個步驟。</span><span class="sxs-lookup"><span data-stu-id="b996f-158">For a policy, the process involves importing and publishing the policy in one step, and then deploying it in another step.</span></span>  
  
##### <a name="to-deploy-bre-rules-using-the-rules-engine-deployment-wizard"></a><span data-ttu-id="b996f-159">若要部署 BRE 規則使用 規則引擎部署精靈</span><span class="sxs-lookup"><span data-stu-id="b996f-159">To deploy BRE rules Using the Rules Engine Deployment Wizard</span></span>  
  
1.  <span data-ttu-id="b996f-160">按一下**啟動**，指向 **所有程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則引擎部署精靈**.</span><span class="sxs-lookup"><span data-stu-id="b996f-160">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rules Engine Deployment Wizard**.</span></span>  
  
2.  <span data-ttu-id="b996f-161">在歡迎使用規則引擎部署精靈] 頁面上，按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b996f-161">On the Welcome to the Rules Engine Deployment Wizard page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="b996f-162">在部署工作 頁面上，按一下 **匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b996f-162">On the Deployment Task page, click **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="b996f-163">在原則存放區 頁面上，在**SQL 伺服器名稱 清單**，選取您的伺服器，然後在**選取的伺服器上設定資料庫**清單中，選取**BizTalkRuleEngineDb**。</span><span class="sxs-lookup"><span data-stu-id="b996f-163">On the Policy Store page, in the **SQL Server Name list**, select your server, and in the **Configuration Database on selected server** list, select **BizTalkRuleEngineDb**.</span></span> <span data-ttu-id="b996f-164">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="b996f-164">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="b996f-165">在 匯入規則引擎原則/詞彙檔案 頁面中，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="b996f-165">On the Import Rules Engine Policy/Vocabulary file page, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="b996f-166">在匯入原則檔案 頁面上，從在**查看**下拉式清單中，移至下列資料夾，根據的詞彙或原則的其中一個：</span><span class="sxs-lookup"><span data-stu-id="b996f-166">On the Import Policy from file page, in the **Look in** drop-down list, move to one of the following folders, depending upon the vocabulary or policy:</span></span>  
  
    -   <span data-ttu-id="b996f-167">\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>A4SWIFT_ 的 \Base Policies\VocabularyCodeLists.xml 和 A4SWIFT_Functions.xml</span><span class="sxs-lookup"><span data-stu-id="b996f-167">\<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies\Vocabulary for A4SWIFT_CodeLists.xml and A4SWIFT_Functions.xml</span></span>  
  
    -   <span data-ttu-id="b996f-168">\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base SWIFT_Reference_Policy.xml，原則SWIFT_PartyIdentifier_Policy.xml、 網路規則原則、 BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml</span><span class="sxs-lookup"><span data-stu-id="b996f-168">\<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies for SWIFT_Reference_Policy.xml, SWIFT_PartyIdentifier_Policy.xml, network rule policies, BIC_Master_Policy.xml, and BIC_Validation_Policy.xml</span></span>  
  
    -   <span data-ttu-id="b996f-169">\<磁碟機\>: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category 1\MTxxx 之 master 和驗證已部署的訊息結構描述相關聯的原則</span><span class="sxs-lookup"><span data-stu-id="b996f-169">\<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MTxxx for the master and validation policies associated with deployed message schemas</span></span>  
  
7.  <span data-ttu-id="b996f-170">選取您想要部署，然後按一下 原則**開啟**。</span><span class="sxs-lookup"><span data-stu-id="b996f-170">Select the policy that you want to deploy, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="b996f-171">在 匯入規則引擎原則/詞彙檔案 頁面中，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b996f-171">On the Import Rules Engine Policy/Vocabulary file page, click **Next**.</span></span>  
  
9. <span data-ttu-id="b996f-172">在 就緒 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b996f-172">On the Ready page, click **Next**.</span></span>  
  
10. <span data-ttu-id="b996f-173">在 匯入原則/詞彙 頁面上，確認命令成功，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b996f-173">On the Importing Policy/Vocabulary page, verify that the command succeeded, and then click **Next**.</span></span>  
  
11. <span data-ttu-id="b996f-174">如果您想要部署原則，在正在完成規則引擎部署精靈 頁面上，按一下 **再次執行此精靈**，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="b996f-174">If you want to deploy a policy, on the Completing the Rules Engine Deployment Wizard page, click **Run this Wizard again**, and then click **Finish**.</span></span>  
  
12. <span data-ttu-id="b996f-175">在歡迎使用規則引擎部署精靈] 頁面上，按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b996f-175">On the Welcome to the Rules Engine Deployment Wizard page, click **Next**.</span></span>  
  
13. <span data-ttu-id="b996f-176">在部署工作 頁面上，按一下 **部署原則**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b996f-176">On the Deployment Task page, click **Deploy Policy**, and then click **Next**.</span></span>  
  
14. <span data-ttu-id="b996f-177">在原則存放區 頁面上，在**SQL 伺服器名稱 清單**，選取您的伺服器，然後在**選取的伺服器上設定資料庫**清單中，選取**BizTalkRuleEngineDb**。</span><span class="sxs-lookup"><span data-stu-id="b996f-177">On the Policy Store page, in the **SQL Server Name list**, select your server, and in the **Configuration Database on selected server** list, select **BizTalkRuleEngineDb**.</span></span> <span data-ttu-id="b996f-178">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="b996f-178">Click **Next**.</span></span>  
  
15. <span data-ttu-id="b996f-179">在部署原則 頁面上，按一下向下箭號旁**規則引擎原則** 文字方塊中，選取您剛才的原則，發佈，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b996f-179">On the Deploy Policy page, click the down arrow next to the **Rules Engine Policy** text box, select the policy you just published, and then click **Next**.</span></span>  
  
16. <span data-ttu-id="b996f-180">在 就緒 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b996f-180">On the Ready page, click **Next**.</span></span>  
  
17. <span data-ttu-id="b996f-181">在**匯入原則/詞彙**頁面上，確認命令成功，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b996f-181">On the **Importing Policy/Vocabulary** page, verify that the command succeeded, and then click **Next**.</span></span>  
  
18. <span data-ttu-id="b996f-182">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="b996f-182">Click **Finish**.</span></span>  
  
19. <span data-ttu-id="b996f-183">重新啟動**規則引擎更新服務**。</span><span class="sxs-lookup"><span data-stu-id="b996f-183">Restart the **Rule Engine Update Service**.</span></span> <span data-ttu-id="b996f-184">這樣即可**啟動**，然後按一下**執行**、 輸入**services.msc**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b996f-184">Do so by clicking **Start**, clicking **Run**, entering **services.msc**, and clicking **OK**.</span></span> <span data-ttu-id="b996f-185">在**服務 （本機）** 視窗中，以滑鼠右鍵按一下**規則引擎更新服務**，然後按一下 **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="b996f-185">In the **Services (Local)** window, right-click **Rule Engine Update Service**, and then click **Restart**.</span></span>