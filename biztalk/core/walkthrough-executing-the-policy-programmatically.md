---
title: 逐步解說： 以程式設計方式執行原則 |Microsoft Docs
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6398e7af-2ed1-4596-879c-3b7d000b8de2
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 666b674e30e548489478af898d5fe88c47d21f14
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985719"
---
# <a name="walkthrough-executing-the-policy-programmatically"></a><span data-ttu-id="dfe3a-102">逐步解說： 以程式設計方式執行原則</span><span class="sxs-lookup"><span data-stu-id="dfe3a-102">Walkthrough: Executing the Policy Programmatically</span></span>
<span data-ttu-id="dfe3a-103">本逐步解說提供逐步程序叫用您在中建立的原則[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)從主控台應用程式的逐步解說以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-103">This walkthrough provides step-by-step procedures for invoking the policy you created in the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough from a console application programmatically.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="dfe3a-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="dfe3a-104">Prerequisites</span></span>  
 <span data-ttu-id="dfe3a-105">您必須先完成[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說之前執行此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-105">You must complete the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough before you perform this walkthrough.</span></span>  

## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="dfe3a-106">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="dfe3a-106">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="dfe3a-107">此逐步解說包含兩個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-107">This walkthrough contains two procedures, as described in the following table.</span></span>  

|<span data-ttu-id="dfe3a-108">程序標題</span><span class="sxs-lookup"><span data-stu-id="dfe3a-108">Procedure title</span></span>|<span data-ttu-id="dfe3a-109">程序說明</span><span class="sxs-lookup"><span data-stu-id="dfe3a-109">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="dfe3a-110">使用 Policy.Execute 方法叫用 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="dfe3a-110">To invoke the ProcessPurchaseOrder policy by using the Policy.Execute method</span></span>|<span data-ttu-id="dfe3a-111">提供使用叫用原則的逐步指示**Policy.Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-111">Provides step-by-step instructions for invoking a policy by using the **Policy.Execute** method.</span></span>|  
|<span data-ttu-id="dfe3a-112">使用 RuleEngine.Execute 方法叫用 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="dfe3a-112">To invoke the ProcessPurchaseOrder policy by using the RuleEngine.Execute method</span></span>|<span data-ttu-id="dfe3a-113">提供使用叫用原則的逐步指示**RuleEngine.Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-113">Provides step-by-step instructions for invoking a policy by using the **RuleEngine.Execute** method.</span></span>|  

### <a name="to-invoke-the-processpurchaseorder-policy-by-using-the-policyexecute-method"></a><span data-ttu-id="dfe3a-114">使用 Policy.Execute 方法叫用 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="dfe3a-114">To invoke the ProcessPurchaseOrder policy by using the Policy.Execute method</span></span>  

1. <span data-ttu-id="dfe3a-115">開始**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-115">Start **Microsoft Visual Studio**.</span></span>  

2. <span data-ttu-id="dfe3a-116">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-116">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  

3. <span data-ttu-id="dfe3a-117">在 **新的專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-117">In the **New Project** dialog box, do the following:</span></span>  


   |             <span data-ttu-id="dfe3a-118">使用</span><span class="sxs-lookup"><span data-stu-id="dfe3a-118">Use this</span></span>              |                             <span data-ttu-id="dfe3a-119">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="dfe3a-119">To do this</span></span>                              |
   |-----------------------------------|---------------------------------------------------------------------|
   |         <span data-ttu-id="dfe3a-120">**專案類型**</span><span class="sxs-lookup"><span data-stu-id="dfe3a-120">**Project types**</span></span>         |                        <span data-ttu-id="dfe3a-121">按一下  **Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-121">Click **Visual C#**.</span></span>                         |
   |           <span data-ttu-id="dfe3a-122">**範本**</span><span class="sxs-lookup"><span data-stu-id="dfe3a-122">**Templates**</span></span>           |                   <span data-ttu-id="dfe3a-123">按一下 **主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-123">Click **Console Application**.</span></span>                    |
   |             <span data-ttu-id="dfe3a-124">**名稱**</span><span class="sxs-lookup"><span data-stu-id="dfe3a-124">**Name**</span></span>              |                       <span data-ttu-id="dfe3a-125">型別**ConsoleClient**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-125">Type **ConsoleClient**.</span></span>                       |
   |           <span data-ttu-id="dfe3a-126">**位置**</span><span class="sxs-lookup"><span data-stu-id="dfe3a-126">**Location**</span></span>            |     <span data-ttu-id="dfe3a-127">指定要儲存專案檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-127">Specify a folder where you want to save the project files.</span></span>      |
   |         <span data-ttu-id="dfe3a-128">**方案名稱**</span><span class="sxs-lookup"><span data-stu-id="dfe3a-128">**Solution Name**</span></span>         |                     <span data-ttu-id="dfe3a-129">型別**ConsoleClientSol**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-129">Type **ConsoleClientSol**.</span></span>                      |
   | <span data-ttu-id="dfe3a-130">**為解決方案建立目錄**</span><span class="sxs-lookup"><span data-stu-id="dfe3a-130">**Create directory for solution**</span></span> | <span data-ttu-id="dfe3a-131">選取此核取方塊以建立方案檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-131">Select this check box to create a directory for the solution files.</span></span> |


4. <span data-ttu-id="dfe3a-132">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-132">Click **OK**.</span></span> <span data-ttu-id="dfe3a-133">**ConsoleClient**專案應該會出現在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-133">The **ConsoleClient** project should appear in Solution Explorer.</span></span> <span data-ttu-id="dfe3a-134">如果看不到方案總管 中，按一下**方案總管**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-134">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  

5. <span data-ttu-id="dfe3a-135">在 [方案總管] 中，以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-135">In Solution Explorer, right-click **References**, and then click **Add Reference**.</span></span>  

6. <span data-ttu-id="dfe3a-136">按一下 **瀏覽**，瀏覽至**\Program Files\Common Files\Microsoft BizTalk**，然後按兩下**Microsoft.RuleEngine.dll**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-136">Click **Browse**, browse to the **\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.RuleEngine.dll**.</span></span>  

7. <span data-ttu-id="dfe3a-137">將下列幾行加入至頂端**Program.cs**在現有的檔案`using`陳述式：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-137">Add the following lines to the top of the **Program.cs** file after the existing `using` statements:</span></span>  

   ```  
   //To use the XmlDocument class  
   using System.Xml;  
   //To use the TypedXmlDocument and Policy classes  
   using Microsoft.RuleEngine;   
   ```  

8. <span data-ttu-id="dfe3a-138">將下列程式碼加入**Main**函式來建立**TypedXmlDocument** XML 文件為基礎的物件：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-138">Add the following code to the **Main** function to create a **TypedXmlDocument** object based on the XML document:</span></span>  

   ```  
   XmlDocument doc = new XmlDocument();  
   //Loading the XML from SamplePO.xml file.  
   //Change the directory as needed  
   doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
   TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
   ```  

9. <span data-ttu-id="dfe3a-139">將下列程式碼加入**Main**函式來執行原則：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-139">Add the following code to the **Main** function to execute the policy:</span></span>  

    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  

10. <span data-ttu-id="dfe3a-140">列印輸出 XML 檔，確認已選取的值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-140">Print the output XML to confirm that the value of the **Status** field is set to **Approved**.</span></span> <span data-ttu-id="dfe3a-141">請注意，不同於 「 商務規則編輯器 」 中，叫用**Policy.Execute**方法不會變更原始文件。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-141">Note that unlike the Business Rule Composer, invoking the **Policy.Execute** method does not change the original document.</span></span>  

    ```  
    //Print the output document  
    Console.WriteLine(txd.Document.OuterXml);   
    ```  

11. <span data-ttu-id="dfe3a-142">在 [**建置**功能表上，按一下**建置 consoleclient]**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-142">On the **Build** menu, click **Build ConsoleClient**.</span></span>  

12. <span data-ttu-id="dfe3a-143">按 CTRL+F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-143">Press CTRL+F5 to execute the application.</span></span> <span data-ttu-id="dfe3a-144">確認已選取的值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-144">Confirm that the value of the **Status** field is set to **Approved**.</span></span>  

### <a name="to-invoke-the-processpurchaseorder-policy-by-using-the-ruleengineexecute-method"></a><span data-ttu-id="dfe3a-145">使用 RuleEngine.Execute 方法叫用 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="dfe3a-145">To invoke the ProcessPurchaseOrder policy by using the RuleEngine.Execute method</span></span>  

1.  <span data-ttu-id="dfe3a-146">在 [方案總管] 中，以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-146">In Solution Explorer, right-click **References**, and then click **Add Reference**.</span></span>  

2.  <span data-ttu-id="dfe3a-147">按一下 **瀏覽**，瀏覽至**\Program Files\Common Files\Microsoft BizTalk**，然後按兩下**Microsoft.BizTalk.RuleEngineExtensions.dll**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-147">Click **Browse**, browse to **\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.BizTalk.RuleEngineExtensions.dll**.</span></span>  

3.  <span data-ttu-id="dfe3a-148">標記為註解中的下列行**Program.cs**檔案：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-148">Comment out the following lines in the **Program.cs** file:</span></span>  

    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  

4.  <span data-ttu-id="dfe3a-149">在加入註解的程式碼後面，再加入下列程式碼，以存取「規則引擎」資料庫：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-149">Add the following code after the commented-out code to get access to the Rule Engine database:</span></span>  

    ```  
    //Get access to the SQL rule store   
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    ```  

5.  <span data-ttu-id="dfe3a-150">新增下列程式碼，以取得存取權**RuleSetInfoCollection** ProcessPurchaseOrder 原則：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-150">Add the following code to get access to **RuleSetInfoCollection** for the ProcessPurchaseOrder policy:</span></span>  

    ```  
    //Get access to RuleSetInfoCollection for the   
    //ProcessPurchaseOrder policy  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    ```  

6.  <span data-ttu-id="dfe3a-151">新增下列程式碼，以建立**RuleSet**物件根據 ProcessPurchaseOrder 原則的規則集資訊：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-151">Add the following code to create a **RuleSet** object based on the rule set information for the ProcessPurchaseOrder policy:</span></span>  

    ```  
    //Create a RuleSet object based on the rule set information   
    //for the ProcessPurchaseOrder policy  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    ```  

7.  <span data-ttu-id="dfe3a-152">新增下列程式碼，以建立**RuleEngine**物件：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-152">Add the following code to create the **RuleEngine** object:</span></span>  

    ```  
    //Create the RuleEngine object  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    ```  

8.  <span data-ttu-id="dfe3a-153">新增下列程式碼，判斷提示**TypedXmlDocument**物件至規則引擎工作記憶體：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-153">Add the following code to assert the **TypedXmlDocument** object into the working memory of the rule engine:</span></span>  

    ```  
    //Assert the TypedXmlDocument object into working memory  
    //of the rule engine  
    engine.Assert(txd);  
    ```  

9. <span data-ttu-id="dfe3a-154">現在加入程式碼以使用執行原則**RuleEngine.Execute**方法：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-154">Now add the code to execute the policy by using the **RuleEngine.Execute** method:</span></span>  

    ```  
    //Execute the policy by invoking RuleEngine.Execute method  
    engine.Execute();  
    ```  

10. <span data-ttu-id="dfe3a-155">請確定**Console.WriteLine**陳述式是中的最後一個陳述式**Main**函式。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-155">Make sure that the **Console.WriteLine** statement is the last statement in the **Main** function.</span></span>  

11. <span data-ttu-id="dfe3a-156">在 [**建置**功能表上，按一下**建置 consoleclient]**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-156">On the **Build** menu, click **Build ConsoleClient**.</span></span>  

12. <span data-ttu-id="dfe3a-157">按 CTRL+F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-157">Press CTRL+F5 to execute the application.</span></span> <span data-ttu-id="dfe3a-158">確認已選取的值**狀態**欄位設定為**Approved**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-158">Confirm that the value of the **Status** field is set to **Approved**.</span></span>  

## <a name="comments"></a><span data-ttu-id="dfe3a-159">註解</span><span class="sxs-lookup"><span data-stu-id="dfe3a-159">Comments</span></span>  

-   <span data-ttu-id="dfe3a-160">完整程式碼**Main**函式，藉由使用執行 ProcessPurchaseOrder 原則**Policy.Execute**方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-160">Complete code for the **Main** function to execute the ProcessPurchaseOrder policy by using the **Policy.Execute** method is as follows:</span></span>  

    ```  
    static void Main(string[] args)  
    {  
    XmlDocument doc = new XmlDocument();  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    policy.Execute(txd);  
    Console.WriteLine(txd.Document.OuterXml);   
    }  
    ```  

-   <span data-ttu-id="dfe3a-161">使用執行 ProcessPurchaseOrder 原則的完整程式碼**RuleEngine.Execute**方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-161">Complete code for executing the ProcessPurchaseOrder policy by using the **RuleEngine.Execute** method is as follows:</span></span>  

    ```  
    static void Main(string[] args)  
    {  
    XmlDocument doc = new XmlDocument();  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    engine.Assert(txd);  
    engine.Execute();  
    Console.WriteLine(txd.Document.OuterXml);   
    }  
    ```  

-   <span data-ttu-id="dfe3a-162">您可能想要新增**console.readline （)** 陳述式的結尾**Main**函式，以便應用程式會等到您結束應用程式。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-162">You may want to add a **Console.ReadLine()** statement at the end of the **Main** function so that the application waits for you to terminate the application.</span></span>  

