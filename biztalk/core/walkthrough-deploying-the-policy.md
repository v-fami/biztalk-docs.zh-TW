---
title: "逐步解說： 部署的原則 |Microsoft 文件"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 205760e2-9cd4-496f-93cd-0f93bc5d3231
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d235fa0f6882ecd9e180aabd26999b1d7f73390
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-deploying-the-policy"></a><span data-ttu-id="d2b08-102">逐步解說： 部署原則</span><span class="sxs-lookup"><span data-stu-id="d2b08-102">Walkthrough: Deploying the Policy</span></span>
<span data-ttu-id="d2b08-103">本逐步解說提供逐步指示部署**ProcessPurchaseOrder**原則中的下列三種方式：</span><span class="sxs-lookup"><span data-stu-id="d2b08-103">This walkthrough provides step-by-step instructions for deploying the **ProcessPurchaseOrder** policy in the following three ways:</span></span>  
  
-   <span data-ttu-id="d2b08-104">使用商務規則引擎部署精靈，匯出和匯入原則。</span><span class="sxs-lookup"><span data-stu-id="d2b08-104">Exporting and importing the policy by using the Business Rules Engine Deployment Wizard.</span></span>  
  
-   <span data-ttu-id="d2b08-105">使用 BizTalk Server 管理主控台，匯出原則至 XML 檔案，以及從 XML 檔案匯入原則。</span><span class="sxs-lookup"><span data-stu-id="d2b08-105">Exporting the policy to an XML file and importing the policy from an XML file by using the BizTalk Server Administration console.</span></span>  
  
-   <span data-ttu-id="d2b08-106">使用 BizTalk Server 管理主控台，將原則匯出為 MSI 檔案的一部分，以及匯入 MSI 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-106">Exporting the policy as part of an MSI file and importing the MSI file by using BizTalk Server Administration console.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d2b08-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="d2b08-107">Prerequisites</span></span>  
 <span data-ttu-id="d2b08-108">您必須先完成[逐步解說： 追蹤原則執行](../core/walkthrough-tracking-policy-execution.md)逐步解說，然後再執行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="d2b08-108">You must complete the [Walkthrough: Tracking Policy Execution](../core/walkthrough-tracking-policy-execution.md) walkthrough before performing this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="d2b08-109">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="d2b08-109">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="d2b08-110">本主題包含下列三個逐步解說：</span><span class="sxs-lookup"><span data-stu-id="d2b08-110">This topic  contains the following three walkthroughs:</span></span>  
  
1.  <span data-ttu-id="d2b08-111">第一個逐步解說包含部署程序**ProcessPurchaseOrder**原則使用商務規則引擎部署精靈。</span><span class="sxs-lookup"><span data-stu-id="d2b08-111">The first walkthrough contains procedures for deploying the **ProcessPurchaseOrder** policy by using the Business Rules Engine Deployment Wizard.</span></span> <span data-ttu-id="d2b08-112">下表描述此逐步解說中的程序。</span><span class="sxs-lookup"><span data-stu-id="d2b08-112">The following table describes the procedures in this walkthrough.</span></span>  
  
    |<span data-ttu-id="d2b08-113">程序標題</span><span class="sxs-lookup"><span data-stu-id="d2b08-113">Procedure title</span></span>|<span data-ttu-id="d2b08-114">程序說明</span><span class="sxs-lookup"><span data-stu-id="d2b08-114">Procedure description</span></span>|  
    |---------------------|---------------------------|  
    |<span data-ttu-id="d2b08-115">使用商務規則引擎部署精靈匯出 POVocabulary 1.0 和 1.1</span><span class="sxs-lookup"><span data-stu-id="d2b08-115">To export POVocabulary 1.0 and 1.1 by using the Business Rules Engine Deployment Wizard</span></span>|<span data-ttu-id="d2b08-116">提供逐步指示，匯出 1.0 和 1.1 版**POVocabulary**詞彙至 XML 檔案使用商務規則引擎部署精靈。</span><span class="sxs-lookup"><span data-stu-id="d2b08-116">Provides step-by-step instructions for exporting versions 1.0 and 1.1 of the **POVocabulary** vocabulary to XML files by using the Business Rules Engine Deployment Wizard.</span></span>|  
    |<span data-ttu-id="d2b08-117">若要使用商務規則引擎部署精靈匯出 ProcessPurchaseOrder 1.3</span><span class="sxs-lookup"><span data-stu-id="d2b08-117">To export ProcessPurchaseOrder 1.3 by using the Business Rules Engine Deployment Wizard</span></span>|<span data-ttu-id="d2b08-118">提供逐步指示，匯出 1.3 版**ProcessPurchaseOrder**原則至 XML 檔案使用商務規則引擎部署精靈。</span><span class="sxs-lookup"><span data-stu-id="d2b08-118">Provides step-by-step instructions for exporting version 1.3 of the **ProcessPurchaseOrder** policy to an XML file by using the Business Rules Engine Deployment Wizard.</span></span>|  
    |<span data-ttu-id="d2b08-119">若要刪除 ProcessPurchaseOrder 和 POVocabulary</span><span class="sxs-lookup"><span data-stu-id="d2b08-119">To delete ProcessPurchaseOrder and POVocabulary</span></span>|<span data-ttu-id="d2b08-120">提供逐步指示，刪除**ProcessPurchaseOrder**原則和**POVocabulary**詞彙，以便您可以測試匯入 XML 檔案來重新建立它們。</span><span class="sxs-lookup"><span data-stu-id="d2b08-120">Provides step-by-step instructions for deleting the **ProcessPurchaseOrder** policy and **POVocabulary** vocabulary so that you can test importing the XML files to re-create them.</span></span>|  
    |<span data-ttu-id="d2b08-121">若要從 XML 匯入以重新建立 POVocabulary 1.0 和 1.1</span><span class="sxs-lookup"><span data-stu-id="d2b08-121">To import from XML to re-create POVocabulary 1.0 and 1.1</span></span>|<span data-ttu-id="d2b08-122">提供逐步指示，匯入的詞彙 XML 檔案來重新建立第一個程序所建立**POVocabulary**詞彙。</span><span class="sxs-lookup"><span data-stu-id="d2b08-122">Provides step-by-step instructions for importing the vocabulary XML file you created in the first procedure to re-create the **POVocabulary** vocabulary.</span></span>|  
    |<span data-ttu-id="d2b08-123">若要確認 POVocabulary 1.0 和 1.1 已重新建立</span><span class="sxs-lookup"><span data-stu-id="d2b08-123">To verify that POVocabulary 1.0 and 1.1 are re-created</span></span>|<span data-ttu-id="d2b08-124">提供逐步指示，使用 「 商務規則編輯器 」 來驗證該 1.0 和 1.1 版**POVocabulary**重新建立。</span><span class="sxs-lookup"><span data-stu-id="d2b08-124">Provides step-by-step instructions for using the Business Rule Composer to verify that versions 1.0 and 1.1 of **POVocabulary** are re-created.</span></span>|  
    |<span data-ttu-id="d2b08-125">若要從 XML 匯入以重新建立 ProcessPurchaseOrder 1.3</span><span class="sxs-lookup"><span data-stu-id="d2b08-125">To import from XML to re-create ProcessPurchaseOrder 1.3</span></span>|<span data-ttu-id="d2b08-126">提供逐步指示，匯入原則 XML 檔來重新建立 1.3 版的第二個程序所建立**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="d2b08-126">Provides step-by-step instructions for importing the policy XML file you created in the second procedure to re-create version 1.3 of the **ProcessPurchaseOrder** policy.</span></span>|  
    |<span data-ttu-id="d2b08-127">若要確認 ProcessPurchaseOrder 1.3 已重新建立</span><span class="sxs-lookup"><span data-stu-id="d2b08-127">To verify that ProcessPurchaseOrder 1.3 is re-created</span></span>|<span data-ttu-id="d2b08-128">提供逐步指示，使用 「 商務規則編輯器 」 以確認 1.3 版的**ProcessPurchaseOrder**原則都會重新建立。</span><span class="sxs-lookup"><span data-stu-id="d2b08-128">Provides step-by-step instructions for using the Business Rule Composer to verify that version 1.3 of the **ProcessPurchaseOrder** policy is re-created.</span></span>|  
  
