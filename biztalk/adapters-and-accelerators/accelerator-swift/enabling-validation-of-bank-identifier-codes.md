---
title: 啟用驗證的銀行識別項代碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Bank Identifier Code (BIC), enabling
ms.assetid: d268a892-f304-44cb-b590-28ef359c8d99
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3868906d4f61242b1344a02147e4e71307d67d3
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25967108"
---
# <a name="enabling-validation-of-bank-identifier-codes"></a><span data-ttu-id="5337a-102">啟用驗證的銀行識別項代碼</span><span class="sxs-lookup"><span data-stu-id="5337a-102">Enabling Validation of Bank Identifier Codes</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="5337a-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] 結構描述，請確定銀行識別項代碼 (BICs) SWIFT 交換文件中指定符合 SWIFT 定義 BIC 資料格式。</span><span class="sxs-lookup"><span data-stu-id="5337a-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] schemas ensure that the Bank Identifier Codes (BICs) specified in the SWIFT interchange document conform to the SWIFT-defined BIC data format.</span></span> <span data-ttu-id="5337a-104">A4SWIFT 也支援驗證針對資料庫中客戶指定 BIC 清單 BICs。</span><span class="sxs-lookup"><span data-stu-id="5337a-104">A4SWIFT also supports validating the BICs against a customer-specified BIC list in a database.</span></span>  
  
 <span data-ttu-id="5337a-105">如果您有啟用 BRE 驗證，然後再啟用 BIC 驗證，您可以執行這項驗證。</span><span class="sxs-lookup"><span data-stu-id="5337a-105">You can perform this validation if you have enabled BRE validation and then enabled BIC validation.</span></span>  
  
 <span data-ttu-id="5337a-106">根據預設，A4SWIFT 安裝程式會停用 BRE 驗證。</span><span class="sxs-lookup"><span data-stu-id="5337a-106">By default, A4SWIFT Setup disables BRE validation.</span></span> <span data-ttu-id="5337a-107">若要啟用它，您必須為 true，會使用 A4SWIFT 解譯器的接收管線設定 BRE 驗證組態參數。</span><span class="sxs-lookup"><span data-stu-id="5337a-107">To enable it, you must set the BRE validation configuration parameter to true for a receive pipeline that uses the A4SWIFT disassembler.</span></span> <span data-ttu-id="5337a-108">您也必須執行 BRE 部署公用程式來主要原則和特定的驗證原則部署到要驗證的訊息 (MT*xxx*_Master_policy.xml 和 MT*xxx*_Validation_Policy.xml)。</span><span class="sxs-lookup"><span data-stu-id="5337a-108">You must also run the BRE Deployment Utility to deploy the master policy and validation policy specific to the message to be validated (MT*xxx*_Master_policy.xml and MT*xxx*_Validation_Policy.xml).</span></span> <span data-ttu-id="5337a-109">如需詳細資訊，請參閱[使用 BRE 原則](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md)和[部署 BRE 規則](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="5337a-109">For more information, see [Working with BRE Policies](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md) and [Deploying BRE Rules](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md).</span></span>  
  
 <span data-ttu-id="5337a-110">您已啟用 BRE 驗證之後，您必須使用發行和部署這兩個 BIC 驗證原則 （BIC_Master_Policy.xml 和 BIC_Validation_Policy.xml） 使用 「 規則引擎部署精靈 」。</span><span class="sxs-lookup"><span data-stu-id="5337a-110">After you have enabled BRE validation, you must use publish and deploy both BIC validation policies (BIC_Master_Policy.xml and BIC_Validation_Policy.xml) using the Rules Engine Deployment Wizard.</span></span> <span data-ttu-id="5337a-111">在進行之前，您必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5337a-111">Before doing so, you must do the following:</span></span>  
  
-   <span data-ttu-id="5337a-112">填入資料庫與來自 SWIFT BIC 值。</span><span class="sxs-lookup"><span data-stu-id="5337a-112">Populate the database with BIC values from SWIFT.</span></span> <span data-ttu-id="5337a-113">您可以使用 Bicplus 資料表在 A4SWIFT 資料庫中，A4SWIFT 安裝程式已安裝，或您可以使用您自己自訂的資料庫。</span><span class="sxs-lookup"><span data-stu-id="5337a-113">You can use the Bicplus table in the A4SWIFT database, which is installed by A4SWIFT Setup, or you can use your own custom database.</span></span> <span data-ttu-id="5337a-114">如需詳細資訊，請參閱[管理 Bicplus 資料庫中的資料表 A4SWIFT](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)。</span><span class="sxs-lookup"><span data-stu-id="5337a-114">For more information, see [Managing the Bicplus Table in the A4SWIFT Database](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md).</span></span>  
  
-   <span data-ttu-id="5337a-115">BIC 資料庫設定和啟用 BIC 驗證 BIC 主要原則自訂。</span><span class="sxs-lookup"><span data-stu-id="5337a-115">Set the BIC database and enable BIC validation by customizing the BIC Master Policy.</span></span> <span data-ttu-id="5337a-116">請參閱下列程序。</span><span class="sxs-lookup"><span data-stu-id="5337a-116">See the procedure below.</span></span>  
  
 <span data-ttu-id="5337a-117">為提升效能，您如果不應部署 BIC 驗證原則不需要 BIC 驗證。</span><span class="sxs-lookup"><span data-stu-id="5337a-117">For better performance, you should not deploy the BIC validation policies if BIC validation is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5337a-118">您可以發行和部署 BIC 驗證原則，只有當您已經發行 A4SWIFT_Codelist 和 A4SWIFT_Functions 詞彙。</span><span class="sxs-lookup"><span data-stu-id="5337a-118">You can publish and deploy the BIC validation policy only if you have published the A4SWIFT_Codelist and A4SWIFT_Functions vocabularies.</span></span> <span data-ttu-id="5337a-119">發行這些詞彙 SWIFTSchemas 組件上執行 BRE 部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="5337a-119">Publish these vocabularies by running the BRE Deployment Utility on the SWIFTSchemas assembly.</span></span> <span data-ttu-id="5337a-120">如需詳細資訊，請參閱[第 1 課： 部署相關的商務規則](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="5337a-120">For more information, see [Lesson 1: Deploying the Related Business Rules](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md).</span></span>  
  
### <a name="to-customize-the-bic-master-policy"></a><span data-ttu-id="5337a-121">若要自訂 BIC 主要原則</span><span class="sxs-lookup"><span data-stu-id="5337a-121">To customize the BIC Master Policy</span></span>  
  
1.  <span data-ttu-id="5337a-122">開啟 XML 編輯器 （例如 [記事本])，並瀏覽至 **<*磁碟機*Program Files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則**。</span><span class="sxs-lookup"><span data-stu-id="5337a-122">Open an XML editor (such as Notepad), and browse to **<*drive*Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies**.</span></span>  
  
