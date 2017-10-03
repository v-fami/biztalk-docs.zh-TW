---
title: "逐步解說： 建立簡單商務原則 |Microsoft 文件"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02d35735-dce2-4ee2-965e-dae307a125b0
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c894ab80926d2fad66af540c492dd053570aaa4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-simple-business-policy"></a><span data-ttu-id="dc381-102">逐步解說： 建立簡單商務原則</span><span class="sxs-lookup"><span data-stu-id="dc381-102">Walkthrough: Creating a Simple Business Policy</span></span>
<span data-ttu-id="dc381-103">本逐步解說提供逐步程序，使用 「 商務規則編輯器 」 建立名為的簡單商務原則**ProcessPurchaseOrder**包含名為的規則**ApprovedRule**。</span><span class="sxs-lookup"><span data-stu-id="dc381-103">This walkthrough provides step-by-step procedures for using the Business Rule Composer to create a simple business policy named **ProcessPurchaseOrder** containing a rule named **ApprovedRule**.</span></span> <span data-ttu-id="dc381-104">**ApprovedRule**規則需要使用者提交 XML 文件當做事實，並將值設定**狀態**欄位中的文件**Approved**如果值**數量**欄位是否小於或等於**500**。</span><span class="sxs-lookup"><span data-stu-id="dc381-104">The **ApprovedRule** rule expects the user to submit an XML document as a fact, and sets the value of the **Status** field in the document to **Approved** if the value of the **Quantity** field is less than or equal to **500**.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dc381-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="dc381-105">Prerequisites</span></span>  
 <span data-ttu-id="dc381-106">您必須先熟悉的商務規則架構，才能執行此逐步解說的基本概念。</span><span class="sxs-lookup"><span data-stu-id="dc381-106">You must be familiar with the basics of the Business Rules Framework to perform this walkthrough.</span></span> <span data-ttu-id="dc381-107">如果您不熟悉 「 商務規則架構，我們建議您閱讀商務規則架構 」 架構概觀[商務規則引擎](../core/business-rules-engine.md)然後再執行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="dc381-107">If you are new to the Business Rules Framework, we recommend that you read the architecture overview of the Business Rules Framework at [Business Rules Engine](../core/business-rules-engine.md) before performing this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="dc381-108">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="dc381-108">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="dc381-109">此逐步解說包含兩個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="dc381-109">This walkthrough contains two procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="dc381-110">程序標題</span><span class="sxs-lookup"><span data-stu-id="dc381-110">Procedure title</span></span>|<span data-ttu-id="dc381-111">程序說明</span><span class="sxs-lookup"><span data-stu-id="dc381-111">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="dc381-112">建立 PO 結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="dc381-112">To create the PO schema file</span></span>|<span data-ttu-id="dc381-113">提供建立文件的結構描述的逐步指示**ProcessPurchaseOrder**原則會使用。</span><span class="sxs-lookup"><span data-stu-id="dc381-113">Provides step-by-step instructions for creating the schema for the document that the **ProcessPurchaseOrder** policy uses.</span></span>|  
|<span data-ttu-id="dc381-114">建立 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="dc381-114">To create the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="dc381-115">提供逐步指示，建立**ProcessPurchaseOrder**使用商務規則編輯器 」 的原則。</span><span class="sxs-lookup"><span data-stu-id="dc381-115">Provides step-by-step instructions for creating the **ProcessPurchaseOrder** policy by using the Business Rule Composer.</span></span>|  
  
### <a name="to-create-the-po-schema-file"></a><span data-ttu-id="dc381-116">建立 PO 結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="dc381-116">To create the PO schema file</span></span>  
  
1.  <span data-ttu-id="dc381-117">在**啟動**功能表中，開啟**記事本**。</span><span class="sxs-lookup"><span data-stu-id="dc381-117">On the **Start** menu, open **Notepad**.</span></span>  
  
2.  <span data-ttu-id="dc381-118">在 [ **檔案** ] 功能表上，指向 [ **新增**]，然後按一下 [ **檔案**]。</span><span class="sxs-lookup"><span data-stu-id="dc381-118">On the **File** menu, point to **New**, and then click **File**.</span></span>  
  
3.  <span data-ttu-id="dc381-119">將下列 XML 文字複製到編輯器中：</span><span class="sxs-lookup"><span data-stu-id="dc381-119">Copy the following XML text to the editor:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://EAISolution.PurchaseOrder" targetNamespace="http://EAISolution.PurchaseOrder" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      <xs:element name="PurchaseOrder">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="Header">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="ReqID" type="xs:string" />  
                  <xs:element name="Date" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Item">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="Description" type="xs:string" />  
                  <xs:element name="Quantity" type="xs:int" />  
                  <xs:element name="UnitPrice" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Status" type="xs:string" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
