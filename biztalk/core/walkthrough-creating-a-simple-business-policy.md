---
title: 逐步解說： 建立簡單商務原則 |Microsoft Docs
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 02d35735-dce2-4ee2-965e-dae307a125b0
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cecf7078592d322f9cc9777aeb530759c5ecf4c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023858"
---
# <a name="walkthrough-creating-a-simple-business-policy"></a><span data-ttu-id="b19f4-102">逐步解說： 建立簡單商務原則</span><span class="sxs-lookup"><span data-stu-id="b19f4-102">Walkthrough: Creating a Simple Business Policy</span></span>
<span data-ttu-id="b19f4-103">本逐步解說提供逐步程序使用 「 商務規則編輯器 」 建立一個名為的簡單商務原則**ProcessPurchaseOrder**包含名為的規則**ApprovedRule**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-103">This walkthrough provides step-by-step procedures for using the Business Rule Composer to create a simple business policy named **ProcessPurchaseOrder** containing a rule named **ApprovedRule**.</span></span> <span data-ttu-id="b19f4-104">**ApprovedRule**規則需要使用者提交 XML 文件當做事實，並設定的值**狀態**欄位中的文件**Approved**如果的值**數量**欄位是小於或等於**500**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-104">The **ApprovedRule** rule expects the user to submit an XML document as a fact, and sets the value of the **Status** field in the document to **Approved** if the value of the **Quantity** field is less than or equal to **500**.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b19f4-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="b19f4-105">Prerequisites</span></span>  
 <span data-ttu-id="b19f4-106">您必須先熟悉的商務規則架構，才能執行此逐步解說基本概念。</span><span class="sxs-lookup"><span data-stu-id="b19f4-106">You must be familiar with the basics of the Business Rules Framework to perform this walkthrough.</span></span> <span data-ttu-id="b19f4-107">如果您不熟悉 「 商務規則架構，我們建議您閱讀在 「 商務規則架構的架構概觀[商務規則引擎](../core/business-rules-engine.md)之前執行此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="b19f4-107">If you are new to the Business Rules Framework, we recommend that you read the architecture overview of the Business Rules Framework at [Business Rules Engine](../core/business-rules-engine.md) before performing this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="b19f4-108">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="b19f4-108">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="b19f4-109">此逐步解說包含兩個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="b19f4-109">This walkthrough contains two procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="b19f4-110">程序標題</span><span class="sxs-lookup"><span data-stu-id="b19f4-110">Procedure title</span></span>|<span data-ttu-id="b19f4-111">程序說明</span><span class="sxs-lookup"><span data-stu-id="b19f4-111">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="b19f4-112">建立 PO 結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="b19f4-112">To create the PO schema file</span></span>|<span data-ttu-id="b19f4-113">提供建立文件的結構描述的逐步指示**ProcessPurchaseOrder**原則會使用。</span><span class="sxs-lookup"><span data-stu-id="b19f4-113">Provides step-by-step instructions for creating the schema for the document that the **ProcessPurchaseOrder** policy uses.</span></span>|  
|<span data-ttu-id="b19f4-114">建立 ProcessPurchaseOrder 原則</span><span class="sxs-lookup"><span data-stu-id="b19f4-114">To create the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="b19f4-115">提供逐步指示，建立**ProcessPurchaseOrder**使用商務規則編輯器 」 的原則。</span><span class="sxs-lookup"><span data-stu-id="b19f4-115">Provides step-by-step instructions for creating the **ProcessPurchaseOrder** policy by using the Business Rule Composer.</span></span>|  
  
### <a name="to-create-the-po-schema-file"></a><span data-ttu-id="b19f4-116">建立 PO 結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="b19f4-116">To create the PO schema file</span></span>  
  
1.  <span data-ttu-id="b19f4-117">在 **開始**功能表中，開啟**記事本**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-117">On the **Start** menu, open **Notepad**.</span></span>  
  
2.  <span data-ttu-id="b19f4-118">在 [ **檔案** ] 功能表上，指向 [ **新增**]，然後按一下 [ **檔案**]。</span><span class="sxs-lookup"><span data-stu-id="b19f4-118">On the **File** menu, point to **New**, and then click **File**.</span></span>  
  
3.  <span data-ttu-id="b19f4-119">將下列 XML 文字複製到編輯器中：</span><span class="sxs-lookup"><span data-stu-id="b19f4-119">Copy the following XML text to the editor:</span></span>  
  
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
  
4.  <span data-ttu-id="b19f4-120">在 **檔案**功能表上，按一下**另存 TextFile1.txt 為**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-120">On the **File** menu, click **Save TextFile1.txt As**.</span></span>  
  