2.  <span data-ttu-id="5337a-123">開啟**BIC_Master_Policy.xml**。</span><span class="sxs-lookup"><span data-stu-id="5337a-123">Open **BIC_Master_Policy.xml**.</span></span> <span data-ttu-id="5337a-124">下列現有的字串取代為新值。</span><span class="sxs-lookup"><span data-stu-id="5337a-124">Replace the following existing strings with new values.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5337a-125">您必須輸入值 A4SWIFT 資料庫中的任一個 Bicplus 資料表，或您自己自訂的資料庫。</span><span class="sxs-lookup"><span data-stu-id="5337a-125">You must enter values for either the Bicplus table in the A4SWIFT database or your own custom database.</span></span> <span data-ttu-id="5337a-126">A4SWIFT 資料庫不 BIC_Master_Policy.xml 中的預設值。</span><span class="sxs-lookup"><span data-stu-id="5337a-126">The A4SWIFT database is not the default in BIC_Master_Policy.xml.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5337a-127">下列字串必須不包含雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="5337a-127">The following strings must not be contained within double quotes.</span></span>  
  
    |<span data-ttu-id="5337a-128">現有的字串</span><span class="sxs-lookup"><span data-stu-id="5337a-128">Existing string</span></span>|<span data-ttu-id="5337a-129">取代成</span><span class="sxs-lookup"><span data-stu-id="5337a-129">Replace with</span></span>|  
    |---------------------|------------------|  
    |<span data-ttu-id="5337a-130">**指定 SQL SERVER 名稱**</span><span class="sxs-lookup"><span data-stu-id="5337a-130">**SPECIFY SQL SERVER NAME**</span></span>|<span data-ttu-id="5337a-131">名稱[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]包含保存 BIC 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5337a-131">The name of the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] containing the database holding the BIC.</span></span>|  
    |<span data-ttu-id="5337a-132">**指定 BIC 資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="5337a-132">**SPECIFY BIC DATABASE NAME**</span></span>|<span data-ttu-id="5337a-133">包含 BIC 資料表的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="5337a-133">The name of the database that contains the BIC table.</span></span>|  
    |<span data-ttu-id="5337a-134">**指定整合式的安全性值**</span><span class="sxs-lookup"><span data-stu-id="5337a-134">**SPECIFY INTEGRATED SECURITY VALUE**</span></span>|<span data-ttu-id="5337a-135">**SSPI**</span><span class="sxs-lookup"><span data-stu-id="5337a-135">**SSPI**</span></span>|  
  
