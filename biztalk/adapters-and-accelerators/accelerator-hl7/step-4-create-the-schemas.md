---
title: 步驟 4： 建立結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, schemas
- creating, schemas
- schemas, creating
ms.assetid: 81b1f538-9743-433a-87f9-a423dcb868c8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 914efbfe8632bb727724a5115f6423b9abb8f54f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000935"
---
# <a name="step-4-create-the-schemas"></a><span data-ttu-id="b9c1a-102">步驟 4： 建立結構描述</span><span class="sxs-lookup"><span data-stu-id="b9c1a-102">Step 4: Create the Schemas</span></span>
<span data-ttu-id="b9c1a-103">在此步驟中，您會建立新的專案 (**BTAHL7 專案**)，其中包含此專案的成品： 結構描述、 對應和協調流程。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-103">In this step, you create a new project (**BTAHL7 Project**) that contains the artifacts for this project: the schemas, map, and orchestration.</span></span> <span data-ttu-id="b9c1a-104">接著，您建立結構描述 (**Doorbell.xsd**) 內送的 XML 編碼訊息，然後選取現有的結構描述 (**ADT_A04_22_GLO_DEF.xsd**) HL7 編碼的外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-104">You then create a schema (**Doorbell.xsd**) for the incoming XML-encoded message, and select an existing schema (**ADT_A04_22_GLO_DEF.xsd**) for the outgoing HL7-encoded message.</span></span> <span data-ttu-id="b9c1a-105">您可以使用這些結構描述來定義您在協調流程內交換訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-105">You use these schemas to define the structure of the messages that you exchange within the orchestration.</span></span>  

### <a name="to-create-the-schemas"></a><span data-ttu-id="b9c1a-106">若要建立結構描述</span><span class="sxs-lookup"><span data-stu-id="b9c1a-106">To create the schemas</span></span>  

1. <span data-ttu-id="b9c1a-107">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-107">On the **File** menu, point to **New**, and then click **Project**.</span></span>  

2. <span data-ttu-id="b9c1a-108">在 [新增專案] 對話方塊中，展開**BizTalk 專案**資料夾，然後再按一下**BTAHL7Projects**資料夾。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-108">In the New Project dialog box, expand the **BizTalk Projects** folder, and then click the **BTAHL7Projects** folder.</span></span>  

3. <span data-ttu-id="b9c1a-109">在 **範本**窗格中，按一下**空白 BTAHL7 專案**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-109">In the **Templates** pane, click **Empty BTAHL7 Project**.</span></span>  

4. <span data-ttu-id="b9c1a-110">在 **名稱**欄位中，輸入**BTAHL7 專案**做為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-110">In the **Name** field, type **BTAHL7 Project** as the project name.</span></span>  

5. <span data-ttu-id="b9c1a-111">在 **解決方案**欄位中，選取**加入至方案**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-111">In the **Solution** field, select **Add to Solution**.</span></span>  

6. <span data-ttu-id="b9c1a-112">在 **位置**欄位中，確認 **\<*磁碟機*\>: \Tutorial\BTAHL7V22Common**是路徑。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-112">In the **Location** field, verify that **\<*drive*\>:\Tutorial\BTAHL7V22Common** is the path.</span></span>  

7. <span data-ttu-id="b9c1a-113">按一下 **確定**開啟新的專案。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-113">Click **OK** to open the new project.</span></span>  

   > [!NOTE]
   >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="b9c1a-114"> 將新的專案加入至方案總管 中。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-114"> adds a new project to Solution Explorer.</span></span> <span data-ttu-id="b9c1a-115">它也會將專案資料夾，並建立中\<*磁碟機*\>: \Tutorial\\**BTAHL7V22Common**專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-115">It also adds the project folder and creates files in the \<*drive*\>:\Tutorial\\**BTAHL7V22Common** Project folder.</span></span>  

8. <span data-ttu-id="b9c1a-116">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-116">In Solution Explorer, right-click the **BTAHL7 Project** project, point to **Add**, and then click **New Item**.</span></span>  

9. <span data-ttu-id="b9c1a-117">在加入新項目-BTAHL7 專案對話方塊中，於**分類** 窗格中，按一下**結構描述檔案**，然後在**範本**窗格中，按一下**結構描述**.</span><span class="sxs-lookup"><span data-stu-id="b9c1a-117">In the Add New Item - BTAHL7 Project dialog box, in the **Categories** pane, click **Schema Files**, and in the **Templates** pane, click **Schema**.</span></span>  

10. <span data-ttu-id="b9c1a-118">在 **名稱**欄位中，輸入**Doorbell.xsd**命名結構描述。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-118">In the **Name** field, type **Doorbell.xsd** to name the schema.</span></span>  

11. <span data-ttu-id="b9c1a-119">按一下 **新增**在 「 BizTalk 編輯器 」 中開啟空白的結構描述。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-119">Click **Add** to open the blank schema in BizTalk Editor.</span></span>  

12. <span data-ttu-id="b9c1a-120">在  **\<結構描述\>** 樹狀結構中，以滑鼠右鍵按一下**根**節點，然後再按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-120">In the **\<Schema\>** tree, right-click the **Root** node, and then click **Rename**.</span></span>  

13. <span data-ttu-id="b9c1a-121">型別**DoorbellRoot**作為新的名稱，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-121">Type **DoorbellRoot** as the new name, and then press **Enter**.</span></span>  

