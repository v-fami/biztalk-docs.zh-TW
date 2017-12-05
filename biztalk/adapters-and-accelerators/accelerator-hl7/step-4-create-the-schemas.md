---
title: "步驟 4： 建立結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, schemas
- creating, schemas
- schemas, creating
ms.assetid: 81b1f538-9743-433a-87f9-a423dcb868c8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ce9ea850632327e257909e1c7d4b60117865e46
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-create-the-schemas"></a><span data-ttu-id="c8291-102">步驟 4： 建立結構描述</span><span class="sxs-lookup"><span data-stu-id="c8291-102">Step 4: Create the Schemas</span></span>
<span data-ttu-id="c8291-103">在此步驟中，您會建立新的專案 (**BTAHL7 專案**)，其中包含這個專案的成品： 結構描述、 對應和協調流程。</span><span class="sxs-lookup"><span data-stu-id="c8291-103">In this step, you create a new project (**BTAHL7 Project**) that contains the artifacts for this project: the schemas, map, and orchestration.</span></span> <span data-ttu-id="c8291-104">然後，您建立結構描述 (**Doorbell.xsd**) 內送的 XML 編碼訊息，然後選取現有的結構描述 (**ADT_A04_22_GLO_DEF.xsd**) 傳出 HL7 編碼訊息。</span><span class="sxs-lookup"><span data-stu-id="c8291-104">You then create a schema (**Doorbell.xsd**) for the incoming XML-encoded message, and select an existing schema (**ADT_A04_22_GLO_DEF.xsd**) for the outgoing HL7-encoded message.</span></span> <span data-ttu-id="c8291-105">您可以使用這些結構描述來定義您在協調流程內交換訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="c8291-105">You use these schemas to define the structure of the messages that you exchange within the orchestration.</span></span>  
  
### <a name="to-create-the-schemas"></a><span data-ttu-id="c8291-106">若要建立結構描述</span><span class="sxs-lookup"><span data-stu-id="c8291-106">To create the schemas</span></span>  
  
1.  <span data-ttu-id="c8291-107">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="c8291-107">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="c8291-108">在 [新增專案] 對話方塊中，展開**BizTalk 專案**資料夾，然後再按一下**BTAHL7Projects**資料夾。</span><span class="sxs-lookup"><span data-stu-id="c8291-108">In the New Project dialog box, expand the **BizTalk Projects** folder, and then click the **BTAHL7Projects** folder.</span></span>  
  