2.  <span data-ttu-id="d2b08-129">第二個逐步解說包含部署程序**ProcessPurchaseOrder**使用 XML 檔案的原則匯出從 BizTalk Server 管理主控台下表描述在此程序逐步解說。</span><span class="sxs-lookup"><span data-stu-id="d2b08-129">The second walkthrough contains procedures for deploying the **ProcessPurchaseOrder** policy by using an XML file exported from the BizTalk Server Administration console The following table describes the procedures in this walkthrough.</span></span>  
  
    |<span data-ttu-id="d2b08-130">程序標題</span><span class="sxs-lookup"><span data-stu-id="d2b08-130">Procedure title</span></span>|<span data-ttu-id="d2b08-131">程序說明</span><span class="sxs-lookup"><span data-stu-id="d2b08-131">Procedure description</span></span>|  
    |---------------------|---------------------------|  
    |<span data-ttu-id="d2b08-132">若要匯出 ProcessPurchaseOrder 1.3 原則和 POVocabulary 詞彙至 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="d2b08-132">To export the ProcessPurchaseOrder 1.3 policy and the POVocabulary vocabulary to an XML file</span></span>|<span data-ttu-id="d2b08-133">提供逐步指示，請使用 BizTalk Server 管理主控台匯出**ProcessPurchaseOrder**原則和**POVocabulary**詞彙至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-133">Provides step-by-step instructions for using the BizTalk Server Administration console to export the **ProcessPurchaseOrder** policy and the **POVocabulary** vocabulary to an XML file.</span></span>|  
    |<span data-ttu-id="d2b08-134">若要刪除 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="d2b08-134">To delete the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="d2b08-135">提供逐步指示，刪除**ProcessPurchaseOrder**原則**RuleTestApp**和 「 規則引擎 」 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d2b08-135">Provides step-by-step instructions for deleting the **ProcessPurchaseOrder** policy from **RuleTestApp** and the rule engine database.</span></span>|  
    |<span data-ttu-id="d2b08-136">若要匯入 XML 檔案以重新建立 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="d2b08-136">To import the XML file to re-create the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="d2b08-137">提供逐步指示，匯入 XML 檔案中重新建立的第一個程序匯出**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="d2b08-137">Provides step-by-step instructions for importing the XML file you exported in the first procedure to re-create the **ProcessPurchaseOrder** policy.</span></span>|  
    |<span data-ttu-id="d2b08-138">若要新增 ProcessPurchaseOrder 原則至 RuleTestApp 應用程式</span><span class="sxs-lookup"><span data-stu-id="d2b08-138">To add the ProcessPurchaseOrder policy to the RuleTestApp application</span></span>|<span data-ttu-id="d2b08-139">提供逐步指示，加入**ProcessPurchaseOrder**原則**RuleTestApp**應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2b08-139">Provides step-by-step instructions for adding the **ProcessPurchaseOrder** policy to the **RuleTestApp** application.</span></span>|  
  
3.  <span data-ttu-id="d2b08-140">第三個逐步解說包含部署程序**ProcessPurchaseOrder**從 BizTalk Server 管理主控台匯出的原則使用 MSI 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-140">The third walkthrough contains procedures for deploying the **ProcessPurchaseOrder** policy by using an MSI file exported from the BizTalk Server Administration console.</span></span> <span data-ttu-id="d2b08-141">下表描述此逐步解說中的程序。</span><span class="sxs-lookup"><span data-stu-id="d2b08-141">The following table describes the procedures in this walkthrough.</span></span>  
  
    |<span data-ttu-id="d2b08-142">程序標題</span><span class="sxs-lookup"><span data-stu-id="d2b08-142">Procedure title</span></span>|<span data-ttu-id="d2b08-143">程序的相關逐步指示</span><span class="sxs-lookup"><span data-stu-id="d2b08-143">Procedure has step-by-step instructions for</span></span>|  
    |---------------------|---------------------------------------------------|  
    |<span data-ttu-id="d2b08-144">若要匯出 RuleTestApp 應用程式至 MSI 檔案</span><span class="sxs-lookup"><span data-stu-id="d2b08-144">To export the RuleTestApp application to an MSI file</span></span>|<span data-ttu-id="d2b08-145">提供逐步指示，匯出**RuleTestApp**應用程式至 MSI 檔案，以便稍後用來重新建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2b08-145">Provides step-by-step instructions for exporting the **RuleTestApp** application to an MSI file, which is used later to re-create the application.</span></span>|  
    |<span data-ttu-id="d2b08-146">若要刪除 RuleTestApp 應用程式</span><span class="sxs-lookup"><span data-stu-id="d2b08-146">To delete the RuleTestApp application</span></span>|<span data-ttu-id="d2b08-147">提供逐步指示，刪除**RuleTestApp**應用程式，以便您可以測試使用 MSI 檔案重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2b08-147">Provides step-by-step instructions for deleting the **RuleTestApp** application so that you can test re-creating the application by using the MSI file.</span></span>|  
    |<span data-ttu-id="d2b08-148">若要確認 ProcessPurchaseOrder 原則和 POVocabulary 詞彙已刪除</span><span class="sxs-lookup"><span data-stu-id="d2b08-148">To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are deleted</span></span>|<span data-ttu-id="d2b08-149">提供逐步指示，使用 「 商務規則編輯器 」 可讓您確認**ProcessPurchaseOrder**原則和 POVocabulary 詞彙已刪除。</span><span class="sxs-lookup"><span data-stu-id="d2b08-149">Provides step-by-step instructions for using the Business Rule Composer to verify that the **ProcessPurchaseOrder** policy and POVocabulary vocabulary are deleted.</span></span>|  
    |<span data-ttu-id="d2b08-150">若要匯入 MSI 檔案以重新建立 RuleTestApp 應用程式</span><span class="sxs-lookup"><span data-stu-id="d2b08-150">To import the MSI file to re-create the RuleTestApp application</span></span>|<span data-ttu-id="d2b08-151">提供使用 BizTalk Server 管理主控台匯入 MSI 檔案的逐步指示來重新建立**RuleTestApp**應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2b08-151">Provides step-by-step instructions for using the BizTalk Server Administration console to import the MSI file to re-create the **RuleTestApp** application.</span></span>|  
    |<span data-ttu-id="d2b08-152">若要確認 ProcessPurchaseOrder 原則已新增至 RuleTestApp</span><span class="sxs-lookup"><span data-stu-id="d2b08-152">To verify that the ProcessPurchaseOrder policy is added to RuleTestApp</span></span>|<span data-ttu-id="d2b08-153">提供逐步指示，使用 BizTalk Server 管理主控台，確認**ProcessPurchaseOrder**原則新增至**RuleTestApp**應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2b08-153">Provides step-by-step instructions for using the BizTalk Server Administration console to verify that the **ProcessPurchaseOrder** policy is added to the **RuleTestApp** application.</span></span>|  
    |<span data-ttu-id="d2b08-154">若要確認 ProcessPurchaseOrder 原則和 POVocabulary 詞彙已重新建立</span><span class="sxs-lookup"><span data-stu-id="d2b08-154">To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are re-created</span></span>|<span data-ttu-id="d2b08-155">提供逐步指示，使用 「 商務規則編輯器 」 可讓您確認**ProcessPurchaseOrder**原則和**POVocabulary**詞彙時都會重新建立。</span><span class="sxs-lookup"><span data-stu-id="d2b08-155">Provides step-by-step instructions for using the Business Rule Composer to verify that the **ProcessPurchaseOrder** policy and **POVocabulary** vocabulary are re-created.</span></span>|  
    |<span data-ttu-id="d2b08-156">測試方案</span><span class="sxs-lookup"><span data-stu-id="d2b08-156">To test the solution</span></span>|<span data-ttu-id="d2b08-157">提供測試方案的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="d2b08-157">Provides step-by-step instructions for testing the solution.</span></span>|  
  
