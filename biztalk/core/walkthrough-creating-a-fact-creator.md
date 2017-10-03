---
title: "逐步解說： 建立事實建立者 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 041c8f73-c72e-43fd-8446-144cecdc95ef
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a1c91417cb58eb53e35c724513d4f955e4e6b6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-fact-creator"></a><span data-ttu-id="ac137-102">逐步解說： 建立事實建立者</span><span class="sxs-lookup"><span data-stu-id="ac137-102">Walkthrough: Creating a Fact Creator</span></span>
<span data-ttu-id="ac137-103">此逐步解說提供逐步程序建立事實建立者元件， **POFactCreator**，可用來測試**ProcessPurchaseOrder**您稍早在建立的原則逐步解說。</span><span class="sxs-lookup"><span data-stu-id="ac137-103">This walkthrough provides step-by-step procedures for creating a fact creator component, **POFactCreator**, which you can use to test the **ProcessPurchaseOrder** policy you created in earlier walkthroughs.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ac137-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="ac137-104">Prerequisites</span></span>  
 <span data-ttu-id="ac137-105">您必須先完成[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說之前執行此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="ac137-105">You must complete the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough before you perform this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="ac137-106">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="ac137-106">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="ac137-107">此逐步解說包含兩個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="ac137-107">This walkthrough contains two procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="ac137-108">程序標題</span><span class="sxs-lookup"><span data-stu-id="ac137-108">Procedure title</span></span>|<span data-ttu-id="ac137-109">程序說明</span><span class="sxs-lookup"><span data-stu-id="ac137-109">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="ac137-110">建立 POFactCreator 元件</span><span class="sxs-lookup"><span data-stu-id="ac137-110">To create the POFactCreator component</span></span>|<span data-ttu-id="ac137-111">提供建立事實建立者元件的逐步指示**POFactCreator**。</span><span class="sxs-lookup"><span data-stu-id="ac137-111">Provides step-by-step instructions for creating a fact creator component, **POFactCreator**.</span></span>|  
|<span data-ttu-id="ac137-112">使用 POFactCreator 測試 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="ac137-112">To test the ProcessPurchaseOrder policy using POFactCreator</span></span>|<span data-ttu-id="ac137-113">提供逐步指示，使用 「 商務規則編輯器 」 工具來測試**ProcessPurchaseOrder**原則使用**POFactCreator**元件。</span><span class="sxs-lookup"><span data-stu-id="ac137-113">Provides step-by-step instructions for using the Business Rule Composer tool to test the **ProcessPurchaseOrder** policy by using the **POFactCreator** component.</span></span>|  
  
### <a name="to-create-the-pofactcreator-component"></a><span data-ttu-id="ac137-114">建立 POFactCreator 元件</span><span class="sxs-lookup"><span data-stu-id="ac137-114">To create the POFactCreator component</span></span>  
  
1.  <span data-ttu-id="ac137-115">啟動**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="ac137-115">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="ac137-116">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="ac137-116">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="ac137-117">在**新專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac137-117">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="ac137-118">使用</span><span class="sxs-lookup"><span data-stu-id="ac137-118">Use this</span></span>|<span data-ttu-id="ac137-119">動作</span><span class="sxs-lookup"><span data-stu-id="ac137-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ac137-120">**專案類型**</span><span class="sxs-lookup"><span data-stu-id="ac137-120">**Project types**</span></span>|<span data-ttu-id="ac137-121">按一下**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="ac137-121">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="ac137-122">**範本**</span><span class="sxs-lookup"><span data-stu-id="ac137-122">**Templates**</span></span>|<span data-ttu-id="ac137-123">按一下**類別庫**。</span><span class="sxs-lookup"><span data-stu-id="ac137-123">Click **Class Library**.</span></span>|  
    |<span data-ttu-id="ac137-124">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ac137-124">**Name**</span></span>|<span data-ttu-id="ac137-125">型別**POFactCreatorLib**。</span><span class="sxs-lookup"><span data-stu-id="ac137-125">Type **POFactCreatorLib**.</span></span>|  
    |<span data-ttu-id="ac137-126">**位置**</span><span class="sxs-lookup"><span data-stu-id="ac137-126">**Location**</span></span>|<span data-ttu-id="ac137-127">指定**C:\BRE-Walkthroughs**做為位置。</span><span class="sxs-lookup"><span data-stu-id="ac137-127">Specify **C:\BRE-Walkthroughs** as the location.</span></span>|  
    |<span data-ttu-id="ac137-128">**方案名稱**</span><span class="sxs-lookup"><span data-stu-id="ac137-128">**Solution Name**</span></span>|<span data-ttu-id="ac137-129">型別**POFactCreatorSol**。</span><span class="sxs-lookup"><span data-stu-id="ac137-129">Type **POFactCreatorSol**.</span></span>|  
    |<span data-ttu-id="ac137-130">**為方案建立目錄**</span><span class="sxs-lookup"><span data-stu-id="ac137-130">**Create directory for solution**</span></span>|<span data-ttu-id="ac137-131">選取此核取方塊以建立方案檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="ac137-131">Select this check box to create a directory for the solution files.</span></span>|  
  
4.  <span data-ttu-id="ac137-132">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ac137-132">Click **OK**.</span></span> <span data-ttu-id="ac137-133">**POFactCreatorLib**專案應該會出現在 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="ac137-133">The **POFactCreatorLib** project should appear in Solution Explorer.</span></span> <span data-ttu-id="ac137-134">如果看不到方案總管 中，按一下**方案總管 中**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="ac137-134">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="ac137-135">在 [屬性] 視窗中，變更名稱的檔案，請**Class1.cs**至**POFactCreator.cs**。</span><span class="sxs-lookup"><span data-stu-id="ac137-135">In the Properties window, change the name of the file, **Class1.cs**, to **POFactCreator.cs**.</span></span>  
  
6.  <span data-ttu-id="ac137-136">在方案總管] 視窗中，以滑鼠右鍵按一下**參考**，然後按一下 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="ac137-136">In the Solution Explorer window, right-click **References**, and then click **Add Reference**.</span></span>  
  