5.  <span data-ttu-id="b19f4-121">值變更**另存為型別**從**文字文件 (\*.txt)** 來**的所有檔案**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-121">Change the value for **Save As type** from **Text Documents(\*.txt)** to **All Files**.</span></span>  
  
6.  <span data-ttu-id="b19f4-122">型別**PO.xsd**中**檔名**文字方塊中，將目錄變更**C:\BRE-Walkthroughs**，變更的值**編碼**至**Unicode** ，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-122">Type **PO.xsd** in the **File name** text box, change the directory to **C:\BRE-Walkthroughs**, change the value of **Encoding** to **Unicode** and then click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b19f4-123">建立目錄**BRE 逐步解說**下方**c:\\** 如果它尚未存在，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-123">Create the directory **BRE-Walkthroughs** under **C:\\** if it does not exist, and then click **Save**.</span></span>  
  
7.  <span data-ttu-id="b19f4-124">關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="b19f4-124">Close Notepad.</span></span>  
  
### <a name="to-create-the-processpurchaseorder-business-policy"></a><span data-ttu-id="b19f4-125">建立 ProcessPurchaseOrder 商務原則</span><span class="sxs-lookup"><span data-stu-id="b19f4-125">To create the ProcessPurchaseOrder business policy</span></span>  
  
1. <span data-ttu-id="b19f4-126">在 **開始**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-126">On the **Start** menu, open **Business Rule Composer**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b19f4-127">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="b19f4-127">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="b19f4-128">若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-128">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b19f4-129">「 商務規則編輯器 」 會顯示**開啟規則存放區**對話方塊中的電腦上第一次開啟時。</span><span class="sxs-lookup"><span data-stu-id="b19f4-129">The Business Rule Composer displays the **Open Rule Store** dialog box when it is opened for the first time on a computer.</span></span> <span data-ttu-id="b19f4-130">如果您看到**開啟規則存放區** 對話方塊中，按一下**確定**之後驗證的 SQL server 名稱和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="b19f4-130">If you see the **Open Rule Store** dialog box, click **OK** after verifying the SQL server name and database name.</span></span>  
  
2. <span data-ttu-id="b19f4-131">在 [原則總管] 視窗中，以滑鼠右鍵按一下**原則**，然後按一下**新增新的原則**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-131">In the Policy Explorer window, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
3. <span data-ttu-id="b19f4-132">編輯原則的名稱**Policy1**至**ProcessPurchaseOrder**按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="b19f4-132">Edit the name of the policy, **Policy1**, to **ProcessPurchaseOrder** and press ENTER.</span></span> <span data-ttu-id="b19f4-133">您也可以變更在 原則名稱**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="b19f4-133">You can also change the name of the policy in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="b19f4-134">以滑鼠右鍵按一下**1.0 版**，然後按一下**AddNewRule**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-134">Right-click **Version 1.0**, and then click **AddNewRule**.</span></span>  
  
5. <span data-ttu-id="b19f4-135">編輯規則的名稱**Rule1**要**ApprovalRule**然後按 ENTER<strong>。</strong></span><span class="sxs-lookup"><span data-stu-id="b19f4-135">Edit the name of the rule from **Rule1** to **ApprovalRule** and press ENTER<strong>.</strong></span></span> <span data-ttu-id="b19f4-136">您也可以變更中規則的名稱**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="b19f4-136">You can also change the name of the rule in the **Properties** window.</span></span>  
  
6. <span data-ttu-id="b19f4-137">在 事實總管 視窗中，按一下**XML 結構描述** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b19f4-137">In the Facts Explorer window, click the **XML Schemas** tab.</span></span>  
  
7. <span data-ttu-id="b19f4-138">以滑鼠右鍵按一下**結構描述**，按一下**瀏覽**，然後選取**PO.xsd**您稍早建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="b19f4-138">Right-click **Schemas**, click **Browse**, and then select the **PO.xsd** file that you created earlier.</span></span>  
  