## <a name="procedures-for-deploying-the-processpurchaseorder-policy-by-using-the-business-rules-engine-deployment-wizard"></a><span data-ttu-id="d2b08-158">使用商務規則引擎部署精靈部署 ProcessPurchaseOrder 原則的程序</span><span class="sxs-lookup"><span data-stu-id="d2b08-158">Procedures for Deploying the ProcessPurchaseOrder Policy by Using the Business Rules Engine Deployment Wizard</span></span>  
  
#### <a name="to-export-povocabulary-10-and-11-by-using-the-business-rules-engine-deployment-wizard"></a><span data-ttu-id="d2b08-159">使用商務規則引擎部署精靈匯出 POVocabulary 1.0 和 1.1</span><span class="sxs-lookup"><span data-stu-id="d2b08-159">To export POVocabulary 1.0 and 1.1 by using the Business Rules Engine Deployment Wizard</span></span>  
  
1.  <span data-ttu-id="d2b08-160">在**啟動**功能表中，開啟**商務規則引擎部署精靈**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-160">On the **Start** menu, open **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-161">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d2b08-161">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d2b08-162">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-162">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d2b08-163">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-163">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="d2b08-164">在**部署工作**頁面上，選取**匯出原則/詞彙至檔案從資料庫**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-164">On the **Deployment Task** page, select **Export Policy/Vocabulary to file from database**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="d2b08-165">在**原則存放區**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-165">On the **Policy Store** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="d2b08-166">在**匯出原則/詞彙**頁面上，按一下**詞彙**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-166">On the **Export Policy/Vocabulary** page, click **Vocabulary**.</span></span>  
  
6.  <span data-ttu-id="d2b08-167">選取**POVocabulary.1.0**從下拉式清單中，為**原則/詞彙**中，輸入或瀏覽以指定 XML 輸出檔名稱做為**C:\BRE-walkthroughs\POVocabulary10.xml**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-167">Select **POVocabulary.1.0** from the drop-down list for **Policy/Vocabulary**, type or browse to specify the XML output file name as **C:\BRE-walkthroughs\POVocabulary10.xml**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="d2b08-168">在**準備**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-168">On the **Ready** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="d2b08-169">在**匯出原則/詞彙**頁面上，按一下**下一步。**</span><span class="sxs-lookup"><span data-stu-id="d2b08-169">On the **Exporting Policy/Vocabulary** page, click **Next.**</span></span>  
  
9. <span data-ttu-id="d2b08-170">選取**再次執行此精靈**，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-170">Select **Run this wizard again**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="d2b08-171">因為您選取**再次執行此精靈**，精靈的第一個畫面會再次出現。</span><span class="sxs-lookup"><span data-stu-id="d2b08-171">Because you selected **Run this wizard again**, the first screen of the wizard appears again.</span></span>  
  
10. <span data-ttu-id="d2b08-172">重複步驟 2 至 6。</span><span class="sxs-lookup"><span data-stu-id="d2b08-172">Repeat steps 2-6.</span></span>  
  
11. <span data-ttu-id="d2b08-173">選取**POVocabulary.1.1**從下拉式清單中，為**原則/詞彙**中，輸入或瀏覽以指定 XML 輸出檔名稱做為**C:\BRE-walkthroughs\POVocabulary11.xml**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-173">Select **POVocabulary.1.1** from the drop-down list for **Policy/Vocabulary**, type or browse to specify the XML output file name as **C:\BRE-walkthroughs\POVocabulary11.xml**, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="d2b08-174">重複步驟 8 和 9。</span><span class="sxs-lookup"><span data-stu-id="d2b08-174">Repeat steps 8 and 9.</span></span>  
  
13. <span data-ttu-id="d2b08-175">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-175">Click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-176">您需要匯出 1.0 和 1.1 版**POVocabulary**因為**ProcessPurchaseOrder** 1.3 相依於這兩個版本**POVocabulary**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-176">You need to export both version 1.0 and version 1.1 of **POVocabulary** because **ProcessPurchaseOrder** 1.3 depends on both versions of **POVocabulary**.</span></span> <span data-ttu-id="d2b08-177">**允許的項目數目上限**從 1.1 版詞彙使用定義。</span><span class="sxs-lookup"><span data-stu-id="d2b08-177">The **Maximum number of items allowed** definition is used from version 1.1 of the vocabulary.</span></span> <span data-ttu-id="d2b08-178">**要求數量**和**Request Status**定義所使用的 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="d2b08-178">The **Requested Quantity** and **Request Status** definitions are used from version 1.0.</span></span>  
  
#### <a name="to-export-processpurchaseorder-13-by-using-the-business-rule-engine-deployment-wizard"></a><span data-ttu-id="d2b08-179">若要使用商務規則引擎部署精靈匯出 ProcessPurchaseOrder 1.3</span><span class="sxs-lookup"><span data-stu-id="d2b08-179">To export ProcessPurchaseOrder 1.3 by using the Business Rule Engine Deployment Wizard</span></span>  
  
1.  <span data-ttu-id="d2b08-180">在**啟動**功能表中，開啟**商務規則引擎部署精靈**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-180">On the **Start** menu, open **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-181">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d2b08-181">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d2b08-182">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-182">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d2b08-183">在**歡迎使用規則引擎部署精靈**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-183">On the **Welcome to the Rules Engine Deployment Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="d2b08-184">選取**匯出原則/詞彙至檔案從資料庫**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-184">Select **Export Policy/Vocabulary to file from database**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="d2b08-185">在**原則存放區**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-185">On the **Policy Store** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="d2b08-186">確認**原則**選取選項。</span><span class="sxs-lookup"><span data-stu-id="d2b08-186">Verify that the **Policy** option is selected.</span></span>  
  
6.  <span data-ttu-id="d2b08-187">選取**ProcessPurchaseOrder.1.3**從下拉式清單中，為**原則/詞彙**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-187">Select **ProcessPurchaseOrder.1.3** from the drop-down list for **Policy/Vocabulary**.</span></span>  
  
7.  <span data-ttu-id="d2b08-188">輸入或瀏覽以指定**C:\BRE-walkthroughs\ProcessPOPolicy13.xml**做為 XML 輸出檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d2b08-188">Type or browse to specify **C:\BRE-walkthroughs\ProcessPOPolicy13.xml** as the XML output file name.</span></span>  
  
8.  <span data-ttu-id="d2b08-189">按一下**下一步**三次，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-189">Click **Next** thrice, and then click **Finish**.</span></span>  
  
#### <a name="to-delete-processpurchaseorder-and-povocabulary"></a><span data-ttu-id="d2b08-190">若要刪除 ProcessPurchaseOrder 和 POVocabulary</span><span class="sxs-lookup"><span data-stu-id="d2b08-190">To delete ProcessPurchaseOrder and POVocabulary</span></span>  
  