3.  <span data-ttu-id="5337a-136">儲存修改過的主要原則。</span><span class="sxs-lookup"><span data-stu-id="5337a-136">Save the modified Master Policy.</span></span>  
  
4.  <span data-ttu-id="5337a-137">按一下**啟動**，指向 **所有程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則引擎部署精靈**.</span><span class="sxs-lookup"><span data-stu-id="5337a-137">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rules Engine Deployment Wizard**.</span></span>  
  
5.  <span data-ttu-id="5337a-138">在 歡迎使用 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-138">On the Welcome page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="5337a-139">在部署工作 頁面上，按一下 **匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-139">On the Deployment Task page, click **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="5337a-140">在原則存放區 頁面上，在**SQL Server 名稱**，選取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，其中包含 BizTalk 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5337a-140">On the Policy Store page, in **SQL Server Name**, select the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] that contains your BizTalk databases.</span></span> <span data-ttu-id="5337a-141">在**選取的伺服器上設定資料庫**，選取**BizTalkRuleEngineDb**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-141">In **Configuration Database on selected server**, select **BizTalkRuleEngineDb**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="5337a-142">在 匯入規則引擎原則/詞彙檔案 頁面中，瀏覽至 **<*磁碟機*files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFTMessages\A4SWIFT SRG\<版本\>\Base 原則**，按一下  **BIC_Master_Policy.xml**，按一下 **開啟**，然後按一下  **下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-142">In the Import Rules Engine Policy/Vocabulary file page, browse to **<*drive*\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies**, click **BIC_Master_Policy.xml**, click **Open**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="5337a-143">在上就緒] 頁面上，確認資料，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-143">On the Ready page, verify the data, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="5337a-144">在 匯入原則/詞彙 頁面上，確認命令成功，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-144">On the Importing Policy/Vocabulary page, verify that the command succeeded, and then click **Next**.</span></span>  
  
11. <span data-ttu-id="5337a-145">在正在完成規則引擎部署精靈 頁面上，按一下 **再次執行此精靈**，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="5337a-145">On the Completing the Rules Engine Deployment Wizard page, click **Run this wizard again**, and then click **Finish**.</span></span>  
  
12. <span data-ttu-id="5337a-146">在 歡迎使用 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-146">On the Welcome page, click **Next**.</span></span>  
  
13. <span data-ttu-id="5337a-147">在部署工作 頁面上，按一下 **部署原則**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-147">On the Deployment Task page, click **Deploy Policy**, and then click **Next**.</span></span>  
  
14. <span data-ttu-id="5337a-148">在**原則存放區**頁面上，於**SQL Server 名稱**，選取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，其中包含 BizTalk 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5337a-148">On the **Policy Store** page, in **SQL Server Name**, select the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] that contains your BizTalk databases.</span></span> <span data-ttu-id="5337a-149">在**選取的伺服器上設定資料庫**，選取**BizTalkRuleEngineDb**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-149">In **Configuration Database on selected server**, select **BizTalkRuleEngineDb**, and then click **Next**.</span></span>  
  
15. <span data-ttu-id="5337a-150">在**部署原則**頁面上，選取**BIC_Master_Policy.1.0**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-150">On the **Deploy Policy** page, select **BIC_Master_Policy.1.0**, and then click **Next**.</span></span>  
  
16. <span data-ttu-id="5337a-151">在**準備**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-151">On the **Ready** page, click **Next**.</span></span>  
  
17. <span data-ttu-id="5337a-152">在部署原則 頁面中，如果部署成功後，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="5337a-152">On the Deploying Policy page, if the deployment has succeeded, click **Next**.</span></span> <span data-ttu-id="5337a-153">按一下**再次執行此精靈**，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="5337a-153">Click **Run this wizard again**, and then click **Finish**.</span></span>  
  
