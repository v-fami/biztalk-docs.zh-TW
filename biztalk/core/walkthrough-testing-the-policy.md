---
title: 逐步解說： 測試原則 |Microsoft 文件
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53ed915d-0f3a-48ea-bfd5-a1f89b9b689c
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36d7ecf6e469ae6c3edd9b3d7cadc0068ba0d021
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-testing-the-policy"></a><span data-ttu-id="23371-102">逐步解說： 測試原則</span><span class="sxs-lookup"><span data-stu-id="23371-102">Walkthrough: Testing the Policy</span></span>
<span data-ttu-id="23371-103">本逐步解說提供逐步程序以測試您中建立的原則[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說。</span><span class="sxs-lookup"><span data-stu-id="23371-103">This walkthrough provides step-by-step procedures for testing the policy you created in the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="23371-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="23371-104">Prerequisites</span></span>  
 <span data-ttu-id="23371-105">您必須先完成[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說之前執行此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="23371-105">You must complete the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough before you perform this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="23371-106">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="23371-106">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="23371-107">此逐步解說包含兩個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="23371-107">This walkthrough contains two procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="23371-108">程序標題</span><span class="sxs-lookup"><span data-stu-id="23371-108">Procedure title</span></span>|<span data-ttu-id="23371-109">程序說明</span><span class="sxs-lookup"><span data-stu-id="23371-109">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="23371-110">若要建立測試檔案</span><span class="sxs-lookup"><span data-stu-id="23371-110">To create the test files</span></span>|<span data-ttu-id="23371-111">提供逐步指示，如建立兩個範例 XML 檔案，其中一個值是 [數量] 欄位為 400 (\<= 500)，另一個為 700 (> 500) 的 [數量] 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="23371-111">Provides step-by-step instructions for creating two sample XML files, one with the value of the Quantity field as 400 (\<= 500) and the other one with the value of the Quantity field as 700 (> 500).</span></span>|  
|<span data-ttu-id="23371-112">若要測試 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="23371-112">To test the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="23371-113">提供逐步指示，說明如何使用「商務規則編輯器」測試 ProcessPurchaseOrder 原則。</span><span class="sxs-lookup"><span data-stu-id="23371-113">Provides step-by-step instructions for testing the policy using Business Rule Composer.</span></span>|  
  
### <a name="to-create-the-test-files"></a><span data-ttu-id="23371-114">若要建立測試檔案</span><span class="sxs-lookup"><span data-stu-id="23371-114">To create the test files</span></span>  
  
1.  <span data-ttu-id="23371-115">在 **啟動**  功能表上，開啟 **記事本**。</span><span class="sxs-lookup"><span data-stu-id="23371-115">On the **Start** menu, open **Notepad**.</span></span>  
  
2.  <span data-ttu-id="23371-116">將下列 XML 文字複製到 [記事本] 中：</span><span class="sxs-lookup"><span data-stu-id="23371-116">Copy the following XML to Notepad:</span></span>  
  
    ```  
    <ns0:PurchaseOrder xmlns:ns0="http://EAISolution.PurchaseOrder">  
      <Header>  
        <ReqID>ReqID_0</ReqID>  
        <Date>Date_0</Date>  
      </Header>  
      <Item>  
        <Description>Description_0</Description>  
        <Quantity>400</Quantity>  
        <UnitPrice>20</UnitPrice>  
      </Item>  
      <Status>XYZ</Status>  
    </ns0:PurchaseOrder>    
    ```  
  
3.  <span data-ttu-id="23371-117">在 **檔案** ] 功能表上，按一下 [ **另存 TextFile1.txt 為**。</span><span class="sxs-lookup"><span data-stu-id="23371-117">On the **File** menu, click **Save TextFile1.txt As**.</span></span>  
  
4.  <span data-ttu-id="23371-118">變更的值 **另存新檔類型** 從 **文字文件 (\*.txt)** 到 **的所有檔案**。</span><span class="sxs-lookup"><span data-stu-id="23371-118">Change the value for **Save As type** from **Text Documents(\*.txt)** to **All Files**.</span></span>  
  
5.  <span data-ttu-id="23371-119">切換至目錄 **C:\BRE-Walkthroughs**。</span><span class="sxs-lookup"><span data-stu-id="23371-119">Change the directory to **C:\BRE-Walkthroughs**.</span></span>  
  
6.  <span data-ttu-id="23371-120">型別 **SamplePO.xml** 的 **檔案名稱**, ，然後按一下  **儲存**。</span><span class="sxs-lookup"><span data-stu-id="23371-120">Type **SamplePO.xml** for **File name**, and then click **Save**.</span></span>  
  
7.  <span data-ttu-id="23371-121">在 [檔案]  功能表上，按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="23371-121">On the **File** menu, click **New**.</span></span>  
  
8.  <span data-ttu-id="23371-122">將下列 XML 文字複製到 [記事本] 中：</span><span class="sxs-lookup"><span data-stu-id="23371-122">Copy the following XML to Notepad:</span></span>  
  
    ```  
    <ns0:PurchaseOrder xmlns:ns0="http://EAISolution.PurchaseOrder">  
      <Header>  
        <ReqID>ReqID_0</ReqID>  
        <Date>Date_0</Date>  
      </Header>  
      <Item>  
        <Description>Description_0</Description>  
        <Quantity>700</Quantity>  
        <UnitPrice>20</UnitPrice>  
      </Item>  
      <Status>XYZ</Status>  
    </ns0:PurchaseOrder>   
    ```  
  
9. <span data-ttu-id="23371-123">在 **檔案** ] 功能表上，按一下 [ **另存 TextFile1.txt 為**。</span><span class="sxs-lookup"><span data-stu-id="23371-123">On the **File** menu, click **Save TextFile1.txt As**.</span></span>  
  
10. <span data-ttu-id="23371-124">變更的值 **另存新檔類型** 從 **文字文件 (\*.txt)** 到 **的所有檔案**。</span><span class="sxs-lookup"><span data-stu-id="23371-124">Change the value for **Save As type** from **Text Documents(\*.txt)** to **All Files**.</span></span>  
  
11. <span data-ttu-id="23371-125">切換至目錄 **C:\BRE-Walkthroughs**。</span><span class="sxs-lookup"><span data-stu-id="23371-125">Change the directory to **C:\BRE-Walkthroughs**.</span></span>  
  
12. <span data-ttu-id="23371-126">型別 **SamplePO2.xml** 的 **檔案名稱**, ，然後按一下  **儲存**。</span><span class="sxs-lookup"><span data-stu-id="23371-126">Type **SamplePO2.xml** for **File name**, and then click **Save**.</span></span>  
  
13. <span data-ttu-id="23371-127">關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="23371-127">Close Notepad.</span></span>  
  
### <a name="to-test-the-processpurchaseorder-policy"></a><span data-ttu-id="23371-128">若要測試 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="23371-128">To test the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="23371-129">在 **啟動**  功能表上，開啟 **商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="23371-129">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="23371-130">如果已開啟 [商務規則編輯器]，請按下 F5 重新整理。</span><span class="sxs-lookup"><span data-stu-id="23371-130">If you have Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23371-131">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="23371-131">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="23371-132">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取 **系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="23371-132">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="23371-133">在 原則總管 視窗中，依序展開 **原則**, ，依序展開 **ProcessPurchaseOrder**, ，以滑鼠右鍵按一下 **1.0 版**, ，然後按一下  **測試原則**。</span><span class="sxs-lookup"><span data-stu-id="23371-133">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0**, and then click **Test Policy**.</span></span>  
  
3.  <span data-ttu-id="23371-134">在 **XMLDocuments** 節點中，選取 **RuleTest.PO**, ，然後按一下  **新增執行個體**。</span><span class="sxs-lookup"><span data-stu-id="23371-134">In the **XMLDocuments** node, select **RuleTest.PO**, and then click **Add Instance**.</span></span>  
  
     <span data-ttu-id="23371-135">![商務規則編輯器 」&#45;TestPolicySelectFacts](../core/media/7115f0d4-0c12-4292-81a5-eb78d62c5543.gif "7115f0d4-0c12-4292-81a5-eb78d62c5543")</span><span class="sxs-lookup"><span data-stu-id="23371-135">![Business Rule Composer&#45;TestPolicySelectFacts](../core/media/7115f0d4-0c12-4292-81a5-eb78d62c5543.gif "7115f0d4-0c12-4292-81a5-eb78d62c5543")</span></span>  
  
4.  <span data-ttu-id="23371-136">選取 **SamplePO.xml** 稍早建立的檔案，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="23371-136">Select the **SamplePO.xml** file that you created earlier, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="23371-137">按一下  **測試**。</span><span class="sxs-lookup"><span data-stu-id="23371-137">Click **Test**.</span></span>  
  
6.  <span data-ttu-id="23371-138">在 [輸出] 視窗中檢視輸出。</span><span class="sxs-lookup"><span data-stu-id="23371-138">Review the output in the Output window.</span></span> <span data-ttu-id="23371-139">如需輸出的說明，請參閱「第一個測試 (samplepo.xml) 的輸出分析」一節。</span><span class="sxs-lookup"><span data-stu-id="23371-139">See the "Analysis of the Output from the First Test (samplepo.xml)" section for an explanation of the output you see.</span></span>  
  
7.  <span data-ttu-id="23371-140">開啟 **SamplePO.xml** 在記事本，並請注意，值 **狀態** 欄位設為 **核准**。</span><span class="sxs-lookup"><span data-stu-id="23371-140">Open **SamplePO.xml** in Notepad and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
8.  <span data-ttu-id="23371-141">以滑鼠右鍵按一下 **1.0 版**, ，然後按一下  **測試原則**。</span><span class="sxs-lookup"><span data-stu-id="23371-141">Right-click **Version 1.0**, and then click **Test Policy**.</span></span>  
  
9. <span data-ttu-id="23371-142">選取 **SamplePO.xml**, ，按一下  **移除執行個體**, ，然後按一下  **新增執行個體**。</span><span class="sxs-lookup"><span data-stu-id="23371-142">Select **SamplePO.xml**, click **Remove instance**, and then click **Add Instance**.</span></span>  
  
10. <span data-ttu-id="23371-143">選取 **SamplePO2.xml** 稍早建立的檔案，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="23371-143">Select the **SamplePO2.xml** file that you created earlier, and then click **Open**.</span></span>  
  
11. <span data-ttu-id="23371-144">按一下  **測試**。</span><span class="sxs-lookup"><span data-stu-id="23371-144">Click **Test**.</span></span> <span data-ttu-id="23371-145">如需輸出的說明，請參閱「第二個測試 (samplepo2.xml) 的輸出分析」一節。</span><span class="sxs-lookup"><span data-stu-id="23371-145">See the "Analysis of the Output from the Second Test (samplepo2.xml)" section for an explanation of the output you see.</span></span>  
  
12. <span data-ttu-id="23371-146">開啟 **SamplePO2.xml** [記事本] 中，並注意值 **狀態** 欄位仍 **XYZ**。</span><span class="sxs-lookup"><span data-stu-id="23371-146">Open the **SamplePO2.xml** file in Notepad and notice that the value of the **Status** field is still **XYZ**.</span></span>  
  
## <a name="analysis-of-the-output-from-the-first-test-samplepoxml"></a><span data-ttu-id="23371-147">第一個測試 (samplepo.xml) 的輸出分析</span><span class="sxs-lookup"><span data-stu-id="23371-147">Analysis of the Output from the First Test (samplepo.xml)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23371-148">輸出文字是粗體，說明在輸出文字之後。</span><span class="sxs-lookup"><span data-stu-id="23371-148">The output text is bold and the explanation follows the output text.</span></span>  
  
 <span data-ttu-id="23371-149">**規則集的規則引擎追蹤︰ ProcessPurchaseOrder 8/31/2006年 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-149">**RULE ENGINE TRACE for RULESET: ProcessPurchaseOrder 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="23371-150">執行原則的規則引擎追蹤 **ProcessPurchaseOrder** 開始於 8/31/2006年 1:33:10 PM。</span><span class="sxs-lookup"><span data-stu-id="23371-150">The rule engine trace for the execution of policy **ProcessPurchaseOrder** started at 8/31/2006 1:33:10 PM.</span></span>  
  
 <span data-ttu-id="23371-151">**事實活動 8/31/2006年 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-151">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="23371-152">**規則引擎執行個體識別碼︰ bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="23371-152">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="23371-153">**規則集名稱︰ ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-153">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-154">**作業︰ 判斷提示**</span><span class="sxs-lookup"><span data-stu-id="23371-154">**Operation: Assert**</span></span>  
  
 <span data-ttu-id="23371-155">**物件類型︰ TypedXmlDocument:PurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-155">**Object Type: TypedXmlDocument:PurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-156">**物件執行個體識別碼︰ 14626574**</span><span class="sxs-lookup"><span data-stu-id="23371-156">**Object Instance Identifier: 14626574**</span></span>  
  
 <span data-ttu-id="23371-157">當您按一下 **測試**, ，會發生下列情況︰</span><span class="sxs-lookup"><span data-stu-id="23371-157">When you click **Test**, the following things happen:</span></span>  
  
1.  <span data-ttu-id="23371-158">商務規則編輯器建立 **RuleEngine.Policy** 物件，進而建立新的規則引擎執行個體，或取得從規則引擎快取規則引擎執行個體。</span><span class="sxs-lookup"><span data-stu-id="23371-158">The Business Rule Composer creates a **RuleEngine.Policy** object, which in turn creates a new rule engine instance or acquires a rule engine instance from the rule engine cache.</span></span>  
  
2.  <span data-ttu-id="23371-159">商務規則編輯器建立 **TypedXmlDocument** SamplePO.xml 檔案為基礎的物件。</span><span class="sxs-lookup"><span data-stu-id="23371-159">The Business Rule Composer creates a **TypedXmlDocument** object based on the SamplePO.xml file.</span></span>  
  
3.  <span data-ttu-id="23371-160">商務規則編輯器 」 會叫用 **Policy.Execute** 方法 **TypedXmlDocument** 物件做為參數。</span><span class="sxs-lookup"><span data-stu-id="23371-160">The Business Rule Composer invokes the **Policy.Execute** method with the **TypedXmlDocument** object as a parameter.</span></span>  
  
4.  <span data-ttu-id="23371-161">**Policy.Execute** 方法會判斷提示 （新增） **TypedXmlDocument** 物件當做事實到規則引擎工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="23371-161">The **Policy.Execute** method asserts (adds) the **TypedXmlDocument** object as a fact into the working memory of the rule engine.</span></span>  
  
5.  <span data-ttu-id="23371-162">規則引擎會使用 **TypedXmlDocument** 物件當做事實並執行 **ProcessPurchaseOrder** 原則。</span><span class="sxs-lookup"><span data-stu-id="23371-162">The rule engine uses the **TypedXmlDocument** object as a fact and executes the **ProcessPurchaseOrder** policy.</span></span>  
  
 <span data-ttu-id="23371-163">**事實活動 8/31/2006年 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-163">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="23371-164">**規則引擎執行個體識別碼︰ bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="23371-164">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="23371-165">**規則集名稱︰ ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-165">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-166">**作業︰ 判斷提示**</span><span class="sxs-lookup"><span data-stu-id="23371-166">**Operation: Assert**</span></span>  
  
 <span data-ttu-id="23371-167">**物件類型︰ TypedXmlDocument:PurchaseOrder: / PurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-167">**Object Type: TypedXmlDocument:PurchaseOrder:/PurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-168">**物件執行個體識別碼︰ 64530307**</span><span class="sxs-lookup"><span data-stu-id="23371-168">**Object Instance Identifier: 64530307**</span></span>  
  
 <span data-ttu-id="23371-169">**事實活動 8/31/2006年 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-169">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="23371-170">**規則引擎執行個體識別碼︰ bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="23371-170">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="23371-171">**規則集名稱︰ ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-171">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-172">**作業︰ 判斷提示**</span><span class="sxs-lookup"><span data-stu-id="23371-172">**Operation: Assert**</span></span>  
  
 <span data-ttu-id="23371-173">**物件類型︰ TypedXmlDocument:PurchaseOrder: / PurchaseOrder/項目**</span><span class="sxs-lookup"><span data-stu-id="23371-173">**Object Type: TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item**</span></span>  
  
 <span data-ttu-id="23371-174">**物件執行個體識別碼︰ 43901854**</span><span class="sxs-lookup"><span data-stu-id="23371-174">**Object Instance Identifier: 43901854**</span></span>  
  
1.  <span data-ttu-id="23371-175">規則引擎會決定哪一個子 **TypedXmlDocument** 物件，以建立根據規則中所定義的 XPath 選取器。</span><span class="sxs-lookup"><span data-stu-id="23371-175">The rule engine determines which child **TypedXmlDocument** objects to create based on the XPath selectors defined in the rules.</span></span> <span data-ttu-id="23371-176">當您建置商務規則編輯器 」 中的規則時，XPath 選取器的預設值為中選取之節點上方的節點 **XML 結構描述** 在事實總管 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="23371-176">When you build rules in the Business Rule Composer, the XPath selector value defaults to the node above the node selected in the **XML Schemas** tab in Facts Explorer.</span></span> <span data-ttu-id="23371-177">XPath 欄位的值預設為選取的節點本身 (相對於其父節點而言)。</span><span class="sxs-lookup"><span data-stu-id="23371-177">The XPath field value defaults to the selected node itself, relative to its parent node.</span></span> <span data-ttu-id="23371-178">不過，如果選取的節點有子系，則只會建立 XPath 選取器繫結指向選取的節點，而不會建立 XPath 欄位繫結。</span><span class="sxs-lookup"><span data-stu-id="23371-178">However, if the node you selected has children, only an XPath selector binding is created to point to the node that you selected, and no XPath field binding is created.</span></span>  
  
2.  <span data-ttu-id="23371-179">下表顯示 XPath 選取器和 XPath 欄位繫結中使用的欄位值 **ProcessPurchaseOrder** 原則。</span><span class="sxs-lookup"><span data-stu-id="23371-179">The following table shows the XPath Selector and XPath Field binding values for the fields used in the **ProcessPurchaseOrder** policy.</span></span> <span data-ttu-id="23371-180">(此原則只有一個規則：ApprovalRule)。</span><span class="sxs-lookup"><span data-stu-id="23371-180">(The policy has only one rule, ApprovalRule.)</span></span>  
  
|<span data-ttu-id="23371-181">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="23371-181">Field name</span></span>|<span data-ttu-id="23371-182">XPath 選取器</span><span class="sxs-lookup"><span data-stu-id="23371-182">XPath Selector</span></span>|<span data-ttu-id="23371-183">XPath 欄位</span><span class="sxs-lookup"><span data-stu-id="23371-183">XPath Field</span></span>|<span data-ttu-id="23371-184">XPath 選取器 (簡化形式)</span><span class="sxs-lookup"><span data-stu-id="23371-184">XPath Selector (simplified form)</span></span>|<span data-ttu-id="23371-185">XPath 欄位</span><span class="sxs-lookup"><span data-stu-id="23371-185">XPath Field</span></span><br /><br /> <span data-ttu-id="23371-186">(簡化形式)</span><span class="sxs-lookup"><span data-stu-id="23371-186">(simplified form)</span></span>|  
|----------------|--------------------|-----------------|----------------------------------------|-----------------------------------------|  
|<span data-ttu-id="23371-187">Quantity</span><span class="sxs-lookup"><span data-stu-id="23371-187">Quantity</span></span>|<span data-ttu-id="23371-188">/ * [local-name = 'PurchaseOrder' and namespace-uri （) ='http://EAISolution.PurchaseOrder'] /\*[local-name = 'Item' and namespace-uri （) =']</span><span class="sxs-lookup"><span data-stu-id="23371-188">/*[local-name()='PurchaseOrder' and namespace-uri()='http://EAISolution.PurchaseOrder']/\*[local-name()='Item' and namespace-uri()='']</span></span>|<span data-ttu-id="23371-189">\*[local-name()='Quantity' and namespace-uri()='']</span><span class="sxs-lookup"><span data-stu-id="23371-189">\*[local-name()='Quantity' and namespace-uri()='']</span></span>|<span data-ttu-id="23371-190">/PurchaseOrder/Item</span><span class="sxs-lookup"><span data-stu-id="23371-190">/PurchaseOrder/Item</span></span>|<span data-ttu-id="23371-191">Quantity</span><span class="sxs-lookup"><span data-stu-id="23371-191">Quantity</span></span>|  
|<span data-ttu-id="23371-192">狀態</span><span class="sxs-lookup"><span data-stu-id="23371-192">Status</span></span>|<span data-ttu-id="23371-193">/ \* [local-name = 'PurchaseOrder' and namespace-uri （) ='http://EAISolution.PurchaseOrder']</span><span class="sxs-lookup"><span data-stu-id="23371-193">/\*[local-name()='PurchaseOrder' and namespace-uri()='http://EAISolution.PurchaseOrder']</span></span>|<span data-ttu-id="23371-194">\*[local-name()='Status' and namespace-uri()='']</span><span class="sxs-lookup"><span data-stu-id="23371-194">\*[local-name()='Status' and namespace-uri()='']</span></span>|<span data-ttu-id="23371-195">/PurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="23371-195">/PurchaseOrder</span></span>|<span data-ttu-id="23371-196">狀態</span><span class="sxs-lookup"><span data-stu-id="23371-196">Status</span></span>|
<!---Loc Comment: Please, verify strucutre in line 183 and 184--->
  
#### <a name="to-view-the-xpath-selector-and-xpath-field-bindings-for-the-quantity-and-status-fields"></a><span data-ttu-id="23371-197">若要檢視 Quantity 和 Status 欄位的 Xpath 選取器和 Xpath 欄位繫結</span><span class="sxs-lookup"><span data-stu-id="23371-197">To view the Xpath Selector and Xpath Field bindings for the Quantity and Status fields</span></span>  
  
1.  <span data-ttu-id="23371-198">在 [原則總管] 視窗中，依序展開 **原則**, ，依序展開 **ProcessPurchaseOrder**, ，然後展開 **1.0 版**。</span><span class="sxs-lookup"><span data-stu-id="23371-198">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, and then expand **Version 1.0**.</span></span>  
  
2.  <span data-ttu-id="23371-199">按一下  **ApprovalRule**。</span><span class="sxs-lookup"><span data-stu-id="23371-199">Click **ApprovalRule**.</span></span>  
  
3.  <span data-ttu-id="23371-200">在右邊的 IF 窗格，按一下  **PO: / PurchaseOrder/Item/Quantity**。</span><span class="sxs-lookup"><span data-stu-id="23371-200">In the IF pane on the right, click **PO:/PurchaseOrder/Item/Quantity**.</span></span>  
  
4.  <span data-ttu-id="23371-201">確認您看到上述資料表中所顯示的值 **XPath 選取器** 和 **XPath 欄位** [屬性] 視窗中的繫結。</span><span class="sxs-lookup"><span data-stu-id="23371-201">Verify that you see the value shown in the preceding table for the **XPath Selector** and **XPath Field** bindings in the Properties window.</span></span>  
  
5.  <span data-ttu-id="23371-202">重複步驟 3 和 4 **PO: / PurchaseOrder/Status** 欄位。</span><span class="sxs-lookup"><span data-stu-id="23371-202">Repeat steps 3 and 4 for the **PO:/PurchaseOrder/Status** field.</span></span>  
  
 <span data-ttu-id="23371-203">規則引擎會建立一個子系 **TypedXmlDocument** 與原始物件 **TypedXmlDocument** 您提交的每個 XPath 選取器。</span><span class="sxs-lookup"><span data-stu-id="23371-203">The rule engine creates a child **TypedXmlDocument** object from the original **TypedXmlDocument** you submitted for each XPath selector.</span></span> <span data-ttu-id="23371-204">因為有兩個不同 XPath 選取器在原則中使用 (**/PurchaseOrder/項目** 的 **數量** 欄位和 **/PurchaseOrder** 的 **狀態** 欄位)，規則引擎會建立兩個子 **TypedXmlDocument** 物件，並會加以判斷提示至規則引擎工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="23371-204">Because there are two distinct XPath selectors used in the policy (**/PurchaseOrder/Item** for the **Quantity** field and **/PurchaseOrder** for the **Status** field), the rule engine creates two child **TypedXmlDocument** objects and asserts them into the working memory of the rule engine.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23371-205">若要查看追蹤一次輸出中，按一下 **1.0 版** 原則總管 視窗中。</span><span class="sxs-lookup"><span data-stu-id="23371-205">To see the trace output again, click **Version 1.0** in the Policy Explorer window.</span></span>  
  
 <span data-ttu-id="23371-206">**條件評估測試 （符合） 8/31/2006年 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-206">**CONDITION EVALUATION TEST (MATCH) 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="23371-207">**規則引擎執行個體識別碼︰ bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="23371-207">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="23371-208">**規則集名稱︰ ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-208">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-209">**測試運算式︰ TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity < = 500**</span><span class="sxs-lookup"><span data-stu-id="23371-209">**Test Expression: TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity <= 500**</span></span>  
  
 <span data-ttu-id="23371-210">**左運算元值︰ 400**</span><span class="sxs-lookup"><span data-stu-id="23371-210">**Left Operand Value: 400**</span></span>  
  
 <span data-ttu-id="23371-211">**右運算元值︰ 500**</span><span class="sxs-lookup"><span data-stu-id="23371-211">**Right Operand Value: 500**</span></span>  
  
 <span data-ttu-id="23371-212">**測試結果︰ True**</span><span class="sxs-lookup"><span data-stu-id="23371-212">**Test Result: True**</span></span>  
  
 <span data-ttu-id="23371-213">**議程更新 8/31/2006年 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-213">**AGENDA UPDATE 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="23371-214">**規則引擎執行個體識別碼︰ bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="23371-214">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="23371-215">**規則集名稱︰ ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-215">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-216">**作業︰ 新增**</span><span class="sxs-lookup"><span data-stu-id="23371-216">**Operation: Add**</span></span>  
  
 <span data-ttu-id="23371-217">**規則名稱︰ ApprovalRule**</span><span class="sxs-lookup"><span data-stu-id="23371-217">**Rule Name: ApprovalRule**</span></span>  
  
 <span data-ttu-id="23371-218">**衝突解決準則︰ 0**</span><span class="sxs-lookup"><span data-stu-id="23371-218">**Conflict Resolution Criteria: 0**</span></span>  
  
 <span data-ttu-id="23371-219">此規則引擎會使用「條件評估」、「衝突解決」和「動作執行」三階段演算法來執行原則。</span><span class="sxs-lookup"><span data-stu-id="23371-219">The rule engine uses the three-stage Condition Evaluation-Conflict Resolution-Action Execution algorithm to execute policies.</span></span> <span data-ttu-id="23371-220">在「條件評估」階段中，此規則引擎會評估所有原則之規則中的條件，並將條件評估為 `true` 的規則新增至議程中。</span><span class="sxs-lookup"><span data-stu-id="23371-220">In the Condition Evaluation stage, the rule engine evaluates the conditions in all the rules in the policy and adds the rules whose conditions evaluate to `true` to the agenda.</span></span> <span data-ttu-id="23371-221">在此簡單範例中， **ProcessPurchaseOrder** 原則不會有一個規則， **ApprovalRule**。</span><span class="sxs-lookup"><span data-stu-id="23371-221">In this simple example, the **ProcessPurchaseOrder** policy has only one rule, **ApprovalRule**.</span></span> <span data-ttu-id="23371-222">因此，規則引擎會評估條件， **數量 < = 500**, 中 **ApprovalRule** 使用值 **數量** 欄位中提交 XML 文件，也就是 **400**。</span><span class="sxs-lookup"><span data-stu-id="23371-222">Therefore, the rule engine evaluates the condition, **Quantity <= 500**, in the **ApprovalRule** using the value of the **Quantity** field in the submitted XML document, which is **400**.</span></span> <span data-ttu-id="23371-223">以上輸出顯示左運算元、右運算元和測試結果的值。</span><span class="sxs-lookup"><span data-stu-id="23371-223">The output above shows you the values of the left operand, right operand, and test result.</span></span>  
  
 <span data-ttu-id="23371-224">在第二個階段「衝突解決準則」中，條件評估為 `true` 的規則會依照其優先順序新增至議程中。</span><span class="sxs-lookup"><span data-stu-id="23371-224">In the second stage, the Conflict Resolution Criteria stage, the rules whose conditions evaluate to `true` are added to the agenda in order based on their priority.</span></span> <span data-ttu-id="23371-225">在此案例中，規則引擎會加入 **ApprovalRule** 議程因為條件 **ApprovalRule** 評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="23371-225">In this scenario, the rule engine adds the **ApprovalRule** to the agenda because the condition for the **ApprovalRule** evaluated to `true`.</span></span> <span data-ttu-id="23371-226">在上述輸出中顯示的衝突解決準則是規則的優先順序 (**ApprovalRule**)。</span><span class="sxs-lookup"><span data-stu-id="23371-226">The Conflict Resolution Criteria shown in the output above is only the priority on the rule (**ApprovalRule**).</span></span> <span data-ttu-id="23371-227">如果您按一下 **ApprovalRule** 節點 [原則總管] 視窗中的，您可以看到值 **優先順序** 上做為 [屬性] 視窗中的規則屬性 **0**, ，這是預設值的規則。</span><span class="sxs-lookup"><span data-stu-id="23371-227">If you click the **ApprovalRule** node in the Policy Explorer window, you can see the value of the **Priority** property on the rule in the Properties window as **0**, which is the default value of a rule.</span></span> <span data-ttu-id="23371-228">如果原則有多個規則，而且要確定某個規則的動作會在另一個規則的動作之後執行，則必須適當設定優先順序。</span><span class="sxs-lookup"><span data-stu-id="23371-228">If you have multiple rules in a policy, and you want to make sure that actions in one rule are executed after actions in another rule, you should set the priority appropriately.</span></span> <span data-ttu-id="23371-229">數字愈大，優先順序愈高。</span><span class="sxs-lookup"><span data-stu-id="23371-229">The larger the number, the higher the priority.</span></span>  
  
 <span data-ttu-id="23371-230">**規則被引發 8/31/2006年 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-230">**RULE FIRED 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="23371-231">**規則引擎執行個體識別碼︰ bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="23371-231">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="23371-232">**規則集名稱︰ ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-232">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-233">**規則名稱︰ ApprovalRule**</span><span class="sxs-lookup"><span data-stu-id="23371-233">**Rule Name: ApprovalRule**</span></span>  
  
 <span data-ttu-id="23371-234">**衝突解決準則︰ 0**</span><span class="sxs-lookup"><span data-stu-id="23371-234">**Conflict Resolution Criteria: 0**</span></span>  
  
 <span data-ttu-id="23371-235">在最後一個階段「動作執行」中，規則引擎會開始執行規則中的動作。</span><span class="sxs-lookup"><span data-stu-id="23371-235">In the last stage, the Action Execution stage, the rule engine starts executing the actions in the rule.</span></span> <span data-ttu-id="23371-236">中的一個動作 **ApprovalRule**, ，可設定的值 **狀態** 提交 XML 文件中的欄位 **核准**。</span><span class="sxs-lookup"><span data-stu-id="23371-236">There is one action in the **ApprovalRule**, which sets the value of the **Status** field in the submitted XML document to **Approved**.</span></span>  
  
 <span data-ttu-id="23371-237">**事實活動 8/31/2006年 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-237">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="23371-238">**規則引擎執行個體識別碼︰ bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="23371-238">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="23371-239">**規則集名稱︰ ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-239">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-240">**作業︰ 撤銷**</span><span class="sxs-lookup"><span data-stu-id="23371-240">**Operation: Retract**</span></span>  
  
 <span data-ttu-id="23371-241">**物件類型︰ TypedXmlDocument:PurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-241">**Object Type: TypedXmlDocument:PurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-242">**物件執行個體識別碼︰ 14626574**</span><span class="sxs-lookup"><span data-stu-id="23371-242">**Object Instance Identifier: 14626574**</span></span>  
  
 <span data-ttu-id="23371-243">**事實活動 8/31/2006年 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-243">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="23371-244">**規則引擎執行個體識別碼︰ bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="23371-244">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="23371-245">**規則集名稱︰ ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-245">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-246">**作業︰ 撤銷**</span><span class="sxs-lookup"><span data-stu-id="23371-246">**Operation: Retract**</span></span>  
  
 <span data-ttu-id="23371-247">**物件類型︰ TypedXmlDocument:PurchaseOrder: / PurchaseOrder/項目**</span><span class="sxs-lookup"><span data-stu-id="23371-247">**Object Type: TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item**</span></span>  
  
 <span data-ttu-id="23371-248">**物件執行個體識別碼︰ 43901854**</span><span class="sxs-lookup"><span data-stu-id="23371-248">**Object Instance Identifier: 43901854**</span></span>  
  
 <span data-ttu-id="23371-249">**事實活動 8/31/2006年 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-249">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="23371-250">**規則引擎執行個體識別碼︰ bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="23371-250">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="23371-251">**規則集名稱︰ ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-251">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-252">**作業︰ 撤銷**</span><span class="sxs-lookup"><span data-stu-id="23371-252">**Operation: Retract**</span></span>  
  
 <span data-ttu-id="23371-253">**物件類型︰ TypedXmlDocument:PurchaseOrder: / PurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-253">**Object Type: TypedXmlDocument:PurchaseOrder:/PurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-254">**物件執行個體識別碼︰** 64530307</span><span class="sxs-lookup"><span data-stu-id="23371-254">**Object Instance Identifier:** 64530307</span></span>  
  
 <span data-ttu-id="23371-255">送出的所有事實 (**PurchaseOrder**) 至規則引擎和規則引擎所建立的子事實根據 XPath 選取器 (**\PurchaseOrder** 和 **\PurchaseOrder\Item**) 會撤回 （移除） 從規則引擎工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="23371-255">All the facts submitted (**PurchaseOrder**) to the rule engine and the child facts created by the rule engine based on XPath selectors (**\PurchaseOrder** and **\PurchaseOrder\Item**) are retracted (removed) from the working memory of the rule engine.</span></span>  
  
## <a name="analysis-of-the-output-from-the-second-test-samplepo2xml"></a><span data-ttu-id="23371-256">第二個測試 (samplepo2.xml) 的輸出分析</span><span class="sxs-lookup"><span data-stu-id="23371-256">Analysis of the Output from the Second Test (samplepo2.xml)</span></span>  
 <span data-ttu-id="23371-257">**條件評估測試 （符合） 9/5/2006年 5:24:42 PM**</span><span class="sxs-lookup"><span data-stu-id="23371-257">**CONDITION EVALUATION TEST (MATCH) 9/5/2006 5:24:42 PM**</span></span>  
  
 <span data-ttu-id="23371-258">**規則引擎執行個體識別碼︰ b749d2fd-a883-4c2f-9974-5cf688010622**</span><span class="sxs-lookup"><span data-stu-id="23371-258">**Rule Engine Instance Identifier: b749d2fd-a883-4c2f-9974-5cf688010622**</span></span>  
  
 <span data-ttu-id="23371-259">**規則集名稱︰ ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="23371-259">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="23371-260">**測試運算式︰ TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity < = 500**</span><span class="sxs-lookup"><span data-stu-id="23371-260">**Test Expression: TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity <= 500**</span></span>  
  
 <span data-ttu-id="23371-261">**左運算元值︰ 700**</span><span class="sxs-lookup"><span data-stu-id="23371-261">**Left Operand Value: 700**</span></span>  
  
 <span data-ttu-id="23371-262">**右運算元值︰ 500**</span><span class="sxs-lookup"><span data-stu-id="23371-262">**Right Operand Value: 500**</span></span>  
  
 <span data-ttu-id="23371-263">**測試結果︰** False</span><span class="sxs-lookup"><span data-stu-id="23371-263">**Test Result:** False</span></span>  
  
 <span data-ttu-id="23371-264">規則引擎會評估條件 (**數量 < = 500**) 中 **ApprovalRule** 使用獨立 **項目** 物件。</span><span class="sxs-lookup"><span data-stu-id="23371-264">The rule engine evaluates the condition (**Quantity <= 500**) in the **ApprovalRule** using the lone **Item** object.</span></span> <span data-ttu-id="23371-265">您可以看到左的運算元值是值 **數量** XML 文件中的項目 **700**。</span><span class="sxs-lookup"><span data-stu-id="23371-265">You can see that left operand value is the value of the **Quantity** element in the XML document, **700**.</span></span> <span data-ttu-id="23371-266">測試結果就是 `false` 因為 **700 < = 500**, ，因此，此規則不會加入至規則引擎的議程。</span><span class="sxs-lookup"><span data-stu-id="23371-266">The test result is `false` because **700 <= 500**, so the rule is not added to the agenda of the rule engine.</span></span> <span data-ttu-id="23371-267">議程中沒有規則。</span><span class="sxs-lookup"><span data-stu-id="23371-267">There is no rule in the agenda.</span></span> <span data-ttu-id="23371-268">因此，有任何動作來執行，以及值 **狀態** 欄位會維持 **XYZ**。</span><span class="sxs-lookup"><span data-stu-id="23371-268">Therefore, there are no actions to execute, and the value of the **Status** field remains **XYZ**.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="23371-269">註解</span><span class="sxs-lookup"><span data-stu-id="23371-269">Comments</span></span>  
  
-   <span data-ttu-id="23371-270">建議您先測試原則，然後從 BizTalk 應用程式之類的用戶端應用程式中使用原則。</span><span class="sxs-lookup"><span data-stu-id="23371-270">We recommend that you test the policies before using them from client applications such as BizTalk applications.</span></span>  
  
-   <span data-ttu-id="23371-271">當您測試使用與資料庫事實的原則 **DataConnection** 商務規則編輯器 中的繫結 **DataConnection** 為您自動建立物件。</span><span class="sxs-lookup"><span data-stu-id="23371-271">When you test a policy that uses database facts with the **DataConnection** binding in the Business Rule Composer, a **DataConnection** object is automatically built for you.</span></span> <span data-ttu-id="23371-272">不過，當您呼叫相同的原則從協調流程使用 **呼叫規則** 圖形，無 **DataConnection** 自動物件傳遞至原則。</span><span class="sxs-lookup"><span data-stu-id="23371-272">However, when you call the same policy from an orchestration by using the **Call Rules** shape, no **DataConnection** object is passed to the policy automatically.</span></span> <span data-ttu-id="23371-273">您應該建立 **DataConnection** 協調流程中的物件並將它當做參數傳遞或建立判斷提示事實擷取器元件 **DataConnection** 物件，然後將原則設定為使用事實擷取器元件。</span><span class="sxs-lookup"><span data-stu-id="23371-273">You should create a **DataConnection** object in the orchestration and pass it as a parameter or create a fact retriever component that asserts the **DataConnection** object, and configure the policy to use the fact retriever component.</span></span>  
  
-   <span data-ttu-id="23371-274">若要測試使用.NET 事實的原則，您應該建立事實建立者元件，並指定它在 **選取事實** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="23371-274">To test a policy that uses a .NET fact, you should create a fact creator component and specify it in the **Select Facts** dialog box.</span></span> <span data-ttu-id="23371-275">如需有關如何建立事實建立者的詳細資訊，請參閱[如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)。</span><span class="sxs-lookup"><span data-stu-id="23371-275">For more information about creating fact creators, see [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md).</span></span> <span data-ttu-id="23371-276">原則會使用資料庫事實時，您可以執行相同的動作 (**TypedDataConnection** 或 **TypedDataTable** 或 **TypedDataRow**) 或 XML 事實 (**TypedXmlDocument**)。</span><span class="sxs-lookup"><span data-stu-id="23371-276">You can do the same thing when the policy uses database facts (**TypedDataConnection** or **TypedDataTable** or **TypedDataRow**) or XML facts (**TypedXmlDocument**).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="23371-277">後續步驟</span><span class="sxs-lookup"><span data-stu-id="23371-277">Next Steps</span></span>  
 <span data-ttu-id="23371-278">現在您已完成此逐步解說中，執行[逐步解說： 從協調流程原則叫用](../core/walkthrough-invoking-the-policy-from-an-orchestration.md)逐步解說中，它將提供逐步指示，來叫用**ProcessPurchaseOrder**從協調流程的原則。</span><span class="sxs-lookup"><span data-stu-id="23371-278">Now that you have completed this walkthrough, perform the [Walkthrough: Invoking the Policy from an Orchestration](../core/walkthrough-invoking-the-policy-from-an-orchestration.md) walkthrough, which gives you step-by-step instructions for invoking the **ProcessPurchaseOrder** policy from an orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23371-279">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23371-279">See Also</span></span>  
 <span data-ttu-id="23371-280">[原則測試追蹤輸出](../core/policy-test-trace-output.md) </span><span class="sxs-lookup"><span data-stu-id="23371-280">[Policy Test Trace Output](../core/policy-test-trace-output.md) </span></span>  
 <span data-ttu-id="23371-281">[條件評估與動作執行](../core/condition-evaluation-and-action-execution.md) </span><span class="sxs-lookup"><span data-stu-id="23371-281">[Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) </span></span>  
 [<span data-ttu-id="23371-282">議程與優先順序</span><span class="sxs-lookup"><span data-stu-id="23371-282">Agenda and Priority</span></span>](../core/agenda-and-priority.md)