4.  <span data-ttu-id="dc381-120">在**檔案**功能表上，按一下 **另存 TextFile1.txt 為**。</span><span class="sxs-lookup"><span data-stu-id="dc381-120">On the **File** menu, click **Save TextFile1.txt As**.</span></span>  
  
5.  <span data-ttu-id="dc381-121">值變更**另存新檔類型**從**文字文件 (\*.txt)**至**所有檔案**。</span><span class="sxs-lookup"><span data-stu-id="dc381-121">Change the value for **Save As type** from **Text Documents(\*.txt)** to **All Files**.</span></span>  
  
6.  <span data-ttu-id="dc381-122">型別**PO.xsd**中**檔案名稱**文字方塊中，將目錄變更**C:\BRE-Walkthroughs**，變更的值**編碼**至**Unicode** ，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="dc381-122">Type **PO.xsd** in the **File name** text box, change the directory to **C:\BRE-Walkthroughs**, change the value of **Encoding** to **Unicode** and then click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc381-123">建立目錄**BRE 逐步解說**下**c:\\** 如果不存在，然後再按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="dc381-123">Create the directory **BRE-Walkthroughs** under **C:\\** if it does not exist, and then click **Save**.</span></span>  
  
7.  <span data-ttu-id="dc381-124">關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="dc381-124">Close Notepad.</span></span>  
  
### <a name="to-create-the-processpurchaseorder-business-policy"></a><span data-ttu-id="dc381-125">建立 ProcessPurchaseOrder 商務原則</span><span class="sxs-lookup"><span data-stu-id="dc381-125">To create the ProcessPurchaseOrder business policy</span></span>  
  
1.  <span data-ttu-id="dc381-126">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="dc381-126">On the **Start** menu, open **Business Rule Composer**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc381-127">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="dc381-127">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="dc381-128">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="dc381-128">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc381-129">「 商務規則編輯器 」 會顯示**開啟規則存放區**對話方塊中的電腦上第一次開啟時。</span><span class="sxs-lookup"><span data-stu-id="dc381-129">The Business Rule Composer displays the **Open Rule Store** dialog box when it is opened for the first time on a computer.</span></span> <span data-ttu-id="dc381-130">如果您看到**開啟規則存放區**對話方塊中，按一下 **確定**之後驗證的 SQL server 名稱和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="dc381-130">If you see the **Open Rule Store** dialog box, click **OK** after verifying the SQL server name and database name.</span></span>  
  