18. <span data-ttu-id="5337a-154">重複步驟 5 至 17 **BIC_Validation_Policy.xml**、 輸入**BIC_Validation_Policy**而不是**BIC_Master_Policy**。</span><span class="sxs-lookup"><span data-stu-id="5337a-154">Repeat steps 5 through 17 for **BIC_Validation_Policy.xml**, entering **BIC_Validation_Policy** instead of **BIC_Master_Policy**.</span></span>  
  
19. <span data-ttu-id="5337a-155">結束 「 規則引擎部署精靈 」。</span><span class="sxs-lookup"><span data-stu-id="5337a-155">Exit the Rules Engine Deployment Wizard.</span></span>  
  
20. <span data-ttu-id="5337a-156">按一下**啟動**，指向 **所有程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="5337a-156">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**.</span></span> <span data-ttu-id="5337a-157">確認**原則**清單包含**BIC_Master_Policy**和**BIC_Validation_Policy**下**原則**。</span><span class="sxs-lookup"><span data-stu-id="5337a-157">Verify that the **Policies** list includes **BIC_Master_Policy** and **BIC_Validation_Policy** under **Policies**.</span></span>  
  
21. <span data-ttu-id="5337a-158">展開**版本 1.0 – 已部署**下**BIC_Master_Policy**，然後按一下  **BIC_Master_Rule**。</span><span class="sxs-lookup"><span data-stu-id="5337a-158">Expand **Version 1.0 - Deployed** under **BIC_Master_Policy**, and then click **BIC_Master_Rule**.</span></span>  
  
22. <span data-ttu-id="5337a-159">在 [THEN] 窗格中，確認列出的 SQL 連線屬性正確無誤。</span><span class="sxs-lookup"><span data-stu-id="5337a-159">In the THEN pane, verify that the SQL Connection properties listed are correct.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5337a-160">A4SWIFT 不會拾取對主要 BIC 驗證原則，直到您重新啟動裝載目前設定為使用 SWIFT 解譯器的接收管線的 BizTalk 服務的變更。</span><span class="sxs-lookup"><span data-stu-id="5337a-160">A4SWIFT does not pick up changes made to the master BIC validation policy until you restart the BizTalk service that hosts the receive pipeline that is currently configured to use the SWIFT disassembler.</span></span> <span data-ttu-id="5337a-161">A4SWIFT 驗證通過此管線 BIC 值 BIC 主要原則中指定的 BIC 資料行中所包含的所有文件。</span><span class="sxs-lookup"><span data-stu-id="5337a-161">A4SWIFT validates all documents that pass through this pipeline for the BIC values that are contained in the BIC column specified in the BIC master policy.</span></span> <span data-ttu-id="5337a-162">用來啟動此 BizTalk 服務 (BTSNTSvc.exe) 的使用者帳戶必須具有存取權的 BIC 資料庫和資料表。</span><span class="sxs-lookup"><span data-stu-id="5337a-162">The user account used to start this BizTalk service (BTSNTSvc.exe) must have access to the BIC database and table.</span></span> <span data-ttu-id="5337a-163">為提升安全性，建議您將授與 BIC 資料庫和資料表的唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="5337a-163">For better security, it is recommended that you grant read-only access to the BIC database and table.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5337a-164">如果您使用 Message Repair 和 New Submission，World Wide Web Publishing 服務必須重新啟動 （藉由執行 iisreset.exe） BIC 驗證才能從 InfoPath 工作。</span><span class="sxs-lookup"><span data-stu-id="5337a-164">If you are using Message Repair and New Submission, the World Wide Web Publishing service must be restarted (by running iisreset.exe) for BIC validation to work from InfoPath.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5337a-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5337a-165">See Also</span></span>  
 <span data-ttu-id="5337a-166">[使用 BRE 原則](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md) </span><span class="sxs-lookup"><span data-stu-id="5337a-166">[Working with BRE Policies](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md) </span></span>  
 [<span data-ttu-id="5337a-167">管理 A4SWIFT 資料庫中的 Bicplus 資料表</span><span class="sxs-lookup"><span data-stu-id="5337a-167">Managing the Bicplus Table in the A4SWIFT Database</span></span>](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)