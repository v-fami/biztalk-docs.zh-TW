---
title: 步驟 2： 在使用 「 BizTalk 編輯器 」 的價格與可用性專案建立 Contoso LOB 應用程式結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating LOB schemas
ms.assetid: 70e26dc9-4299-4d30-8f8b-5cc3469a2025
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f899a6614ea5d5d28c555be1b39e72b5880fe3ae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999327"
---
# <a name="step-2-creating-the-contoso-lob-application-schemas-for-the-price-and-availability-project-using-biztalk-editor"></a><span data-ttu-id="35d27-102">步驟 2： 建立 Contoso LOB 應用程式結構描述為價格與可用性專案使用 「 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="35d27-102">Step 2: Creating the Contoso LOB Application Schemas for the Price and Availability Project Using BizTalk Editor</span></span>
<span data-ttu-id="35d27-103">在此步驟中，您將產生結構描述，用來向 Contoso ERP 系統查詢特定產品的價格與可用性。</span><span class="sxs-lookup"><span data-stu-id="35d27-103">In this step, you generate the schema to use to query the Contoso ERP system for the price and availability of a particular product.</span></span> <span data-ttu-id="35d27-104">您可以使用 BizTalk server 的 Microsoft® SQL 配接器，以產生此結構描述。</span><span class="sxs-lookup"><span data-stu-id="35d27-104">You generate this schema by using the Microsoft® SQL Adapter for BizTalk Server.</span></span>  

### <a name="to-update-the-sql-stored-procedure-for-schema-generation"></a><span data-ttu-id="35d27-105">更新 SQL 預存程序以準備產生結構描述</span><span class="sxs-lookup"><span data-stu-id="35d27-105">To update the SQL stored procedure for schema generation</span></span>  

1.  <span data-ttu-id="35d27-106">按一下 **開始**，指向**所有程式**，指向**Microsoft SQL Server 2008 R2**，然後按一下**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="35d27-106">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  

2.  <span data-ttu-id="35d27-107">在 Microsoft SQL Server Management Studio 中，展開**資料庫**，展開**Contoso**，展開**可程式性**，然後展開**預存程序**.</span><span class="sxs-lookup"><span data-stu-id="35d27-107">In the Microsoft SQL Server Management Studio, expand **Databases**, expand **Contoso**, expand **Programmability**, and then expand **Stored Procedures**.</span></span>  

3.  <span data-ttu-id="35d27-108">以滑鼠右鍵按一下**dbo。SP_GetInventoryForProductID**，然後按一下**修改**。</span><span class="sxs-lookup"><span data-stu-id="35d27-108">Right-click **dbo.SP_GetInventoryForProductID**, and then click **Modify**.</span></span>  

4.  <span data-ttu-id="35d27-109">在查詢視窗中，插入逗號和空格，然後輸入 "xmldata" 後面加上 "for xml auto"。</span><span class="sxs-lookup"><span data-stu-id="35d27-109">In the query window, insert a comma, a space, and then "xmldata" immediately following "for xml auto".</span></span> <span data-ttu-id="35d27-110">此程式碼行應如下所示：</span><span class="sxs-lookup"><span data-stu-id="35d27-110">The line of code should be the following:</span></span>  

    ```  
    for xml auto, xmldata  
    ```  

5.  <span data-ttu-id="35d27-111">按一下  **Execute**預存程序中儲存的變更。</span><span class="sxs-lookup"><span data-stu-id="35d27-111">Click **Execute** to save the changes to the stored procedure.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="35d27-112">讓 Microsoft SQL Server Management Studio 保持開啟供下一個程序使用。</span><span class="sxs-lookup"><span data-stu-id="35d27-112">Leave the Microsoft SQL Server Management Studio open for the next procedure.</span></span>  

### <a name="to-create-the-contoso-price-and-availability-schema"></a><span data-ttu-id="35d27-113">若要建立 Contoso 價格與可用性結構描述</span><span class="sxs-lookup"><span data-stu-id="35d27-113">To create the Contoso Price and Availability schema</span></span>  

