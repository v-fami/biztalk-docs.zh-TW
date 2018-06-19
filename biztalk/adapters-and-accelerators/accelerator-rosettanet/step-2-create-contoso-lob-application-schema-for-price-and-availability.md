---
title: 步驟 2： 建立 Contoso LOB 應用程式的結構描述為價格與可用性專案使用 BizTalk 編輯器 |Microsoft 文件
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
ms.openlocfilehash: 441bb90c8fa0f2edb271af384e2540a741150137
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005759"
---
# <a name="step-2-creating-the-contoso-lob-application-schemas-for-the-price-and-availability-project-using-biztalk-editor"></a><span data-ttu-id="73fd2-102">步驟 2： 建立 Contoso LOB 應用程式的結構描述的價格與可用性專案中使用 [BizTalk 編輯器]</span><span class="sxs-lookup"><span data-stu-id="73fd2-102">Step 2: Creating the Contoso LOB Application Schemas for the Price and Availability Project Using BizTalk Editor</span></span>
<span data-ttu-id="73fd2-103">在此步驟中，您將產生結構描述，用來向 Contoso ERP 系統查詢特定產品的價格與可用性。</span><span class="sxs-lookup"><span data-stu-id="73fd2-103">In this step, you generate the schema to use to query the Contoso ERP system for the price and availability of a particular product.</span></span> <span data-ttu-id="73fd2-104">使用產生此結構描述[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® BizTalk Server 的 SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="73fd2-104">You generate this schema by using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® SQL Adapter for BizTalk Server.</span></span>  
  
### <a name="to-update-the-sql-stored-procedure-for-schema-generation"></a><span data-ttu-id="73fd2-105">更新 SQL 預存程序以準備產生結構描述</span><span class="sxs-lookup"><span data-stu-id="73fd2-105">To update the SQL stored procedure for schema generation</span></span>  
  
1.  <span data-ttu-id="73fd2-106">按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-106">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="73fd2-107">在 Microsoft SQL Server Management Studio 中，依序展開**資料庫**，依序展開**Contoso**，依序展開**可程式性**，然後展開**預存程序**.</span><span class="sxs-lookup"><span data-stu-id="73fd2-107">In the Microsoft SQL Server Management Studio, expand **Databases**, expand **Contoso**, expand **Programmability**, and then expand **Stored Procedures**.</span></span>  
  
3.  <span data-ttu-id="73fd2-108">以滑鼠右鍵按一下**dbo。SP_GetInventoryForProductID**，然後按一下 **修改**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-108">Right-click **dbo.SP_GetInventoryForProductID**, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="73fd2-109">在查詢視窗中，插入逗號和空格，然後輸入 "xmldata" 後面加上 "for xml auto"。</span><span class="sxs-lookup"><span data-stu-id="73fd2-109">In the query window, insert a comma, a space, and then "xmldata" immediately following "for xml auto".</span></span> <span data-ttu-id="73fd2-110">此程式碼行應如下所示：</span><span class="sxs-lookup"><span data-stu-id="73fd2-110">The line of code should be the following:</span></span>  
  
    ```  
    for xml auto, xmldata  
    ```  
  
5.  <span data-ttu-id="73fd2-111">按一下**Execute**將變更儲存到預存程序。</span><span class="sxs-lookup"><span data-stu-id="73fd2-111">Click **Execute** to save the changes to the stored procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73fd2-112">讓 Microsoft SQL Server Management Studio 保持開啟供下一個程序使用。</span><span class="sxs-lookup"><span data-stu-id="73fd2-112">Leave the Microsoft SQL Server Management Studio open for the next procedure.</span></span>  
  
### <a name="to-create-the-contoso-price-and-availability-schema"></a><span data-ttu-id="73fd2-113">若要建立 Contoso 價格與可用性結構描述</span><span class="sxs-lookup"><span data-stu-id="73fd2-113">To create the Contoso Price and Availability schema</span></span>  
  
1.  <span data-ttu-id="73fd2-114">開啟中的 Contoso 解決方案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="73fd2-114">Open the Contoso solution in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="73fd2-115">在 方案總管 中，以滑鼠右鍵按一下**ContosoPriceAndAvailability**專案，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-115">In Solution Explorer, right-click the **ContosoPriceAndAvailability** project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
3.  <span data-ttu-id="73fd2-116">在 [新增產生的項] 對話方塊使用**新增配接器中繼資料**選取左窗格中，按一下**新增配接器中繼資料**在右窗格中，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-116">In the Add Generated Iems dialog box, with **Add Adapter Metadata** selected in the left pane, click **Add Adapter Metadata** in the right pane, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="73fd2-117">在**新增配接器精靈**頁面上，選取**SQL**從已註冊的配接器，然後再按一下清單**下一步**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-117">On the **Add Adapter Wizard** page, select **SQL** from the list of registered adapters, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="73fd2-118">在**資料庫資訊**頁面上，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-118">On the **Database Information** page, click **Set**.</span></span>  
  
6.  <span data-ttu-id="73fd2-119">在 [資料連結屬性] 對話方塊中**選取或輸入伺服器名稱**方塊中，輸入**localhost**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-119">In the Data Link Properties dialog box, in the **Select or enter a server name** box, type **localhost**.</span></span> <span data-ttu-id="73fd2-120">選取**使用 Windows NT 整合式安全性**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-120">Select **Use Windows NT Integrated security**.</span></span> <span data-ttu-id="73fd2-121">如**選取的資料庫伺服器上**，選取**Contoso**資料庫從資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="73fd2-121">For **Select the database on the server**, select the **Contoso** database from the database list.</span></span> <span data-ttu-id="73fd2-122">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-122">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="73fd2-123">在**資料庫資訊**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-123">On the **Database Information** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="73fd2-124">在**結構描述資訊**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="73fd2-124">On the **Schema Information** page, do the following:</span></span>  
  
    |<span data-ttu-id="73fd2-125">使用</span><span class="sxs-lookup"><span data-stu-id="73fd2-125">Use this</span></span>|<span data-ttu-id="73fd2-126">動作</span><span class="sxs-lookup"><span data-stu-id="73fd2-126">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="73fd2-127">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="73fd2-127">**Target namespace**</span></span>|<span data-ttu-id="73fd2-128">型別**http://Contoso.com/Price**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-128">Type **http://Contoso.com/Price**.</span></span>|  
    |<span data-ttu-id="73fd2-129">**選取連接埠類型**</span><span class="sxs-lookup"><span data-stu-id="73fd2-129">**Select the port type**</span></span>|<span data-ttu-id="73fd2-130">選取**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-130">Select **Send port**.</span></span>|  
    |<span data-ttu-id="73fd2-131">**要求文件根項目名稱**</span><span class="sxs-lookup"><span data-stu-id="73fd2-131">**Request document root element name**</span></span>|<span data-ttu-id="73fd2-132">型別**rootPriceRequest**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-132">Type **rootPriceRequest**.</span></span>|  
    |<span data-ttu-id="73fd2-133">**回應文件根項目名稱**</span><span class="sxs-lookup"><span data-stu-id="73fd2-133">**Response document root element name**</span></span>|<span data-ttu-id="73fd2-134">型別**rootPriceResponse**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-134">Type **rootPriceResponse**.</span></span>|  
  
9. <span data-ttu-id="73fd2-135">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-135">Click **Next**.</span></span>  
  
10. <span data-ttu-id="73fd2-136">在**陳述式類型資訊**頁面上，選取**預存程序**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-136">On the **Statement type information** page, select **Stored Procedure**, and then click **Next**.</span></span>  
  
11. <span data-ttu-id="73fd2-137">在**陳述式資訊** 頁面上，針對**\<選取預存程序\>**，選取**SP_GetInventoryForProductID**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="73fd2-137">On the **Statement Information** page, for **\<Select a stored procedure\>**, select **SP_GetInventoryForProductID** from the drop-down list.</span></span> <span data-ttu-id="73fd2-138">按一下**產生**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-138">Click **Generate**, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="73fd2-139">在**完成 SQL 傳輸結構描述產生精靈**頁面上，按一下**完成**結構描述匯入 ContosoPriceAndAvailability BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="73fd2-139">On the **Completing the SQL Transport Schema Generation Wizard** page, click **Finish** to import the schema into the ContosoPriceAndAvailability BizTalk project.</span></span>  
  
13. <span data-ttu-id="73fd2-140">在 [方案總管] 中，以滑鼠右鍵按一下產生的結構描述 (SQLService_Price.xsd)，請按一下**重新命名**，然後輸入**ContosoPriceAndAvailability.xsd**做為結構描述的新名稱。</span><span class="sxs-lookup"><span data-stu-id="73fd2-140">In Solution Explorer, right-click the generated schema (SQLService_Price.xsd), click **Rename**, and type **ContosoPriceAndAvailability.xsd** as the new name for the schema.</span></span> <span data-ttu-id="73fd2-141">按一下 **[輸入]**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-141">Click **Enter**.</span></span>  
  
14. <span data-ttu-id="73fd2-142">在 ContosoPriceAndAvailability 結構描述的 [屬性] 視窗設定**型別名稱**屬性**ContosoPriceSchema**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-142">In the Properties window for the ContosoPriceAndAvailability schema, set the **Type Name** property to **ContosoPriceSchema**.</span></span>  
  
15. <span data-ttu-id="73fd2-143">根據預設，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會建立名為 BizTalk 協調流程**BizTalk Orchestration.odx**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-143">By default, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] creates a BizTalk orchestration named **BizTalk Orchestration.odx**.</span></span> <span data-ttu-id="73fd2-144">此協調流程，以滑鼠右鍵按一下，然後按一下 **刪除**因為您不需要此協調流程。</span><span class="sxs-lookup"><span data-stu-id="73fd2-144">Right-click this orchestration, and then click **Delete** because you do not need this orchestration.</span></span> <span data-ttu-id="73fd2-145">在 協調流程將永久刪除，指出快顯視窗，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-145">In the popup indicating that the orchestration will be deleted permanently, click **OK**.</span></span>  
  
16. <span data-ttu-id="73fd2-146">在 Microsoft SQL Server Management Studio 中，移除`xmldata`述詞，並從逗號`SP_GetInventoryForProductID`預存程序，您在上一個步驟中加入，然後按一下  **Execute**。</span><span class="sxs-lookup"><span data-stu-id="73fd2-146">In the Microsoft SQL Server Management Studio, remove the `xmldata` predicate and the comma from the `SP_GetInventoryForProductID` stored procedure that you added in the previous step, and then click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fd2-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="73fd2-147">See Also</span></span>  
 [<span data-ttu-id="73fd2-148">步驟 3：使用 BizTalk 對應工具為價格與可用性專案建立 Contoso LOB 應用程式對應</span><span class="sxs-lookup"><span data-stu-id="73fd2-148">Step 3: Creating the Contoso LOB Application Maps for the Price and Availability Project Using BizTalk Mapper</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-create-contoso-lob-application-map-for-price-and-availability-in-mapper.md)