8. <span data-ttu-id="b19f4-139">在 [屬性] 視窗中，將變更的值**文件類型**屬性從**PO**來**RuleTest.PO**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-139">In the properties window, change the value of the **Document Type** property from **PO** to **RuleTest.PO**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b19f4-140">您將建立名為的 BizTalk 專案**RuleTest**稍後[逐步解說： 叫用原則與協調流程](../core/walkthrough-invoking-the-policy-from-an-orchestration.md)逐步解說。</span><span class="sxs-lookup"><span data-stu-id="b19f4-140">You will be creating a BizTalk project named **RuleTest** later in the [Walkthrough: Invoking the Policy from an Orchestration](../core/walkthrough-invoking-the-policy-from-an-orchestration.md) walkthrough.</span></span> <span data-ttu-id="b19f4-141">在於逐步解說中，您將會加入**PO.xsd**檔案加入專案中，建立會叫用的協調流程**ProcessPurchaseOrder**原則，以及測試原則。</span><span class="sxs-lookup"><span data-stu-id="b19f4-141">In that walkthrough, you will add the **PO.xsd** file to the project, create an orchestration that invokes the **ProcessPurchaseOrder** policy, and then test the policy.</span></span> <span data-ttu-id="b19f4-142">若要測試從協調流程的原則，您需要確定您變更**文件類型**屬性設**\<專案名稱\>。\<SchemaName\>**，即**RuleTest.PO**在此情況下。</span><span class="sxs-lookup"><span data-stu-id="b19f4-142">To test the policy from the orchestration, you need to make sure that you change the **Document Type** property to **\<Project Name\>.\<SchemaName\>**, which is **RuleTest.PO** in this case.</span></span>  
  
    <span data-ttu-id="b19f4-143">![BRE&#45;逐步解說&#45;ChangeDocType](../core/media/e9a370fd-d9b2-48f0-ad0e-85a5428a9c21.gif "e9a370fd-d9b2-48f0-ad0e-85a5428a9c21")</span><span class="sxs-lookup"><span data-stu-id="b19f4-143">![BRE&#45;Walkthrough&#45;ChangeDocType](../core/media/e9a370fd-d9b2-48f0-ad0e-85a5428a9c21.gif "e9a370fd-d9b2-48f0-ad0e-85a5428a9c21")</span></span>  
  
9. <span data-ttu-id="b19f4-144">在 [事實總管] 視窗中，依序展開**PurchaseOrder**，然後展開**項目**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-144">In the Facts Explorer window, expand **PurchaseOrder**, and then expand **Item**.</span></span>  
  
10. <span data-ttu-id="b19f4-145">在 [IF] 窗格 （上方） 右邊，以滑鼠右鍵按一下**條件**，按一下**述詞**，然後按一下**小於或等於**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-145">In the IF pane (top) on the right, right-click **Conditions**, click **Predicates**, and then click **LessThanEqual**.</span></span>  
  
     <span data-ttu-id="b19f4-146">![商務規則編輯器 」&#45;小於或等於](../core/media/1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7.gif "1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7")</span><span class="sxs-lookup"><span data-stu-id="b19f4-146">![Business Rule Composer &#45; Less Than or Equal](../core/media/1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7.gif "1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7")</span></span>  
  
11. <span data-ttu-id="b19f4-147">拖曳**Quantity**節點從 事實總管 視窗，來**引數 1** IF 窗格中。</span><span class="sxs-lookup"><span data-stu-id="b19f4-147">Drag the **Quantity** node from the Facts Explorer window to **argument1** in the IF pane.</span></span>  
  
     <span data-ttu-id="b19f4-148">![商務規則編輯器 」 &#45; DragQuantity](../core/media/4742eca6-4a8a-401d-8989-cab4e8025fb3.gif "4742eca6-4a8a-401d-8989-cab4e8025fb3")</span><span class="sxs-lookup"><span data-stu-id="b19f4-148">![Business Rule Composer &#45; DragQuantity](../core/media/4742eca6-4a8a-401d-8989-cab4e8025fb3.gif "4742eca6-4a8a-401d-8989-cab4e8025fb3")</span></span>  
  
     <span data-ttu-id="b19f4-149">![商務規則編輯器 」&#45;UseQuantity](../core/media/ee4f61b1-0f15-4329-b0b5-9badd21dcd61.gif "ee4f61b1-0f15-4329-b0b5-9badd21dcd61")</span><span class="sxs-lookup"><span data-stu-id="b19f4-149">![Business Rule Composer&#45;UseQuantity](../core/media/ee4f61b1-0f15-4329-b0b5-9badd21dcd61.gif "ee4f61b1-0f15-4329-b0b5-9badd21dcd61")</span></span>  
  
12. <span data-ttu-id="b19f4-150">在 [IF] 窗格中，按一下**argument2**，型別`500`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="b19f4-150">In the IF pane, click **argument2**, type `500`, and then press ENTER.</span></span>  
  
13. <span data-ttu-id="b19f4-151">拖曳**狀態**節點從 [事實總管] 視窗以商務規則編輯器的右下方的 [THEN] 窗格。</span><span class="sxs-lookup"><span data-stu-id="b19f4-151">Drag the **Status** node from the Facts Explorer window to the THEN pane at the bottom-right side of Business Rule Composer.</span></span>  
  
     <span data-ttu-id="b19f4-152">![商務規則編輯器 」&#45;DragStatus](../core/media/3617251a-a192-4aec-9474-81f6290c0832.gif "3617251a-a192-4aec-9474-81f6290c0832")</span><span class="sxs-lookup"><span data-stu-id="b19f4-152">![Business Rule Composer&#45;DragStatus](../core/media/3617251a-a192-4aec-9474-81f6290c0832.gif "3617251a-a192-4aec-9474-81f6290c0832")</span></span>  
  
14. <span data-ttu-id="b19f4-153">在 [THEN] 窗格中，按一下**\<輸入值\>** ，然後輸入**Approved**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-153">In the THEN pane, click **\<Enter a value\>** and then type **Approved**.</span></span>  
  
15. <span data-ttu-id="b19f4-154">在 [原則總管] 視窗中，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="b19f4-154">In the Policy Explorer window, right-click **Version 1.0 (not saved)**, and then click **Save**.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="b19f4-155">註解</span><span class="sxs-lookup"><span data-stu-id="b19f4-155">Comments</span></span>  
  
-   <span data-ttu-id="b19f4-156">原則中可能有一或多個規則。</span><span class="sxs-lookup"><span data-stu-id="b19f4-156">A policy can have one or more rules.</span></span> <span data-ttu-id="b19f4-157">您將新增另一個規則**DeniedRule**，請在[逐步解說： 將規則新增至原則](../core/walkthrough-adding-a-rule-to-the-policy.md)逐步解說。</span><span class="sxs-lookup"><span data-stu-id="b19f4-157">You will be adding another rule, **DeniedRule**, in the [Walkthrough: Adding a Rule to the Policy](../core/walkthrough-adding-a-rule-to-the-policy.md) walkthrough.</span></span>  
  
-   <span data-ttu-id="b19f4-158">您可以修改原則，以便在原則處於「已儲存」狀態時加入更多規則、變更條件和變更動作。</span><span class="sxs-lookup"><span data-stu-id="b19f4-158">You can modify the policy to add more rules, change conditions, and change actions when the policy is in the Saved state.</span></span>  
  
-   <span data-ttu-id="b19f4-159">您可以藉由指定排定優先順序的規則執行**優先順序**商務規則編輯器 」 中的規則上的屬性。</span><span class="sxs-lookup"><span data-stu-id="b19f4-159">You can prioritize execution of rules by specifying the **Priority** property on rules in Business Rule Composer.</span></span> <span data-ttu-id="b19f4-160">例如，如果您按一下**ApprovedRule** 原則總管 視窗中的節點，您可以看到**優先順序**屬性 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="b19f4-160">For example, if you click the **ApprovedRule** node in the Policy Explorer window, you can see the **Priority** property in the Properties window.</span></span> <span data-ttu-id="b19f4-161">數字愈大，規則的優先順序愈高。</span><span class="sxs-lookup"><span data-stu-id="b19f4-161">The larger the number, the higher the rule priority.</span></span>  
  
-   <span data-ttu-id="b19f4-162">您可以使用 XML 結構描述、資料庫或 .NET 組件做為原則的資料來源。</span><span class="sxs-lookup"><span data-stu-id="b19f4-162">You can use an XML schema, a database, or a .NET assembly as a data source for the policy.</span></span> <span data-ttu-id="b19f4-163">在此逐步解說中，您已使用 XML 結構描述做為資料來源。</span><span class="sxs-lookup"><span data-stu-id="b19f4-163">In this walkthrough, you used an XML schema as a data source.</span></span> <span data-ttu-id="b19f4-164">您應該將結構描述的 XML 文件執行個體當做事實提交至規則引擎來執行原則。</span><span class="sxs-lookup"><span data-stu-id="b19f4-164">You should submit an XML document instance of the schema as a fact to the rule engine to execute the policy.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b19f4-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b19f4-165">Next Steps</span></span>  
 <span data-ttu-id="b19f4-166">既然您已完成本逐步解說中，執行[逐步解說： 測試原則](../core/walkthrough-testing-the-policy.md)逐步解說，它可讓您測試的逐步指示**ProcessPurchaseOrder**原則您在本逐步解說中建立。</span><span class="sxs-lookup"><span data-stu-id="b19f4-166">Now that you have completed this walkthrough, perform the [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) walkthrough, which gives you step-by-step instructions for testing the **ProcessPurchaseOrder** policy you created in this walkthrough.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19f4-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b19f4-167">See Also</span></span>  
 [<span data-ttu-id="b19f4-168">關於商務規則</span><span class="sxs-lookup"><span data-stu-id="b19f4-168">About Business Rules</span></span>](../core/about-business-rules.md)