1. <span data-ttu-id="35d27-114">開啟中的 Contoso 解決方案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="35d27-114">Open the Contoso solution in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  

2. <span data-ttu-id="35d27-115">在 [方案總管] 中，以滑鼠右鍵按一下**ContosoPriceAndAvailability**專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="35d27-115">In Solution Explorer, right-click the **ContosoPriceAndAvailability** project, point to **Add**, and then click **Add Generated Items**.</span></span>  

3. <span data-ttu-id="35d27-116">在 [新增產生的項] 對話方塊中，使用**新增的配接器中繼資料**選取左窗格中，按一下**新增配接器中繼資料**在右窗格中，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="35d27-116">In the Add Generated Iems dialog box, with **Add Adapter Metadata** selected in the left pane, click **Add Adapter Metadata** in the right pane, and then click **Add**.</span></span>  

4. <span data-ttu-id="35d27-117">在 [**新增配接器精靈**頁面上，選取**SQL**從清單中已註冊的配接器，然後再按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="35d27-117">On the **Add Adapter Wizard** page, select **SQL** from the list of registered adapters, and then click **Next**.</span></span>  

5. <span data-ttu-id="35d27-118">在 **資料庫資訊**頁面上，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="35d27-118">On the **Database Information** page, click **Set**.</span></span>  

6. <span data-ttu-id="35d27-119">在 [資料連結屬性] 對話方塊中，在**選取或輸入伺服器名稱**方塊中，輸入**localhost**。</span><span class="sxs-lookup"><span data-stu-id="35d27-119">In the Data Link Properties dialog box, in the **Select or enter a server name** box, type **localhost**.</span></span> <span data-ttu-id="35d27-120">選取 **使用 Windows NT 整合式安全性**。</span><span class="sxs-lookup"><span data-stu-id="35d27-120">Select **Use Windows NT Integrated security**.</span></span> <span data-ttu-id="35d27-121">針對**選取的伺服器上的資料庫**，選取**Contoso**資料庫從資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="35d27-121">For **Select the database on the server**, select the **Contoso** database from the database list.</span></span> <span data-ttu-id="35d27-122">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="35d27-122">Click **OK**.</span></span>  

7. <span data-ttu-id="35d27-123">在 [**資料庫資訊**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="35d27-123">On the **Database Information** page, click **Next**.</span></span>  

8. <span data-ttu-id="35d27-124">在 **結構描述資訊**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="35d27-124">On the **Schema Information** page, do the following:</span></span>  


   |                <span data-ttu-id="35d27-125">使用</span><span class="sxs-lookup"><span data-stu-id="35d27-125">Use this</span></span>                 |              <span data-ttu-id="35d27-126">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="35d27-126">To do this</span></span>              |
   |-----------------------------------------|--------------------------------------|
   |          <span data-ttu-id="35d27-127">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="35d27-127">**Target namespace**</span></span>           | <span data-ttu-id="35d27-128">型別**<http://Contoso.com/Price>**。</span><span class="sxs-lookup"><span data-stu-id="35d27-128">Type **<http://Contoso.com/Price>**.</span></span> |
   |        <span data-ttu-id="35d27-129">**選取連接埠類型**</span><span class="sxs-lookup"><span data-stu-id="35d27-129">**Select the port type**</span></span>         |        <span data-ttu-id="35d27-130">選取 **傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="35d27-130">Select **Send port**.</span></span>         |
   | <span data-ttu-id="35d27-131">**要求文件根元素名稱**</span><span class="sxs-lookup"><span data-stu-id="35d27-131">**Request document root element name**</span></span>  |      <span data-ttu-id="35d27-132">型別**rootPriceRequest**。</span><span class="sxs-lookup"><span data-stu-id="35d27-132">Type **rootPriceRequest**.</span></span>      |
   | <span data-ttu-id="35d27-133">**回應文件根元素名稱**</span><span class="sxs-lookup"><span data-stu-id="35d27-133">**Response document root element name**</span></span> |     <span data-ttu-id="35d27-134">型別**rootPriceResponse**。</span><span class="sxs-lookup"><span data-stu-id="35d27-134">Type **rootPriceResponse**.</span></span>      |


9. <span data-ttu-id="35d27-135">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="35d27-135">Click **Next**.</span></span>  

10. <span data-ttu-id="35d27-136">在 [**陳述式類型資訊**頁面上，選取**預存程序**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="35d27-136">On the **Statement type information** page, select **Stored Procedure**, and then click **Next**.</span></span>  

11. <span data-ttu-id="35d27-137">在上**陳述式資訊**頁面上，如**\<選取預存程序\>**，選取**SP_GetInventoryForProductID**從下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="35d27-137">On the **Statement Information** page, for **\<Select a stored procedure\>**, select **SP_GetInventoryForProductID** from the drop-down list.</span></span> <span data-ttu-id="35d27-138">按一下 [ **Generate**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="35d27-138">Click **Generate**, and then click **Next**.</span></span>  

12. <span data-ttu-id="35d27-139">在 **完成 SQL 傳輸結構描述產生精靈**頁面上，按一下**完成**結構描述匯入 ContosoPriceAndAvailability BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="35d27-139">On the **Completing the SQL Transport Schema Generation Wizard** page, click **Finish** to import the schema into the ContosoPriceAndAvailability BizTalk project.</span></span>  

13. <span data-ttu-id="35d27-140">在 [方案總管] 中，以滑鼠右鍵按一下所產生的結構描述 (SQLService_Price.xsd)，請按一下**重新命名**，然後輸入**ContosoPriceAndAvailability.xsd**做為結構描述的新名稱。</span><span class="sxs-lookup"><span data-stu-id="35d27-140">In Solution Explorer, right-click the generated schema (SQLService_Price.xsd), click **Rename**, and type **ContosoPriceAndAvailability.xsd** as the new name for the schema.</span></span> <span data-ttu-id="35d27-141">按一下 **[輸入]**。</span><span class="sxs-lookup"><span data-stu-id="35d27-141">Click **Enter**.</span></span>  

14. <span data-ttu-id="35d27-142">在 ContosoPriceAndAvailability 結構描述的 屬性 視窗中，設定**型別名稱**屬性設**ContosoPriceSchema**。</span><span class="sxs-lookup"><span data-stu-id="35d27-142">In the Properties window for the ContosoPriceAndAvailability schema, set the **Type Name** property to **ContosoPriceSchema**.</span></span>  

15. <span data-ttu-id="35d27-143">根據預設，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]建立名為 BizTalk 協調流程**BizTalk Orchestration.odx**。</span><span class="sxs-lookup"><span data-stu-id="35d27-143">By default, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] creates a BizTalk orchestration named **BizTalk Orchestration.odx**.</span></span> <span data-ttu-id="35d27-144">此協調流程，以滑鼠右鍵按一下，然後按一下**刪除**因為您不需要此協調流程。</span><span class="sxs-lookup"><span data-stu-id="35d27-144">Right-click this orchestration, and then click **Delete** because you do not need this orchestration.</span></span> <span data-ttu-id="35d27-145">在協調流程將會永久刪除，指出快顯視窗，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="35d27-145">In the popup indicating that the orchestration will be deleted permanently, click **OK**.</span></span>  

16. <span data-ttu-id="35d27-146">在 Microsoft SQL Server Management Studio 中，移除`xmldata`述詞，並從逗號`SP_GetInventoryForProductID`預存程序，您在上一個步驟中，新增，然後按一下**Execute**。</span><span class="sxs-lookup"><span data-stu-id="35d27-146">In the Microsoft SQL Server Management Studio, remove the `xmldata` predicate and the comma from the `SP_GetInventoryForProductID` stored procedure that you added in the previous step, and then click **Execute**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="35d27-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35d27-147">See Also</span></span>  
 [<span data-ttu-id="35d27-148">步驟 3：使用 BizTalk 對應工具為價格與可用性專案建立 Contoso LOB 應用程式對應</span><span class="sxs-lookup"><span data-stu-id="35d27-148">Step 3: Creating the Contoso LOB Application Maps for the Price and Availability Project Using BizTalk Mapper</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-create-contoso-lob-application-map-for-price-and-availability-in-mapper.md)