1.  <span data-ttu-id="d2b08-191">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-191">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="d2b08-192">如果您有商務規則編輯器已開啟，請按 F5 或按一下**重新載入**上**檔案**重新整理的功能表。</span><span class="sxs-lookup"><span data-stu-id="d2b08-192">If you have Business Rule Composer already open, press F5 or click **Reload** on the **File** menu to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-193">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d2b08-193">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d2b08-194">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-194">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d2b08-195">在 原則總管 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **刪除**.</span><span class="sxs-lookup"><span data-stu-id="d2b08-195">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0**, and then click **Delete**.</span></span> <span data-ttu-id="d2b08-196">如果**刪除**是停用，以滑鼠右鍵按一下**1.0 版**，然後按一下 **解除部署**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-196">If **Delete** is disabled, right-click **Version 1.0**, and then click **Undeploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-197">已部署的原則版本無法加以刪除。</span><span class="sxs-lookup"><span data-stu-id="d2b08-197">The deployed policy versions cannot be deleted.</span></span> <span data-ttu-id="d2b08-198">您必須先解除原則的部署，才能刪除原則版本。</span><span class="sxs-lookup"><span data-stu-id="d2b08-198">You must undeploy a policy before deleting a policy version.</span></span>  
  
3.  <span data-ttu-id="d2b08-199">按一下**是**確認訊息方塊中。</span><span class="sxs-lookup"><span data-stu-id="d2b08-199">Click **Yes** in the confirmation message box.</span></span>  
  
4.  <span data-ttu-id="d2b08-200">重複步驟 2 和 3 以刪除**1.1 版**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-200">Repeat steps 2 and 3 to delete **Version 1.1**.</span></span>  
  
5.  <span data-ttu-id="d2b08-201">重複步驟 2 和 3 以刪除**1.2 版**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-201">Repeat steps 2 and 3 to delete **Version 1.2**.</span></span>  
  
6.  <span data-ttu-id="d2b08-202">以滑鼠右鍵按一下**1.3 版-部署**，然後按一下 **解除部署**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-202">Right-click **Version 1.3 - Deployed**, and then click **Undeploy**.</span></span> <span data-ttu-id="d2b08-203">如果**解除部署**選項已停用、 略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="d2b08-203">If the **Undeploy** option is disabled, ignore this step.</span></span>  
  
7.  <span data-ttu-id="d2b08-204">在 事實總管 視窗中，依序展開**詞彙**，以滑鼠右鍵按一下**POVocabulary**，然後按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-204">In the Facts Explorer window, expand **Vocabularies**, right-click **POVocabulary**, and then click **Delete**.</span></span>  
  
#### <a name="to-import-from-xml-to-re-create-povocabulary-10-and-11"></a><span data-ttu-id="d2b08-205">若要從 XML 匯入以重新建立 POVocabulary 1.0 和 1.1</span><span class="sxs-lookup"><span data-stu-id="d2b08-205">To import from XML to re-create POVocabulary 1.0 and 1.1</span></span>  
  
1.  <span data-ttu-id="d2b08-206">在**啟動**功能表中，開啟**商務規則引擎部署精靈**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-206">On the **Start** menu, open **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-207">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d2b08-207">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d2b08-208">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-208">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d2b08-209">在**歡迎使用規則引擎部署精靈**，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-209">On the **Welcome to the Rules Engine Deployment Wizard**, click **Next**.</span></span>  
  
3.  <span data-ttu-id="d2b08-210">在**部署工作**頁面上，選取**匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-210">On the **Deployment Task** page, select **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="d2b08-211">在**原則存放區**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-211">On the **Policy Store** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="d2b08-212">瀏覽並選取**POVocabulary10.xml**您在第一個程序中建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-212">Browse and select the **POVocabulary10.xml** file you created in the first procedure.</span></span>  
  
6.  <span data-ttu-id="d2b08-213">按一下**開啟**或按兩下**POVocabulary10.xml**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-213">Click **Open** or double-click **POVocabulary10.xml**.</span></span>  
  
7.  <span data-ttu-id="d2b08-214">按一下**下一步**商務規則引擎部署精靈 」 中。</span><span class="sxs-lookup"><span data-stu-id="d2b08-214">Click **Next** in the Business Rules Engine Deployment Wizard.</span></span>  
  
8.  <span data-ttu-id="d2b08-215">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-215">Click **Next**.</span></span>  
  
9. <span data-ttu-id="d2b08-216">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-216">Click **Next**.</span></span>  
  
10. <span data-ttu-id="d2b08-217">選取**再次執行此精靈**，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-217">Select **Run this wizard again**, and then click **Finish**.</span></span>  
  
11. <span data-ttu-id="d2b08-218">重複步驟 2 至 9 以匯入**POVocabulary11.xml**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-218">Repeat steps 2-9 to import **POVocabulary11.xml**.</span></span>  
  
12. <span data-ttu-id="d2b08-219">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-219">Click **Finish**.</span></span>  
  
#### <a name="to-verify-that-povocabulary-10-and-11-are-re-created"></a><span data-ttu-id="d2b08-220">若要確認 POVocabulary 1.0 和 1.1 已重新建立</span><span class="sxs-lookup"><span data-stu-id="d2b08-220">To verify that POVocabulary 1.0 and 1.1 are re-created</span></span>  
  
1.  <span data-ttu-id="d2b08-221">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-221">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="d2b08-222">如果您有已經開啟它，請按 F5 或按一下**重新載入**上**檔案**重新整理的功能表。</span><span class="sxs-lookup"><span data-stu-id="d2b08-222">If you have it already open, press F5 or click **Reload** on the **File** menu to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-223">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d2b08-223">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d2b08-224">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-224">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d2b08-225">在 事實總管 視窗中，按一下**詞彙** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d2b08-225">In the Facts Explorer window, click the **Vocabularies** tab.</span></span>  
  
3.  <span data-ttu-id="d2b08-226">展開**詞彙**，而且您應該會看到**POVocabulary**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-226">Expand **Vocabularies**, and you should see **POVocabulary**.</span></span>  
  
4.  <span data-ttu-id="d2b08-227">展開**POVocabulary**，而且您應該會看到**1.0 版**和**1.1 版**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-227">Expand **POVocabulary**, and you should see **Version 1.0** and **Version 1.1**.</span></span>  
  
#### <a name="to-import-from-xml-to-re-create-processpurchaseorder-13"></a><span data-ttu-id="d2b08-228">若要從 XML 匯入以重新建立 ProcessPurchaseOrder 1.3</span><span class="sxs-lookup"><span data-stu-id="d2b08-228">To import from XML to re-create ProcessPurchaseOrder 1.3</span></span>  
  
1.  <span data-ttu-id="d2b08-229">在**啟動**功能表中，開啟**商務規則引擎部署精靈**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-229">On the **Start** menu, open **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-230">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d2b08-230">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d2b08-231">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-231">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d2b08-232">在**歡迎使用規則引擎部署精靈**，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-232">On the **Welcome to the Rules Engine Deployment Wizard**, click **Next**.</span></span>  
  
3.  <span data-ttu-id="d2b08-233">在**部署工作**頁面上，選取**匯入並發佈原則/詞彙至資料庫，從檔案的 fileto 資料庫**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-233">On the **Deployment Task** page, select **Import and publish Policy/Vocabulary to database from fileto database from file**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="d2b08-234">在**原則存放區**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-234">On the **Policy Store** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="d2b08-235">瀏覽並選取**ProcessPOPolicy13.xml**您稍早在本逐步解說中建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-235">Browse and select the **ProcessPOPolicy13.xml** file you created earlier in this walkthrough.</span></span>  
  