3.  <span data-ttu-id="c8291-109">在**範本**] 窗格中，按一下 [**空白 BTAHL7 專案**。</span><span class="sxs-lookup"><span data-stu-id="c8291-109">In the **Templates** pane, click **Empty BTAHL7 Project**.</span></span>  
  
4.  <span data-ttu-id="c8291-110">在**名稱**欄位中，輸入**BTAHL7 專案**做為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="c8291-110">In the **Name** field, type **BTAHL7 Project** as the project name.</span></span>  
  
5.  <span data-ttu-id="c8291-111">在**方案**欄位中，選取**將加入至方案**。</span><span class="sxs-lookup"><span data-stu-id="c8291-111">In the **Solution** field, select **Add to Solution**.</span></span>  
  
6.  <span data-ttu-id="c8291-112">在**位置**欄位中，確認  **\<*磁碟機*\>: \Tutorial\BTAHL7V22Common** 是的路徑。</span><span class="sxs-lookup"><span data-stu-id="c8291-112">In the **Location** field, verify that **\<*drive*\>:\Tutorial\BTAHL7V22Common** is the path.</span></span>  
  
7.  <span data-ttu-id="c8291-113">按一下**確定**開啟新的專案。</span><span class="sxs-lookup"><span data-stu-id="c8291-113">Click **OK** to open the new project.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="c8291-114">將新的專案加入至方案總管 中。</span><span class="sxs-lookup"><span data-stu-id="c8291-114"> adds a new project to Solution Explorer.</span></span> <span data-ttu-id="c8291-115">它也會將專案資料夾，並建立檔案中的\<*磁碟機*\>: \Tutorial\\**BTAHL7V22Common**專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="c8291-115">It also adds the project folder and creates files in the \<*drive*\>:\Tutorial\\**BTAHL7V22Common** Project folder.</span></span>  
  
8.  <span data-ttu-id="c8291-116">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7 專案**專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="c8291-116">In Solution Explorer, right-click the **BTAHL7 Project** project, point to **Add**, and then click **New Item**.</span></span>  
  
9. <span data-ttu-id="c8291-117">在加入新項目-BTAHL7 專案對話方塊中，於**類別** 窗格中，按一下 **結構描述檔案**，然後在**範本** 窗格中，按一下**結構描述**.</span><span class="sxs-lookup"><span data-stu-id="c8291-117">In the Add New Item - BTAHL7 Project dialog box, in the **Categories** pane, click **Schema Files**, and in the **Templates** pane, click **Schema**.</span></span>  
  
10. <span data-ttu-id="c8291-118">在**名稱**欄位中，輸入**Doorbell.xsd**命名結構描述。</span><span class="sxs-lookup"><span data-stu-id="c8291-118">In the **Name** field, type **Doorbell.xsd** to name the schema.</span></span>  
  
11. <span data-ttu-id="c8291-119">按一下**新增**在 「 BizTalk 編輯器 」 中開啟空白的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c8291-119">Click **Add** to open the blank schema in BizTalk Editor.</span></span>  
  
12. <span data-ttu-id="c8291-120">在**\<結構描述\>**樹狀目錄中，以滑鼠右鍵按一下**根**節點，然後再按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="c8291-120">In the **\<Schema\>** tree, right-click the **Root** node, and then click **Rename**.</span></span>  
  
13. <span data-ttu-id="c8291-121">型別**DoorbellRoot**作為新的名稱，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c8291-121">Type **DoorbellRoot** as the new name, and then press **Enter**.</span></span>  
  
14. <span data-ttu-id="c8291-122">以滑鼠右鍵按一下**DoorbellRoot**節點，指向**插入結構描述節點**，然後按一下 **子欄位項目**新增下列欄位 （每個欄位重複此步驟項目）：</span><span class="sxs-lookup"><span data-stu-id="c8291-122">Right-click the **DoorbellRoot** node, point to **Insert Schema Node**, and then click **Child Field Element** to add the following fields (repeat this step for each field element):</span></span>  
  
    -   <span data-ttu-id="c8291-123">**名字**</span><span class="sxs-lookup"><span data-stu-id="c8291-123">**FirstName**</span></span>  
  
    -   <span data-ttu-id="c8291-124">**MiddleName**</span><span class="sxs-lookup"><span data-stu-id="c8291-124">**MiddleName**</span></span>  
  
    -   <span data-ttu-id="c8291-125">**LastName**</span><span class="sxs-lookup"><span data-stu-id="c8291-125">**LastName**</span></span>  
  
    -   <span data-ttu-id="c8291-126">**SSN**</span><span class="sxs-lookup"><span data-stu-id="c8291-126">**SSN**</span></span>  
  
15. <span data-ttu-id="c8291-127">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7 專案**，指向 **新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="c8291-127">In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.</span></span>  
  
16. <span data-ttu-id="c8291-128">在加入新項目-BTAHL7 專案對話方塊中，於**類別** 窗格中，按一下  **BTAHL7 結構描述**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="c8291-128">In the Add New Item - BTAHL7 Project dialog box, in the **Categories** pane, click **BTAHL7 Schemas**, and then click **Add**.</span></span>  
  
17. <span data-ttu-id="c8291-129">HL7 結構描述選取器 對話方塊中，在中**訊息類別**方塊中，選取**V2.X**，然後在**結構描述的詳細資料** 窗格中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c8291-129">In the HL7 Schema Selector dialog box, in the **Message Class** box, select **V2.X**, and in the **Schema Details** pane, do the following:</span></span>  
  
    |<span data-ttu-id="c8291-130">使用</span><span class="sxs-lookup"><span data-stu-id="c8291-130">Use this</span></span>|<span data-ttu-id="c8291-131">動作</span><span class="sxs-lookup"><span data-stu-id="c8291-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c8291-132">**版本**</span><span class="sxs-lookup"><span data-stu-id="c8291-132">**Version**</span></span>|<span data-ttu-id="c8291-133">選取 HL7 訊息的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c8291-133">Select the version number of the HL7 message.</span></span> <span data-ttu-id="c8291-134">在此教學課程中，使用**2.2**。</span><span class="sxs-lookup"><span data-stu-id="c8291-134">In this tutorial, use **2.2**.</span></span>|  
    |<span data-ttu-id="c8291-135">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="c8291-135">**Message Type**</span></span>|<span data-ttu-id="c8291-136">選取 HL7 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="c8291-136">Select the type of HL7 message.</span></span> <span data-ttu-id="c8291-137">在此教學課程中，使用**ADT**。</span><span class="sxs-lookup"><span data-stu-id="c8291-137">In this tutorial, use **ADT**.</span></span>|  
    |<span data-ttu-id="c8291-138">**觸發程序事件**</span><span class="sxs-lookup"><span data-stu-id="c8291-138">**Trigger Event**</span></span>|<span data-ttu-id="c8291-139">選取 HL7 訊息的觸發程序事件值。</span><span class="sxs-lookup"><span data-stu-id="c8291-139">Select the Trigger Event value for the HL7 message.</span></span> <span data-ttu-id="c8291-140">在此教學課程中，使用**A04**。</span><span class="sxs-lookup"><span data-stu-id="c8291-140">In this tutorial, use **A04**.</span></span>|  
  
18. <span data-ttu-id="c8291-141">按一下**完成**ADT_A04_22_GLO_DEF.xsd （註冊病患） 結構描述新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="c8291-141">Click **Finish** to add the ADT_A04_22_GLO_DEF.xsd (Register Patient) schema to your project.</span></span> <span data-ttu-id="c8291-142">關閉 [HL7 結構描述選取器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c8291-142">Close the HL7 Schema Selector dialog box.</span></span>  
  
19. <span data-ttu-id="c8291-143">在 方案總管下**BTAHL7 專案**，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="c8291-143">In Solution Explorer, under **BTAHL7 Project**, right-click **References** and then click **Add Reference**.</span></span>  
  
20. <span data-ttu-id="c8291-144">在 加入參考 對話方塊上**專案**索引標籤上，選取**BTAHL7V22Common**專案中，按一下 **新增**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c8291-144">In the Add Reference dialog box, on the **Projects** tab, select the **BTAHL7V22Common** project, click **Add**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c8291-145">這樣會加入至原始專案的參考，讓[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]正確辨識 HL7 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c8291-145">This adds a reference to the original project so that [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] recognizes the HL7 schemas correctly.</span></span>  
  
21. <span data-ttu-id="c8291-146">在 方案總管下**BTAHL7 專案**，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="c8291-146">In Solution Explorer, under **BTAHL7 Project**, right-click **References** and then click **Add Reference**.</span></span>  
  
22. <span data-ttu-id="c8291-147">在 加入參考 對話方塊中，按一下**瀏覽** 索引標籤。在**查詢**方塊中，移至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端教學課程\Tutorial_BTAHL7Drop\Bin。</span><span class="sxs-lookup"><span data-stu-id="c8291-147">In the Add Reference dialog box, click the **Browse** tab. In the **Look In** box, move to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop\Bin.</span></span> <span data-ttu-id="c8291-148">按一下**Microsoft.Solutions.BTAHL7.HL7Schemas.dll**，按一下 **新增**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c8291-148">Click **Microsoft.Solutions.BTAHL7.HL7Schemas.dll**, click **Add**, and then click **OK**.</span></span>  
  
 <span data-ttu-id="c8291-149">若要繼續[步驟 5： 升級結構描述屬性](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c8291-149">Proceed to [Step 5: Promote Schema Properties](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8291-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8291-150">See Also</span></span>  
 [<span data-ttu-id="c8291-151">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="c8291-151">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)