2.  <span data-ttu-id="dc381-131">在原則總管] 視窗中，以滑鼠右鍵按一下**原則**，然後按一下 [**新增原則**。</span><span class="sxs-lookup"><span data-stu-id="dc381-131">In the Policy Explorer window, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
3.  <span data-ttu-id="dc381-132">編輯原則的名稱， **[policy1]**至**ProcessPurchaseOrder**按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="dc381-132">Edit the name of the policy, **Policy1**, to **ProcessPurchaseOrder** and press ENTER.</span></span> <span data-ttu-id="dc381-133">您也可以變更原則的名稱**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="dc381-133">You can also change the name of the policy in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="dc381-134">以滑鼠右鍵按一下**1.0 版**，然後按一下  **AddNewRule**。</span><span class="sxs-lookup"><span data-stu-id="dc381-134">Right-click **Version 1.0**, and then click **AddNewRule**.</span></span>  
  
5.  <span data-ttu-id="dc381-135">編輯名稱，將規則和**Rule1**至**ApprovalRule**按下 ENTER**。**</span><span class="sxs-lookup"><span data-stu-id="dc381-135">Edit the name of the rule from **Rule1** to **ApprovalRule** and press ENTER**.**</span></span> <span data-ttu-id="dc381-136">您也可以變更中規則的名稱**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="dc381-136">You can also change the name of the rule in the **Properties** window.</span></span>  
  
6.  <span data-ttu-id="dc381-137">在 事實總管 視窗中，按一下**XML 結構描述** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="dc381-137">In the Facts Explorer window, click the **XML Schemas** tab.</span></span>  
  
7.  <span data-ttu-id="dc381-138">以滑鼠右鍵按一下**結構描述**，按一下 **瀏覽**，然後選取**PO.xsd**您稍早建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="dc381-138">Right-click **Schemas**, click **Browse**, and then select the **PO.xsd** file that you created earlier.</span></span>  
  
8.  <span data-ttu-id="dc381-139">在 [屬性] 視窗中變更的值**文件類型**屬性從**PO**至**[ruletest.po]**。</span><span class="sxs-lookup"><span data-stu-id="dc381-139">In the properties window, change the value of the **Document Type** property from **PO** to **RuleTest.PO**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc381-140">您將建立 BizTalk 專案，名為**RuleTest**稍後[逐步解說： 叫用的原則，從協調流程](../core/walkthrough-invoking-the-policy-from-an-orchestration.md)逐步解說。</span><span class="sxs-lookup"><span data-stu-id="dc381-140">You will be creating a BizTalk project named **RuleTest** later in the [Walkthrough: Invoking the Policy from an Orchestration](../core/walkthrough-invoking-the-policy-from-an-orchestration.md) walkthrough.</span></span> <span data-ttu-id="dc381-141">逐步解說中，您將加入， **PO.xsd**檔案加入專案中，建立會叫用的協調流程**ProcessPurchaseOrder**原則，然後再測試該原則。</span><span class="sxs-lookup"><span data-stu-id="dc381-141">In that walkthrough, you will add the **PO.xsd** file to the project, create an orchestration that invokes the **ProcessPurchaseOrder** policy, and then test the policy.</span></span> <span data-ttu-id="dc381-142">若要測試的原則，從協調流程，您需要確定您變更**文件類型**屬性**\<專案名稱 >。\<SchemaName >**，也就是**[ruletest.po]**在此情況下。</span><span class="sxs-lookup"><span data-stu-id="dc381-142">To test the policy from the orchestration, you need to make sure that you change the **Document Type** property to **\<Project Name>.\<SchemaName>**, which is **RuleTest.PO** in this case.</span></span>  
  
     <span data-ttu-id="dc381-143">![BRE &#45;逐步解說 &#45;ChangeDocType](../core/media/e9a370fd-d9b2-48f0-ad0e-85a5428a9c21.gif "e9a370fd-d9b2-48f0-ad0e-85a5428a9c21")</span><span class="sxs-lookup"><span data-stu-id="dc381-143">![BRE&#45;Walkthrough&#45;ChangeDocType](../core/media/e9a370fd-d9b2-48f0-ad0e-85a5428a9c21.gif "e9a370fd-d9b2-48f0-ad0e-85a5428a9c21")</span></span>  
  
9. <span data-ttu-id="dc381-144">在 [事實總管] 視窗中，依序展開**PurchaseOrder**，然後展開**項目**。</span><span class="sxs-lookup"><span data-stu-id="dc381-144">In the Facts Explorer window, expand **PurchaseOrder**, and then expand **Item**.</span></span>  
  
10. <span data-ttu-id="dc381-145">在 IF 窗格 （上方） 右邊，以滑鼠右鍵按一下**條件**，按一下 **述詞**，然後按一下 **小於或等於**。</span><span class="sxs-lookup"><span data-stu-id="dc381-145">In the IF pane (top) on the right, right-click **Conditions**, click **Predicates**, and then click **LessThanEqual**.</span></span>  
  
     <span data-ttu-id="dc381-146">![商務規則編輯器 &#45;小於或等於](../core/media/1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7.gif "1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7")</span><span class="sxs-lookup"><span data-stu-id="dc381-146">![Business Rule Composer &#45; Less Than or Equal](../core/media/1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7.gif "1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7")</span></span>  
  
11. <span data-ttu-id="dc381-147">拖曳**數量**節點從 [事實總管] 視窗**引數 1** [IF] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="dc381-147">Drag the **Quantity** node from the Facts Explorer window to **argument1** in the IF pane.</span></span>  
  
     <span data-ttu-id="dc381-148">![商務規則編輯器 &#45;DragQuantity](../core/media/4742eca6-4a8a-401d-8989-cab4e8025fb3.gif "4742eca6-4a8a-401d-8989-cab4e8025fb3")</span><span class="sxs-lookup"><span data-stu-id="dc381-148">![Business Rule Composer &#45; DragQuantity](../core/media/4742eca6-4a8a-401d-8989-cab4e8025fb3.gif "4742eca6-4a8a-401d-8989-cab4e8025fb3")</span></span>  
  
     <span data-ttu-id="dc381-149">![商務規則編輯器 &#45;UseQuantity](../core/media/ee4f61b1-0f15-4329-b0b5-9badd21dcd61.gif "ee4f61b1-0f15-4329-b0b5-9badd21dcd61")</span><span class="sxs-lookup"><span data-stu-id="dc381-149">![Business Rule Composer&#45;UseQuantity](../core/media/ee4f61b1-0f15-4329-b0b5-9badd21dcd61.gif "ee4f61b1-0f15-4329-b0b5-9badd21dcd61")</span></span>  
  
12. <span data-ttu-id="dc381-150">在 IF 窗格中，按一下 **引數 2**，型別`500`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="dc381-150">In the IF pane, click **argument2**, type `500`, and then press ENTER.</span></span>  
  
13. <span data-ttu-id="dc381-151">拖曳**狀態**節點從 [事實總管] 視窗右下角的商務規則編輯器 [THEN] 窗格。</span><span class="sxs-lookup"><span data-stu-id="dc381-151">Drag the **Status** node from the Facts Explorer window to the THEN pane at the bottom-right side of Business Rule Composer.</span></span>  
  
     <span data-ttu-id="dc381-152">![商務規則編輯器 &#45; DragStatus](../core/media/3617251a-a192-4aec-9474-81f6290c0832.gif "3617251a-a192-4aec-9474-81f6290c0832")</span><span class="sxs-lookup"><span data-stu-id="dc381-152">![Business Rule Composer&#45;DragStatus](../core/media/3617251a-a192-4aec-9474-81f6290c0832.gif "3617251a-a192-4aec-9474-81f6290c0832")</span></span>  
  
14. <span data-ttu-id="dc381-153">在 [THEN] 窗格中，按一下**\<輸入的值 >** ，然後輸入**Approved**。</span><span class="sxs-lookup"><span data-stu-id="dc381-153">In the THEN pane, click **\<Enter a value>** and then type **Approved**.</span></span>  
  
15. <span data-ttu-id="dc381-154">在原則總管] 視窗中，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="dc381-154">In the Policy Explorer window, right-click **Version 1.0 (not saved)**, and then click **Save**.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="dc381-155">註解</span><span class="sxs-lookup"><span data-stu-id="dc381-155">Comments</span></span>  
  
-   <span data-ttu-id="dc381-156">原則中可能有一或多個規則。</span><span class="sxs-lookup"><span data-stu-id="dc381-156">A policy can have one or more rules.</span></span> <span data-ttu-id="dc381-157">您會加入另一個規則**DeniedRule**，請在[逐步解說： 將規則新增至原則](../core/walkthrough-adding-a-rule-to-the-policy.md)逐步解說。</span><span class="sxs-lookup"><span data-stu-id="dc381-157">You will be adding another rule, **DeniedRule**, in the [Walkthrough: Adding a Rule to the Policy](../core/walkthrough-adding-a-rule-to-the-policy.md) walkthrough.</span></span>  
  
-   <span data-ttu-id="dc381-158">您可以修改原則，以便在原則處於「已儲存」狀態時加入更多規則、變更條件和變更動作。</span><span class="sxs-lookup"><span data-stu-id="dc381-158">You can modify the policy to add more rules, change conditions, and change actions when the policy is in the Saved state.</span></span>  
  
-   <span data-ttu-id="dc381-159">您可以設定規則的執行，藉由指定**優先順序**商務規則編輯器 」 中的規則上的屬性。</span><span class="sxs-lookup"><span data-stu-id="dc381-159">You can prioritize execution of rules by specifying the **Priority** property on rules in Business Rule Composer.</span></span> <span data-ttu-id="dc381-160">例如，如果您按一下**ApprovedRule** 原則總管 視窗中的節點，您可以看到**優先順序**屬性 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="dc381-160">For example, if you click the **ApprovedRule** node in the Policy Explorer window, you can see the **Priority** property in the Properties window.</span></span> <span data-ttu-id="dc381-161">數字愈大，規則的優先順序愈高。</span><span class="sxs-lookup"><span data-stu-id="dc381-161">The larger the number, the higher the rule priority.</span></span>  
  
-   <span data-ttu-id="dc381-162">您可以使用 XML 結構描述、資料庫或 .NET 組件做為原則的資料來源。</span><span class="sxs-lookup"><span data-stu-id="dc381-162">You can use an XML schema, a database, or a .NET assembly as a data source for the policy.</span></span> <span data-ttu-id="dc381-163">在此逐步解說中，您已使用 XML 結構描述做為資料來源。</span><span class="sxs-lookup"><span data-stu-id="dc381-163">In this walkthrough, you used an XML schema as a data source.</span></span> <span data-ttu-id="dc381-164">您應該將結構描述的 XML 文件執行個體當做事實提交至規則引擎來執行原則。</span><span class="sxs-lookup"><span data-stu-id="dc381-164">You should submit an XML document instance of the schema as a fact to the rule engine to execute the policy.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="dc381-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dc381-165">Next Steps</span></span>  
 <span data-ttu-id="dc381-166">現在您已完成此逐步解說中，執行[逐步解說： 測試原則](../core/walkthrough-testing-the-policy.md)逐步解說，它可讓您測試的逐步指示**ProcessPurchaseOrder**原則您在本逐步解說中建立。</span><span class="sxs-lookup"><span data-stu-id="dc381-166">Now that you have completed this walkthrough, perform the [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) walkthrough, which gives you step-by-step instructions for testing the **ProcessPurchaseOrder** policy you created in this walkthrough.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc381-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc381-167">See Also</span></span>  
 [<span data-ttu-id="dc381-168">關於商務規則</span><span class="sxs-lookup"><span data-stu-id="dc381-168">About Business Rules</span></span>](../core/about-business-rules.md)