6.  <span data-ttu-id="d2b08-236">按一下**開啟**或按兩下**ProcessPOPolicy13.xml**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-236">Click **Open** or double-click **ProcessPOPolicy13.xml**.</span></span>  
  
7.  <span data-ttu-id="d2b08-237">按一下**下一步**商務規則引擎部署精靈 」 中。</span><span class="sxs-lookup"><span data-stu-id="d2b08-237">Click **Next** in the Business Rules Engine Deployment Wizard.</span></span>  
  
8.  <span data-ttu-id="d2b08-238">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-238">Click **Next**.</span></span>  
  
9. <span data-ttu-id="d2b08-239">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-239">Click **Next**, and then click **Finish**.</span></span>  
  
#### <a name="to-verify-that-processpurchaseorder-13-is-re-created"></a><span data-ttu-id="d2b08-240">若要確認 ProcessPurchaseOrder 1.3 已重新建立</span><span class="sxs-lookup"><span data-stu-id="d2b08-240">To verify that ProcessPurchaseOrder 1.3 is re-created</span></span>  
  
1.  <span data-ttu-id="d2b08-241">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-241">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="d2b08-242">如果您有已經開啟它，請按 F5 或按一下**重新載入**上**檔案**重新整理的功能表。</span><span class="sxs-lookup"><span data-stu-id="d2b08-242">If you have it already open, press F5 or click **Reload** on the **File** menu to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-243">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d2b08-243">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d2b08-244">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-244">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d2b08-245">在 [原則總管] 視窗中，依序展開**原則**和您應該會看到**ProcessPurchaseOrder**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-245">In the Policy Explorer window, expand **Policies** and you should see **ProcessPurchaseOrder**.</span></span>  
  
3.  <span data-ttu-id="d2b08-246">展開**ProcessPurchaseOrder**和您應該會看到**1.3 版-已發佈**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-246">Expand **ProcessPurchaseOrder** and you should see **Version 1.3 - Published**.</span></span>  
  
## <a name="procedures-for-deploying-the-policy-by-using-an-xml-file-exported-from-the-biztalk-server-administration-console"></a><span data-ttu-id="d2b08-247">使用由 BizTalk Server 管理主控台匯出的 XML 檔案以部署原則的程序</span><span class="sxs-lookup"><span data-stu-id="d2b08-247">Procedures for Deploying the Policy by Using an XML file Exported from the BizTalk Server Administration Console</span></span>  
  
#### <a name="to-export-the-processpurchaseorder-13-policy-and-the-povocabulary-vocabulary-to-an-xml-file"></a><span data-ttu-id="d2b08-248">若要匯出 ProcessPurchaseOrder 1.3 原則和 POVocabulary 詞彙至 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="d2b08-248">To export the ProcessPurchaseOrder 1.3 policy and the POVocabulary vocabulary to an XML file</span></span>  
  