14. <span data-ttu-id="b9c1a-122">以滑鼠右鍵按一下**DoorbellRoot**節點，指向**插入結構描述節點**，然後按一下**子欄位項目**加入 （每個欄位重複此步驟中的下列欄位項目）：</span><span class="sxs-lookup"><span data-stu-id="b9c1a-122">Right-click the **DoorbellRoot** node, point to **Insert Schema Node**, and then click **Child Field Element** to add the following fields (repeat this step for each field element):</span></span>  

    -   <span data-ttu-id="b9c1a-123">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="b9c1a-123">**FirstName**</span></span>  

    -   <span data-ttu-id="b9c1a-124">**MiddleName**</span><span class="sxs-lookup"><span data-stu-id="b9c1a-124">**MiddleName**</span></span>  

    -   <span data-ttu-id="b9c1a-125">**lastName**</span><span class="sxs-lookup"><span data-stu-id="b9c1a-125">**LastName**</span></span>  

    -   <span data-ttu-id="b9c1a-126">**SSN**</span><span class="sxs-lookup"><span data-stu-id="b9c1a-126">**SSN**</span></span>  

15. <span data-ttu-id="b9c1a-127">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-127">In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.</span></span>  

16. <span data-ttu-id="b9c1a-128">在加入新項目-BTAHL7 專案對話方塊中，於**分類** 窗格中，按一下**BTAHL7 結構描述**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-128">In the Add New Item - BTAHL7 Project dialog box, in the **Categories** pane, click **BTAHL7 Schemas**, and then click **Add**.</span></span>  

17. <span data-ttu-id="b9c1a-129">在 HL7 結構描述選取器 對話方塊中，在**Message 類別**方塊中，選取**V2.X**，然後在**結構描述詳細資料** 窗格中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b9c1a-129">In the HL7 Schema Selector dialog box, in the **Message Class** box, select **V2.X**, and in the **Schema Details** pane, do the following:</span></span>  


    |     <span data-ttu-id="b9c1a-130">使用</span><span class="sxs-lookup"><span data-stu-id="b9c1a-130">Use this</span></span>      |                                     <span data-ttu-id="b9c1a-131">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="b9c1a-131">To do this</span></span>                                     |
    |-------------------|------------------------------------------------------------------------------------|
    |    <span data-ttu-id="b9c1a-132">**版本(Version)**</span><span class="sxs-lookup"><span data-stu-id="b9c1a-132">**Version**</span></span>    |    <span data-ttu-id="b9c1a-133">選取 HL7 訊息的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-133">Select the version number of the HL7 message.</span></span> <span data-ttu-id="b9c1a-134">在本教學課程中，使用**2.2**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-134">In this tutorial, use **2.2**.</span></span>    |
    | <span data-ttu-id="b9c1a-135">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="b9c1a-135">**Message Type**</span></span>  |           <span data-ttu-id="b9c1a-136">選取 HL7 訊息的類型。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-136">Select the type of HL7 message.</span></span> <span data-ttu-id="b9c1a-137">在本教學課程中，使用**ADT**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-137">In this tutorial, use **ADT**.</span></span>           |
    | <span data-ttu-id="b9c1a-138">**觸發程序事件**</span><span class="sxs-lookup"><span data-stu-id="b9c1a-138">**Trigger Event**</span></span> | <span data-ttu-id="b9c1a-139">選取 HL7 訊息的觸發程序事件值。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-139">Select the Trigger Event value for the HL7 message.</span></span> <span data-ttu-id="b9c1a-140">在本教學課程中，使用**A04**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-140">In this tutorial, use **A04**.</span></span> |


18. <span data-ttu-id="b9c1a-141">按一下 **完成**ADT_A04_22_GLO_DEF.xsd （註冊病人） 結構描述新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-141">Click **Finish** to add the ADT_A04_22_GLO_DEF.xsd (Register Patient) schema to your project.</span></span> <span data-ttu-id="b9c1a-142">關閉 [HL7 結構描述選取器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-142">Close the HL7 Schema Selector dialog box.</span></span>  

19. <span data-ttu-id="b9c1a-143">在 方案總管底下**BTAHL7 專案**，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-143">In Solution Explorer, under **BTAHL7 Project**, right-click **References** and then click **Add Reference**.</span></span>  

20. <span data-ttu-id="b9c1a-144">在 加入參考 對話方塊中上,**專案**索引標籤上，選取**BTAHL7V22Common**專案，按一下 **新增**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-144">In the Add Reference dialog box, on the **Projects** tab, select the **BTAHL7V22Common** project, click **Add**, and then click **OK**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="b9c1a-145">這會加入至原始專案的參考，讓[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]正確辨識 HL7 結構描述。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-145">This adds a reference to the original project so that [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] recognizes the HL7 schemas correctly.</span></span>  

21. <span data-ttu-id="b9c1a-146">在 方案總管底下**BTAHL7 專案**，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-146">In Solution Explorer, under **BTAHL7 Project**, right-click **References** and then click **Add Reference**.</span></span>  

22. <span data-ttu-id="b9c1a-147">在 [加入參考] 對話方塊中，按一下**瀏覽**] 索引標籤。在 [**查詢**方塊中，移至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\End 端對端教學課程中的快速鍵對應\Tutorial_BTAHL7Drop\Bin。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-147">In the Add Reference dialog box, click the **Browse** tab. In the **Look In** box, move to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop\Bin.</span></span> <span data-ttu-id="b9c1a-148">按一下  **Microsoft.Solutions.BTAHL7.HL7Schemas.dll**，按一下**新增**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-148">Click **Microsoft.Solutions.BTAHL7.HL7Schemas.dll**, click **Add**, and then click **OK**.</span></span>  

    <span data-ttu-id="b9c1a-149">請繼續進行[步驟 5： 升級結構描述屬性](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b9c1a-149">Proceed to [Step 5: Promote Schema Properties](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="b9c1a-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9c1a-150">See Also</span></span>  
 [<span data-ttu-id="b9c1a-151">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="b9c1a-151">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)