7.  <span data-ttu-id="ac137-137">按一下**瀏覽**，瀏覽至**C:\Program Files\Common Files\Microsoft BizTalk**，然後按兩下**Microsoft.RuleEngine.dll**。</span><span class="sxs-lookup"><span data-stu-id="ac137-137">Click **Browse**, navigate to **C:\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.RuleEngine.dll**.</span></span>  
  
8.  <span data-ttu-id="ac137-138">將下列行加入至頂端**POFactCreator.cs**檔案的現有`using`陳述式：</span><span class="sxs-lookup"><span data-stu-id="ac137-138">Add the following lines to the top of the **POFactCreator.cs** file after the existing `using` statements:</span></span>  
  
    ```  
    //To use the XmlDocument class  
    using System.Xml;  
    //To use the TypedXmlDocument and Policy classes  
    using Microsoft.RuleEngine;   
    ```  
  
9. <span data-ttu-id="ac137-139">修改**POFactCreator**類別衍生自**IFactCreator**介面：</span><span class="sxs-lookup"><span data-stu-id="ac137-139">Modify the **POFactCreator** class to derive from the **IFactCreator** interface:</span></span>  
  
    ```  
    public class POFactCreator : IFactCreator  
    {  
    }  
    ```  
  
10. <span data-ttu-id="ac137-140">以滑鼠右鍵按一下**IFactCreator**，指向 **實作介面**，然後按一下 **實作介面**。</span><span class="sxs-lookup"><span data-stu-id="ac137-140">Right-click **IFactCreator**, point to **Implement Interface**, and then click **Implement Interface**.</span></span>  
  
     <span data-ttu-id="ac137-141">![BRE &#45;逐步解說 &#45; ImplementInterface](../core/media/ca1ae06c-ad24-4eac-94c3-5a06ad0f7305.gif "ca1ae06c-ad24-4eac-94c3-5a06ad0f7305")</span><span class="sxs-lookup"><span data-stu-id="ac137-141">![BRE&#45;Walkthrough&#45;ImplementInterface](../core/media/ca1ae06c-ad24-4eac-94c3-5a06ad0f7305.gif "ca1ae06c-ad24-4eac-94c3-5a06ad0f7305")</span></span>  
  
11. <span data-ttu-id="ac137-142">新增公用建構函式來**POFactCreator**類別如下所示：</span><span class="sxs-lookup"><span data-stu-id="ac137-142">Add a public constructor to the **POFactCreator** class as shown below:</span></span>  
  
    ```  
    public POFactCreator()  
    {  
    }  
    ```  
  
12. <span data-ttu-id="ac137-143">中的單獨陳述式中移除**CreateFacts**方法。</span><span class="sxs-lookup"><span data-stu-id="ac137-143">Remove the lone statement in the **CreateFacts** method.</span></span>  
  
13. <span data-ttu-id="ac137-144">將下列程式碼加入**CreateFacts**方法來建立**TypedXmlDocument**物件根據**SamplePO.xml**文件：</span><span class="sxs-lookup"><span data-stu-id="ac137-144">Add the following code to the **CreateFacts** method to create a **TypedXmlDocument** object based on the **SamplePO.xml** document:</span></span>  
  
    ```  
    XmlDocument doc = new XmlDocument();  
    //Loading the XML from SamplePO.xml file.  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    ```  
  
14. <span data-ttu-id="ac137-145">加入下列程式碼，建立與事實陣列**TypedXmlDocument**物件做為唯一事實：</span><span class="sxs-lookup"><span data-stu-id="ac137-145">Add the following code to create an array of facts with the **TypedXmlDocument** object as the only fact:</span></span>  
  
    ```  
    object[] facts = new object[1];  
    facts[0] = txd;   
    ```  
  
15. <span data-ttu-id="ac137-146">傳回事實陣列從**CreateFacts**方法：</span><span class="sxs-lookup"><span data-stu-id="ac137-146">Return the facts array from the **CreateFacts** method:</span></span>  
  
    ```  
    return facts;  
    ```  
  
16. <span data-ttu-id="ac137-147">確認在的完整程式碼**CreateFacts**方法看起來如下：</span><span class="sxs-lookup"><span data-stu-id="ac137-147">Verify that the complete code in the **CreateFacts** method looks like the following:</span></span>  
  
    ```  
    public object[] CreateFacts(RuleSetInfo ruleSetInfo)  
    {  
    XmlDocument doc = new XmlDocument();  
    //Loading the XML from SamplePO.xml file.  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
  
    object[] facts = new object[1];  
    facts[0] = txd;  
    return facts;  
    }  
    ```  
  
17. <span data-ttu-id="ac137-148">中的單獨陳述式中移除**GetFactTypes**方法。</span><span class="sxs-lookup"><span data-stu-id="ac137-148">Remove the lone statement in the **GetFactTypes** method.</span></span>  
  
18. <span data-ttu-id="ac137-149">將下列程式碼加入**GetFactTypes**方法以傳回包含類型的類型陣列**TypedXmlDocument**類別：</span><span class="sxs-lookup"><span data-stu-id="ac137-149">Add the following code to the **GetFactTypes** method to return an array of types containing the type of the **TypedXmlDocument** class:</span></span>  
  
    ```  
    Type[] t = new Type[1];  
    t[0] = typeof(TypedXmlDocument);  
    return t;  
    ```  
  
19. <span data-ttu-id="ac137-150">啟動**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="ac137-150">Start **Visual Studio Command Prompt**.</span></span>  
  
20. <span data-ttu-id="ac137-151">將目錄變更**C:\BRE-Walkthroughs\POFactCreatorSol**，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="ac137-151">Change the directory to **C:\BRE-Walkthroughs\POFactCreatorSol**, and then execute the following command:</span></span>  
  
     <span data-ttu-id="ac137-152">**Sn-k POFactCreator.snk**</span><span class="sxs-lookup"><span data-stu-id="ac137-152">**Sn -k POFactCreator.snk**</span></span>  
  
21. <span data-ttu-id="ac137-153">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，展開**屬性**，然後按兩下**AssemblyInfo.cs**。</span><span class="sxs-lookup"><span data-stu-id="ac137-153">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, expand **Properties**, and then double-click **AssemblyInfo.cs**.</span></span>  
  
22. <span data-ttu-id="ac137-154">加入下列陳述式來**AssemblyInfo.cs**檔案結尾：</span><span class="sxs-lookup"><span data-stu-id="ac137-154">Add the following statement to the **AssemblyInfo.cs** file at the end:</span></span>  
  
    ```  
    [assembly: AssemblyKeyFile(@"C:\BRE-Walkthroughs\POFactCreatorSol\POFactCreator.snk")]  
    ```  
  
23. <span data-ttu-id="ac137-155">在方案總管] 視窗中，以滑鼠右鍵按一下**POFactCreatorLib**，然後按一下 [**建置**。</span><span class="sxs-lookup"><span data-stu-id="ac137-155">In the Solution Explorer window, right-click **POFactCreatorLib**, and then click **Build**.</span></span>  
  
24. <span data-ttu-id="ac137-156">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元中，將目錄變更**C:\BRE-Walkthroughs\POFactCreatorSol\POFactCreatorLib\Bin\Debug**，然後執行下列命令，以註冊**POFactCreator**元件在 gac （全域組件快取）。</span><span class="sxs-lookup"><span data-stu-id="ac137-156">At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt, change the directory to **C:\BRE-Walkthroughs\POFactCreatorSol\POFactCreatorLib\Bin\Debug**, and then execute the following command to register the **POFactCreator** component with the GAC (global assembly cache).</span></span> <span data-ttu-id="ac137-157">如果沒有開啟命令提示字元，請執行步驟 19 來開啟。</span><span class="sxs-lookup"><span data-stu-id="ac137-157">If you do not have the command prompt open, follow step 19 to open it.</span></span>  
  
     <span data-ttu-id="ac137-158">**Gacutil-i POFactCreatorLib.dll**</span><span class="sxs-lookup"><span data-stu-id="ac137-158">**Gacutil -i POFactCreatorLib.dll**</span></span>  
  
### <a name="to-test-the-processpurchaseorder-policy-using-pofactcreator"></a><span data-ttu-id="ac137-159">使用 POFactCreator 測試 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="ac137-159">To test the ProcessPurchaseOrder policy using POFactCreator</span></span>  
  
1.  <span data-ttu-id="ac137-160">在**啟動**功能表上，指向**所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="ac137-160">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rule Composer**.</span></span> <span data-ttu-id="ac137-161">如果已經開啟 [商務規則編輯器]，請按 F5 重新整理。</span><span class="sxs-lookup"><span data-stu-id="ac137-161">If you have the Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac137-162">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="ac137-162">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="ac137-163">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="ac137-163">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="ac137-164">在 [原則總管] 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrder**，最新版本中，以滑鼠右鍵按一下，然後按一下**測試原則**。</span><span class="sxs-lookup"><span data-stu-id="ac137-164">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click the latest version, and then click **Test Policy**.</span></span>  
  
     <span data-ttu-id="ac137-165">![商務規則編輯器 &#45;TestPolicyMenu](../core/media/af63c437-aeba-4e6a-a772-3346e7babee5.gif "af63c437-aeba-4e6a-a772-3346e7babee5")</span><span class="sxs-lookup"><span data-stu-id="ac137-165">![Business Rule Composer&#45;TestPolicyMenu](../core/media/af63c437-aeba-4e6a-a772-3346e7babee5.gif "af63c437-aeba-4e6a-a772-3346e7babee5")</span></span>  
  
3.  <span data-ttu-id="ac137-166">在對話方塊底部，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="ac137-166">At the bottom of the dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="ac137-167">在**.NET 組件**對話方塊中，選取**pofactcreatorlib**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ac137-167">In the **.NET Assemblies** dialog box, select **POFactCreatorLib**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="ac137-168">在**選取繫結**對話方塊中，按一下**POFactCreator**中**POFactCreatorLib，10.0.0**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ac137-168">In the **Select Binding** dialog box, click **POFactCreator** in **POFactCreatorLib, 10.0.0**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="ac137-169">按一下**測試**。</span><span class="sxs-lookup"><span data-stu-id="ac137-169">Click **Test**.</span></span>  
  
7.  <span data-ttu-id="ac137-170">確認**ApprovalRule**引發輸出 視窗中。</span><span class="sxs-lookup"><span data-stu-id="ac137-170">Verify that the **ApprovalRule** is fired in the Output window.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="ac137-171">註解</span><span class="sxs-lookup"><span data-stu-id="ac137-171">Comments</span></span>  
  
-   <span data-ttu-id="ac137-172">若要使用「商務規則編輯器」來測試使用 .NET 類別之非靜態方法的原則，您必須建立事實建立者元件。</span><span class="sxs-lookup"><span data-stu-id="ac137-172">To test a policy that uses non-static methods of a .NET class by using the Business Rule Composer, you must create a fact creator component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac137-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac137-173">See Also</span></span>  
 [<span data-ttu-id="ac137-174">如何建立事實擷取器</span><span class="sxs-lookup"><span data-stu-id="ac137-174">How to Create a Fact Retriever</span></span>](../core/how-to-create-a-fact-retriever.md)