-   <span data-ttu-id="dfe3a-163">在此逐步解說中，用戶端只提交一個事實至 ProcessPurchaseOrder 原則。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-163">In this walkthrough, the client submits only one fact to the ProcessPurchaseOrder policy.</span></span> <span data-ttu-id="dfe3a-164">如果用戶端必須提交一個以上的事實至原則，它必須建立事實陣列，並使用多載**Execute**採用陣列做為參數的方法。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-164">If the client needs to submit more than one fact to a policy, it needs to create an array of facts and use the overloaded **Execute** method that takes an array as a parameter.</span></span> <span data-ttu-id="dfe3a-165">下列程式碼範例將示範如何執行這項工作：</span><span class="sxs-lookup"><span data-stu-id="dfe3a-165">The following sample code shows how to do that:</span></span>  

    ```  
    Policy policy = new Policy("PolicyName");  
    object[] facts = new object[2];  
    facts[0] = txd;  
    facts[1] = new MyClass();  
    policy.Execute(facts);  
    policy.Dispose();  
    ```  

-   <span data-ttu-id="dfe3a-166">第一個參數**TypedXmlDocument**建構函式程式碼中的是您用來建置原則型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-166">The first parameter to the **TypedXmlDocument** constructor in the code is the name of the type you used to build the policy.</span></span>  