1.  <span data-ttu-id="d2b08-249">在**啟動**功能表中，開啟[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d2b08-249">On the **Start** menu, open [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span> <span data-ttu-id="d2b08-250">如果您已經開啟此工具，請按 F5 重新整理。</span><span class="sxs-lookup"><span data-stu-id="d2b08-250">If you have the tool already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="d2b08-251">展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**RuleTestApp**.</span><span class="sxs-lookup"><span data-stu-id="d2b08-251">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Applications**, and then expand **RuleTestApp**.</span></span>  
  
3.  <span data-ttu-id="d2b08-252">按一下**原則**，並確定您看到 ProcessPurchaseOrder 1.3 原則清單中的。</span><span class="sxs-lookup"><span data-stu-id="d2b08-252">Click **Policies** and make sure that you see the ProcessPurchaseOrder 1.3 policy in the list.</span></span>  
  
4.  <span data-ttu-id="d2b08-253">以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後按一下 **匯出**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-253">Right-click **ProcessPurchaseOrder**, and then click **Export**.</span></span>  
  
5.  <span data-ttu-id="d2b08-254">在**匯出原則**對話方塊方塊中，請確定**ProcessPurchaseOrder**原則和**POVocabulary**已選取。</span><span class="sxs-lookup"><span data-stu-id="d2b08-254">In the **Export Policies** dialog box, make sure the **ProcessPurchaseOrder** policy and the **POVocabulary** are selected.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-255">您可以匯出至 XML 檔案的應用程式中的所有原則，以滑鼠右鍵按一下**RuleTest** ，然後按一下 **都匯出**上**原則**功能表。</span><span class="sxs-lookup"><span data-stu-id="d2b08-255">You can export all the policies in an application to an XML file by right-clicking **RuleTest** and then clicking **Export** on the **Policies** menu.</span></span> <span data-ttu-id="d2b08-256">這樣就可以將此應用程式使用的所有原則和詞彙匯出至單一 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-256">This way you can export all the policies and vocabulary used by this application to a single XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-257">您可以匯出至 XML 檔案的所有應用程式中的所有原則，以滑鼠右鍵按一下**應用程式**節點，然後按一下**都匯出**上**原則**功能表。</span><span class="sxs-lookup"><span data-stu-id="d2b08-257">You can export all the policies in all the applications to an XML file by right-clicking the **Applications** node and then clicking **Export** on the **Policies** menu.</span></span> <span data-ttu-id="d2b08-258">這樣就可以將所有應用程式使用的所有原則和詞彙匯出至單一 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-258">This way you can export all the policies and vocabularies used by all the applications into a single XML file.</span></span>  
  
6.  <span data-ttu-id="d2b08-259">指定輸出 XML 檔案名稱 (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**)，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-259">Specify an output XML file name (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**), and then click **Ok**.</span></span>  
  
#### <a name="to-delete-the-processpurchaseorder-policy"></a><span data-ttu-id="d2b08-260">若要刪除 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="d2b08-260">To delete the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="d2b08-261">在 BizTalk Server 管理，以滑鼠右鍵按一下**ProcessPurchaseOrder**在清單中，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-261">In BizTalk Server Administration, right-click **ProcessPurchaseOrder** in the list, and then click **Remove**.</span></span>  
  
2.  <span data-ttu-id="d2b08-262">按一下**是**中**移除原則**訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="d2b08-262">Click **Yes** in the **Remove Policy** message box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-263">如果原則處於已部署狀態，您無法將它移除。</span><span class="sxs-lookup"><span data-stu-id="d2b08-263">If the policy is in the deployed state, it cannot be removed.</span></span> <span data-ttu-id="d2b08-264">以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後按一下 **解除部署**解除部署原則。</span><span class="sxs-lookup"><span data-stu-id="d2b08-264">Right-click **ProcessPurchaseOrder**, and then click **Undeploy** to undeploy the policy.</span></span> <span data-ttu-id="d2b08-265">**移除**解除部署原則時，目前使用功能表項目。</span><span class="sxs-lookup"><span data-stu-id="d2b08-265">The **Remove** menu item is available when the policy is undeployed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-266">詞彙**ProcessPurchaseOrder**原則而定，在此情況下**POVocabulary**，也會一併刪除。</span><span class="sxs-lookup"><span data-stu-id="d2b08-266">The vocabularies on which the **ProcessPurchaseOrder** policy depends, in this case **POVocabulary**, are also deleted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-267">當您從應用程式移除原則時，也會從規則引擎資料庫刪除它所依存的原則和詞彙，而不只是從應用程式刪除。</span><span class="sxs-lookup"><span data-stu-id="d2b08-267">When you remove a policy from an application, the policy and the vocabularies that it depends on are deleted from the rule engine database as well, not just from the application.</span></span>  
  
#### <a name="to-import-the-xml-file-to-re-create-the-processpurchaseorder-policy"></a><span data-ttu-id="d2b08-268">若要匯入 XML 檔案以重新建立 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="d2b08-268">To import the XML file to re-create the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="d2b08-269">在 BizTalk Server 管理，依序展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後展開**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-269">In BizTalk Server Administration, expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**.</span></span>  
  
2.  <span data-ttu-id="d2b08-270">以滑鼠右鍵按一下**應用程式**，指向 **匯入**，然後按一下 **原則**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-270">Right-click **Applications**, point to **Import**, and then click **Policies**.</span></span>  
  
3.  <span data-ttu-id="d2b08-271">瀏覽，然後按兩下 XML 檔案 (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**) 在第一個程序中所建立。</span><span class="sxs-lookup"><span data-stu-id="d2b08-271">Browse, and double-click the XML file (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**) that you created in the first procedure.</span></span>  
  
4.  <span data-ttu-id="d2b08-272">展開**\<所有成品\>**下**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-272">Expand **\<All Artifacts\>** under **Applications**.</span></span>  
  
5.  <span data-ttu-id="d2b08-273">按一下**原則**，而且您應該會看見 1.3 版**ProcessPurchaseOrder**原則清單中的。</span><span class="sxs-lookup"><span data-stu-id="d2b08-273">Click **Policies**, and you should see version 1.3 of the **ProcessPurchaseOrder** policy in the list.</span></span>  
  
6.  <span data-ttu-id="d2b08-274">按 F5 重新整理檢視。</span><span class="sxs-lookup"><span data-stu-id="d2b08-274">Press F5 to refresh the view.</span></span> <span data-ttu-id="d2b08-275">**ProcessPurchaseOrder**原則應該處於**未發行**狀態。</span><span class="sxs-lookup"><span data-stu-id="d2b08-275">The **ProcessPurchaseOrder** policy should be in the **Not Published** state.</span></span>  
  
#### <a name="to-add-the-processpurchaseorder-policy-to-the-ruletestapp-application"></a><span data-ttu-id="d2b08-276">若要新增 ProcessPurchaseOrder 原則至 RuleTestApp 應用程式</span><span class="sxs-lookup"><span data-stu-id="d2b08-276">To add the ProcessPurchaseOrder policy to the RuleTestApp application</span></span>  
  
1.  <span data-ttu-id="d2b08-277">在 BizTalk Server 管理，以滑鼠右鍵按一下**ProcessPurchaseOrder**原則，然後再按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-277">In BizTalk Server Administration, right-click **ProcessPurchaseOrder** policy, and then click **Publish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-278">只有已發佈的原則才可以加入至 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2b08-278">Only published policies can be added to a BizTalk application.</span></span>  
  
2.  <span data-ttu-id="d2b08-279">在**應用程式**] 節點，展開 [ **RuleTestApp**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-279">In the **Applications** node, expand **RuleTestApp**.</span></span>  
  
3.  <span data-ttu-id="d2b08-280">按一下**原則**中**RuleTestApp**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-280">Click **Policies** in **RuleTestApp**.</span></span>  
  
4.  <span data-ttu-id="d2b08-281">以滑鼠右鍵按一下右邊清單中，指向**新增**，然後按一下 **原則**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-281">Right-click in the list on the right, point to **Add**, and then click **Policy**.</span></span>  
  
5.  <span data-ttu-id="d2b08-282">展開**ProcessPurchaseOrder**節點中，選取的核取方塊**（已發佈） 1.3 版**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-282">Expand the **ProcessPurchaseOrder** node, select the check box for **Version 1.3 (Published)**, and then click **OK**.</span></span> <span data-ttu-id="d2b08-283">執行個體時提供 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="d2b08-283">.</span></span>  
  
6.  <span data-ttu-id="d2b08-284">以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-284">Right-click **ProcessPurchaseOrder**, and then click **Deploy**.</span></span> <span data-ttu-id="d2b08-285">如果您沒有看到**ProcessPurchaseOrder**在清單中，按下 F5 以重新整理檢視。</span><span class="sxs-lookup"><span data-stu-id="d2b08-285">If you do not see **ProcessPurchaseOrder** in the list, press F5 to refresh the view.</span></span>  
  
7.  <span data-ttu-id="d2b08-286">按一下**是**確認訊息方塊中。</span><span class="sxs-lookup"><span data-stu-id="d2b08-286">Click **Yes** in the confirmation message box.</span></span>  
  
## <a name="procedures-for-deploying-the-policy-by-using-an-msi-file"></a><span data-ttu-id="d2b08-287">使用 MSI 檔案部署原則的程序</span><span class="sxs-lookup"><span data-stu-id="d2b08-287">Procedures for Deploying the Policy by Using an MSI File</span></span>  
  
#### <a name="to-export-the-ruletestapp-application-to-an-msi-file"></a><span data-ttu-id="d2b08-288">若要匯出 RuleTestApp 應用程式至 MSI 檔案</span><span class="sxs-lookup"><span data-stu-id="d2b08-288">To export the RuleTestApp application to an MSI file</span></span>  
  
1.  <span data-ttu-id="d2b08-289">在**啟動**功能表中，開啟**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-289">On the **Start** menu, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="d2b08-290">如果您已經開啟此工具，請按 F5 重新整理。</span><span class="sxs-lookup"><span data-stu-id="d2b08-290">If you have the tool already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="d2b08-291">展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-291">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="d2b08-292">以滑鼠右鍵按一下**RuleTestApp**，指向 **匯出**，然後按一下  **MSI 檔案**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-292">Right-click **RuleTestApp**, point to **Export**, and then click **MSI file**.</span></span>  
  
4.  <span data-ttu-id="d2b08-293">在**歡迎使用匯出 MSI 檔案精靈**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-293">On the **Welcome to the Export MSI File Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="d2b08-294">在**選取資源**頁面上，檢閱所有的預設選項，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-294">On the **Select Resources** page, review all the default options, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="d2b08-295">在**指定 IIS 主控件**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-295">On the **Specify IIS Hosts** page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="d2b08-296">在**相依性**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-296">On the **Dependencies** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="d2b08-297">在**目的地**頁面上，指定的目錄和名稱為 MSI **C:\BRE-Walkthroughs\RuleTestApp.msi**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-297">On the **Destination** page, specify the directory and name for the MSI as **C:\BRE-Walkthroughs\RuleTestApp.msi**.</span></span>  
  
9. <span data-ttu-id="d2b08-298">按一下 **[匯出]**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-298">Click **Export**.</span></span>  
  
10. <span data-ttu-id="d2b08-299">在**摘要**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-299">On the **Summary** page, click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-300">當您匯出 RuleTestApp 應用程式時，應用程式使用的原則和詞彙也會匯出至 MSI 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-300">When you export the RuleTestApp application, the policies and vocabularies used by the application are also exported in the MSI file.</span></span> <span data-ttu-id="d2b08-301">稍後匯入 MSI 檔案時，便會重新建立所有的詞彙、原則和應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2b08-301">Later, when you import the MSI file, the vocabulary, policy, and application are all re-created.</span></span>  
  
#### <a name="to-delete-the-ruletestapp-application"></a><span data-ttu-id="d2b08-302">若要刪除 RuleTestApp 應用程式</span><span class="sxs-lookup"><span data-stu-id="d2b08-302">To delete the RuleTestApp application</span></span>  
  
1.  <span data-ttu-id="d2b08-303">在 BizTalk Server 管理，以滑鼠右鍵按一下**RuleTestApp**，並檢查**刪除**功能表是啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="d2b08-303">In BizTalk Server Administration, right-click **RuleTestApp**, and check if the **Delete** menu is enabled or disabled.</span></span>  
  
2.  <span data-ttu-id="d2b08-304">如果**刪除**是停用，以滑鼠右鍵按一下**RuleTestApp**，按一下 **停止**，選取**完全停止-終止執行個體**，然後按一下  **停止**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-304">If **Delete** is disabled, right-click **RuleTestApp**, click **Stop**, select **Full Stop - Terminate Instance**, and then click **Stop**.</span></span>  
  
3.  <span data-ttu-id="d2b08-305">以滑鼠右鍵按一下**RuleTestApp**，然後按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-305">Right-click **RuleTestApp**, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="d2b08-306">按一下**是**確認刪除。</span><span class="sxs-lookup"><span data-stu-id="d2b08-306">Click **Yes** to confirm deletion.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-307">當您刪除應用程式時，也會從規則引擎資料庫刪除應用程式中的所有原則及相依詞彙。</span><span class="sxs-lookup"><span data-stu-id="d2b08-307">When you delete an application, all the policies in the application and dependent vocabularies are deleted from the rule engine database as well.</span></span>  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-and-povocabulary-vocabulary-are-deleted"></a><span data-ttu-id="d2b08-308">若要確認 ProcessPurchaseOrder 原則和 POVocabulary 詞彙已刪除</span><span class="sxs-lookup"><span data-stu-id="d2b08-308">To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are deleted</span></span>  
  
1.  <span data-ttu-id="d2b08-309">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-309">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="d2b08-310">如果已開啟 [商務規則編輯器]，請按下 F5 重新整理。</span><span class="sxs-lookup"><span data-stu-id="d2b08-310">If you have Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-311">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d2b08-311">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d2b08-312">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-312">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d2b08-313">在 [原則總管] 視窗中，依序展開**原則**，並確定 ProcessPurchaseOrder 原則不存在。</span><span class="sxs-lookup"><span data-stu-id="d2b08-313">In the Policy Explorer window, expand **Policies**, and make sure that the ProcessPurchaseOrder policy does not exist.</span></span>  
  
3.  <span data-ttu-id="d2b08-314">在 [事實總管] 視窗中，依序展開**詞彙**，並確定 POVocabulary 不存在。</span><span class="sxs-lookup"><span data-stu-id="d2b08-314">In the Facts Explorer window, expand **Vocabularies**, and make sure that POVocabulary does not exist.</span></span>  
  
#### <a name="to-import-the-msi-file-to-re-create-the-ruletestapp-application"></a><span data-ttu-id="d2b08-315">若要匯入 MSI 檔案以重新建立 RuleTestApp 應用程式</span><span class="sxs-lookup"><span data-stu-id="d2b08-315">To import the MSI file to re-create the RuleTestApp application</span></span>  
  
1.  <span data-ttu-id="d2b08-316">在**啟動**功能表中，開啟**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-316">On the **Start** menu, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="d2b08-317">如果已經開啟 BizTalk Server 管理主控台，請按 F5 重新整理它。</span><span class="sxs-lookup"><span data-stu-id="d2b08-317">If you have the BizTalk Server Administration console already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="d2b08-318">展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後展開**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-318">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**.</span></span>  
  
3.  <span data-ttu-id="d2b08-319">以滑鼠右鍵按一下**應用程式**，指向 **匯入**，然後按一下  **MSI 檔案**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-319">Right-click **Applications**, point to **Import**, and then click **MSI file**.</span></span>  
  
4.  <span data-ttu-id="d2b08-320">在**歡迎使用匯入精靈**頁面上，瀏覽並選取您稍早匯出的 MSI 檔案 (RuleTestApp.msi)**要匯入 MSI 檔案**設定。</span><span class="sxs-lookup"><span data-stu-id="d2b08-320">On the **Welcome to the Import Wizard** page, browse and select the MSI file (RuleTestApp.msi) you exported earlier for the **MSI file to import** setting.</span></span>  
  
5.  <span data-ttu-id="d2b08-321">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-321">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="d2b08-322">在**應用程式設定**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-322">On the **Application Settings** page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="d2b08-323">在**應用程式目標環境設定**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-323">On the **Application Target Environment Settings** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="d2b08-324">在**匯入摘要**頁面上，按一下**匯入**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-324">On the **Import Summary** page, click **Import**.</span></span>  
  
9. <span data-ttu-id="d2b08-325">在**匯入成功**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-325">On the **Import Succeeded** page, click **Finish**.</span></span> <span data-ttu-id="d2b08-326">您應該會看到**RuleTestApp**下方會建立應用程式**應用程式**BizTalk Server 管理主控台中。</span><span class="sxs-lookup"><span data-stu-id="d2b08-326">You should see that the **RuleTestApp** application is created under **Applications** in the BizTalk Server Administration console.</span></span>  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-is-added-to-ruletestapp"></a><span data-ttu-id="d2b08-327">若要確認 ProcessPurchaseOrder 原則已新增至 RuleTestApp</span><span class="sxs-lookup"><span data-stu-id="d2b08-327">To verify that the ProcessPurchaseOrder policy is added to RuleTestApp</span></span>  
  
1.  <span data-ttu-id="d2b08-328">展開**RuleTestApp** BizTalk Server 管理主控台中。</span><span class="sxs-lookup"><span data-stu-id="d2b08-328">Expand **RuleTestApp** in the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="d2b08-329">選取**原則**和您應該會看到**ProcessPurchaseOrder**在右窗格的清單中。</span><span class="sxs-lookup"><span data-stu-id="d2b08-329">Select **Policies** and you should see **ProcessPurchaseOrder** in the list in the right pane.</span></span>  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-and-povocabulary-vocabulary-are-re-created"></a><span data-ttu-id="d2b08-330">若要確認 ProcessPurchaseOrder 原則和 POVocabulary 詞彙已重新建立</span><span class="sxs-lookup"><span data-stu-id="d2b08-330">To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are re-created</span></span>  
  
1.  <span data-ttu-id="d2b08-331">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-331">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="d2b08-332">如果您已經開啟它，請按 F5 重新整理。</span><span class="sxs-lookup"><span data-stu-id="d2b08-332">If you have it already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-333">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d2b08-333">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d2b08-334">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-334">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d2b08-335">在 [原則總管] 視窗中，依序展開**原則**，並確定**ProcessPurchaseOrder**存在。</span><span class="sxs-lookup"><span data-stu-id="d2b08-335">In the Policy Explorer window, expand **Policies**, and make sure that **ProcessPurchaseOrder** exists.</span></span>  
  
3.  <span data-ttu-id="d2b08-336">在 [事實總管] 視窗中，依序展開**詞彙**，並確定**POVocabulary**存在。</span><span class="sxs-lookup"><span data-stu-id="d2b08-336">In the Facts Explorer window, expand **Vocabularies**, and make sure that **POVocabulary** exists.</span></span>  
  
#### <a name="to-test-the-solution"></a><span data-ttu-id="d2b08-337">測試方案</span><span class="sxs-lookup"><span data-stu-id="d2b08-337">To test the solution</span></span>  
  
1.  <span data-ttu-id="d2b08-338">在**啟動**功能表中，開啟**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-338">On the **Start** menu, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="d2b08-339">如果已經開啟 BizTalk Server 管理主控台，請按 F5 重新整理它。</span><span class="sxs-lookup"><span data-stu-id="d2b08-339">If you have the BizTalk Server Administration console already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="d2b08-340">展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-340">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="d2b08-341">以滑鼠右鍵按一下**RuleTestApp**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-341">Right-click **RuleTestApp**, and then click **Start**.</span></span>  
  
4.  <span data-ttu-id="d2b08-342">按一下 **[啟動]**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-342">Click **Start**.</span></span>  
  
5.  <span data-ttu-id="d2b08-343">複製**SamplePO.xml**您在建立[逐步解說： 測試原則](../core/walkthrough-testing-the-policy.md)協調流程的輸入目錄。</span><span class="sxs-lookup"><span data-stu-id="d2b08-343">Copy **SamplePO.xml** that you created in [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) to the input directory for the orchestration.</span></span>  
  
6.  <span data-ttu-id="d2b08-344">您應該會在協調流程的輸出目錄中看到輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-344">You should see an output file in the output directory for the orchestration.</span></span> <span data-ttu-id="d2b08-345">開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="d2b08-345">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
7.  <span data-ttu-id="d2b08-346">重複步驟 3 和 4 **SamplePO2.xml**，並注意值**狀態**輸出文件中的欄位會與輸入文件中的相同 (**XYZ**)。</span><span class="sxs-lookup"><span data-stu-id="d2b08-346">Repeat steps 3 and 4 with **SamplePO2.xml**, and notice that the value of the **Status** field in the output document is the same as in the input document (**XYZ**).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="d2b08-347">註解</span><span class="sxs-lookup"><span data-stu-id="d2b08-347">Comments</span></span>  
  
-   <span data-ttu-id="d2b08-348">它是**非常重要**請記得，當您從應用程式移除原則時，您除了移除應用程式和原則之間的關聯; 也從規則中刪除的原則和其相關聯的詞彙引擎 」 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d2b08-348">It is **very important** to remember that when you remove a policy from an application, you do not just remove the association between the application and the policy; you also delete the policy and its associated vocabulary from the rule engine database.</span></span>  
  
-   <span data-ttu-id="d2b08-349">當您啟動應用程式時，它會依預設自動部署原則。</span><span class="sxs-lookup"><span data-stu-id="d2b08-349">When you start an application, by default, it deploys the policies automatically.</span></span> <span data-ttu-id="d2b08-350">同樣地，當您停止應用程式並選取**完全停止-終止執行個體**，相關聯的原則會自動解除部署。</span><span class="sxs-lookup"><span data-stu-id="d2b08-350">Similarly, when you stop an application and select **Full Stop - Terminate Instances**, the associated policies are undeployed automatically.</span></span> <span data-ttu-id="d2b08-351">當您選取**部分停止-擱置正在執行的執行個體**，相關聯的原則解除部署自動。</span><span class="sxs-lookup"><span data-stu-id="d2b08-351">When you select **Partial Stop - Suspend running instances**, the associated policies are not undeployed automatically.</span></span>  
  
-   <span data-ttu-id="d2b08-352">在執行任何作業之前，應該重新整理「商務規則編輯器」和「BizTalk Server 管理主控台」中的檢視，確定您看到的是最新資訊。</span><span class="sxs-lookup"><span data-stu-id="d2b08-352">You should refresh the views in Business Rule Composer and BizTalk Server Administration console to make sure you are looking at the latest information before performing any operation.</span></span>  
  
-   <span data-ttu-id="d2b08-353">如果您建立新的版本，其舊版是 BizTalk 應用程式相關聯的原則，您應手動將新版本的原則加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2b08-353">If you create a new version of the policy whose earlier version is associated with a BizTalk application, you should manually add the new version of the policy to the application.</span></span> <span data-ttu-id="d2b08-354">您不應該移除舊版本的原則，除非您真的要將它從規則引擎資料庫刪除。</span><span class="sxs-lookup"><span data-stu-id="d2b08-354">You should not remove the old version of the policy unless you really want to delete it from the rule engine database.</span></span>  
  
-   <span data-ttu-id="d2b08-355">您可以在匯入前，將兩個或更多的 BRL 檔案 (商務規則語言 XML 檔案) 合併到單一的 BRL 檔案中。</span><span class="sxs-lookup"><span data-stu-id="d2b08-355">You can merge two or more BRL (Business Rule Language XML file) files into a single BRL file before importing.</span></span> <span data-ttu-id="d2b08-356">下列程式碼顯示三個 BRL 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-356">The following code shows three BRL files.</span></span> <span data-ttu-id="d2b08-357">第一個 BRL 檔案包含**POVocabulary**詞彙。</span><span class="sxs-lookup"><span data-stu-id="d2b08-357">The first BRL file contains the **POVocabulary** vocabulary.</span></span> <span data-ttu-id="d2b08-358">第二個 BRL 檔案包含**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="d2b08-358">The second BRL file contains the **ProcessPurchaseOrder** policy.</span></span> <span data-ttu-id="d2b08-359">第三個 BRL 檔案同時包含**POVocabulary**詞彙和**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="d2b08-359">The third BRL file contains both the **POVocabulary** vocabulary and the **ProcessPurchaseOrder** policy.</span></span> <span data-ttu-id="d2b08-360">第三個 BRE 檔案是藉由執行下列步驟所建立：</span><span class="sxs-lookup"><span data-stu-id="d2b08-360">The third BRE file is created by performing the following steps:</span></span>  
  
    1.  <span data-ttu-id="d2b08-361">建立新的檔案使用的任何檔案編輯器，並將它儲存為 XML 檔案 (例如： POPolicyVocabulary.xml)。</span><span class="sxs-lookup"><span data-stu-id="d2b08-361">Create a new file using any file editor and save it as an XML file (for example: POPolicyVocabulary.xml).</span></span>  
  
    2.  <span data-ttu-id="d2b08-362">從包含詞彙的第一個 BRL 檔案複製整個 XML 內容。</span><span class="sxs-lookup"><span data-stu-id="d2b08-362">Copy the entire XML content from the first BRL file containing the vocabulary.</span></span>  
  
    3.  <span data-ttu-id="d2b08-363">複製規則集區塊 (以開始\<ruleset\>標記，且結尾為\</ruleset\>標記) 從第二個 BRL 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-363">Copy the ruleset block (starts with the \<ruleset\> tag and ends with the \</ruleset\> tag) from the second BRL file.</span></span>  
  
    4.  <span data-ttu-id="d2b08-364">儲存新檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b08-364">Save the new file.</span></span> <span data-ttu-id="d2b08-365">您可以匯入這個單一 XML 檔案，以建立**POVocabulary**詞彙和**ProcessPurchaseOrder**原則。</span><span class="sxs-lookup"><span data-stu-id="d2b08-365">You can import this single XML file to create the **POVocabulary** vocabulary and the **ProcessPurchaseOrder** policy.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2b08-366">在合併的 BRL 檔案中，詞彙和規則集節點的列出順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="d2b08-366">It does not matter in which order the vocabulary and ruleset nodes are listed in the merged BRL file.</span></span> <span data-ttu-id="d2b08-367">您可以讓規則集節點列在詞彙節點前頭。</span><span class="sxs-lookup"><span data-stu-id="d2b08-367">You can have the ruleset node ahead of the vocabulary node.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <vocabulary id="e588676a-ba01-4f37-b59d-91f7e1eb1f1a" name="POVocabulary" uri="" description="">  
           ……   
      </vocabulary>  
    </brl>  
  
    <?xml version="1.0" encoding="utf-8"?>  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <ruleset name="ProcessPurchaseOrder">  
         ……  
      </ruleset>  
    </brl>  
  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <vocabulary id="e588676a-ba01-4f37-b59d-91f7e1eb1f1a" name="POVocabulary" uri="" description="">  
           ……   
      </vocabulary>  
      <ruleset name="ProcessPurchaseOrder">  
         ……  
      </ruleset>  
    </brl>  
    ```