-   <span data-ttu-id="dfe3a-167">**Policy.Execute**方法基本上是一個包裝函式**RuleEngine.Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-167">The **Policy.Execute** method is basically a wrapper around the **RuleEngine.Execute** method.</span></span> <span data-ttu-id="dfe3a-168">因此，使用**Policy.Execute**如您所見本逐步解說中，方法是叫用原則，最簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-168">Therefore, using the **Policy.Execute** method is the easiest way of invoking a policy, as you have seen in this walkthrough.</span></span>  

-   <span data-ttu-id="dfe3a-169">進一步控制執行原則的詳細資訊，您可能想要**RuleEngine.Execute**方法，而不是使用**Policy.Execute**。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-169">For more control over the execution of the policy, you may want to use the **RuleEngine.Execute** method instead of using **Policy.Execute**.</span></span> <span data-ttu-id="dfe3a-170">例如，您可以暫時終止引擎利用**暫止**函式，然後再繼續執行時，使用**Execute**函式。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-170">For example, you can halt the engine temporarily by using the **Halt** function, and then resume it by using the **Execute** function.</span></span> <span data-ttu-id="dfe3a-171">如需詳細資訊，請參閱 <<c0> [ 暫止](../core/halt.md)。</span><span class="sxs-lookup"><span data-stu-id="dfe3a-171">For more information, see [Halt](../core/halt.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="dfe3a-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfe3a-172">See Also</span></span>  
 [<span data-ttu-id="dfe3a-173">如何執行原則</span><span class="sxs-lookup"><span data-stu-id="dfe3a-173">How to Execute Policies</span></span>](../core/how-to-execute-policies.md)