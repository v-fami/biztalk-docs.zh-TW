---
title: "步驟 3： 新增觸發程序事件 （訊息） 結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc4a67d9-9582-4f2b-9bc9-18fbff823d29
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 439caac8f1da151a9f203a1372039aaeedbfe83c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-add-a-trigger-event-message-schema"></a><span data-ttu-id="314a8-102">步驟 3： 新增觸發程序事件 （訊息） 結構描述</span><span class="sxs-lookup"><span data-stu-id="314a8-102">Step 3: Add a Trigger Event (Message) Schema</span></span>
<span data-ttu-id="314a8-103">在此步驟中，您會建立空的新專案[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]專案範本。</span><span class="sxs-lookup"><span data-stu-id="314a8-103">In this step, you create a new project based on the Empty [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Project template.</span></span> <span data-ttu-id="314a8-104">加入此專案中，您將結構描述，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]用來驗證內送的批次中的訊息 (ADT ^ A03)。</span><span class="sxs-lookup"><span data-stu-id="314a8-104">To this project, you add the schema that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will use to validate the messages in the incoming batch (ADT^A03).</span></span> <span data-ttu-id="314a8-105">您將參考加入包含 v2.3.1 通用結構描述的專案，專案中，指派強式名稱，然後再部署專案。</span><span class="sxs-lookup"><span data-stu-id="314a8-105">You add a reference to the project containing the v2.3.1 common schemas, assign the strong name to the project, and then deploy the project.</span></span>  
  
### <a name="to-add-the-project-containing-the-message-schema"></a><span data-ttu-id="314a8-106">若要加入包含訊息結構描述的專案</span><span class="sxs-lookup"><span data-stu-id="314a8-106">To add the project containing the message schema</span></span>  
  
1.  <span data-ttu-id="314a8-107">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="314a8-107">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="314a8-108">在 [新增專案] 對話方塊中**專案類型**區段中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。</span><span class="sxs-lookup"><span data-stu-id="314a8-108">In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="314a8-109">在**範本**區段中，選取**空白 BTAHL7 專案**。</span><span class="sxs-lookup"><span data-stu-id="314a8-109">In the **Templates** section, select **Empty BTAHL7 Project**.</span></span>  
  
4.  <span data-ttu-id="314a8-110">在**名稱**方塊中，輸入**BTAHL7V231Body**做為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="314a8-110">In the **Name** box, enter **BTAHL7V231Body** as the project name.</span></span>  
  
5.  <span data-ttu-id="314a8-111">在**方案**方塊中，選取**將加入至方案**。</span><span class="sxs-lookup"><span data-stu-id="314a8-111">In the **Solution** box, select **Add to Solution**.</span></span>  
  
6.  <span data-ttu-id="314a8-112">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="314a8-112">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="314a8-113">在 方案總管 節點下的新專案中，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="314a8-113">In Solution Explorer, under the node for your new project, right-click **References**, and then click **Add Reference**.</span></span>  
  
8.  <span data-ttu-id="314a8-114">在 加入參考 對話方塊上**專案**索引標籤上，按一下  **BTAHL7V231Common 專案**中**專案名稱**資料行中，按一下 **新增**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="314a8-114">In the Add Reference dialog box, on the **Projects** tab, click **BTAHL7V231Common Project** in the **Project Name** column, click **Add**, and then click **OK**.</span></span>  
  
### <a name="to-add-the-schema-to-the-project"></a><span data-ttu-id="314a8-115">將結構描述加入至專案</span><span class="sxs-lookup"><span data-stu-id="314a8-115">To add the schema to the project</span></span>  
  
1.  <span data-ttu-id="314a8-116">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Body**，指向 **新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="314a8-116">In Solution Explorer, right-click **BTAHL7V231Body**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="314a8-117">在 加入新項目 對話方塊中，依序展開**BizTalk 專案項目**，然後按一下  **BTAHL7 結構描述**。</span><span class="sxs-lookup"><span data-stu-id="314a8-117">In the Add New Item dialog box, expand **BizTalk Project Items**, and then click **BTAHL7 Schemas**.</span></span> <span data-ttu-id="314a8-118">在**範本** 窗格中，按一下  **BTAHL7 結構描述**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="314a8-118">In the **Templates** pane, click **BTAHL7 Schemas**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="314a8-119">在**HL7 結構描述選取器**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="314a8-119">In the **HL7 Schema Selector** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="314a8-120">使用</span><span class="sxs-lookup"><span data-stu-id="314a8-120">Use this</span></span>|<span data-ttu-id="314a8-121">動作</span><span class="sxs-lookup"><span data-stu-id="314a8-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="314a8-122">**Message 類別**</span><span class="sxs-lookup"><span data-stu-id="314a8-122">**Message Class**</span></span>|<span data-ttu-id="314a8-123">保留**V2.X**為選取狀態。</span><span class="sxs-lookup"><span data-stu-id="314a8-123">Keep **V2.X** as selected.</span></span>|  
    |<span data-ttu-id="314a8-124">**版本**</span><span class="sxs-lookup"><span data-stu-id="314a8-124">**Version**</span></span>|<span data-ttu-id="314a8-125">選取**2.3.1**。</span><span class="sxs-lookup"><span data-stu-id="314a8-125">Select **2.3.1**.</span></span>|  
    |<span data-ttu-id="314a8-126">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="314a8-126">**Message Type**</span></span>|<span data-ttu-id="314a8-127">選取**ADT**。</span><span class="sxs-lookup"><span data-stu-id="314a8-127">Select **ADT**.</span></span>|  
    |<span data-ttu-id="314a8-128">**觸發程序事件**</span><span class="sxs-lookup"><span data-stu-id="314a8-128">**Trigger Event**</span></span>|<span data-ttu-id="314a8-129">選取**A03**。</span><span class="sxs-lookup"><span data-stu-id="314a8-129">Select **A03**.</span></span>|  
  
4.  <span data-ttu-id="314a8-130">按一下**建立**將結構描述加入至專案，然後按一下 **取消**以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="314a8-130">Click **Create** to add the schema to the project, then click **Cancel** to close the dialog box.</span></span> <span data-ttu-id="314a8-131">請注意該 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 已加入 BTAHL7V231Body 專案 ADT_A03_231_GLO_DEF.xsd 結構描述。</span><span class="sxs-lookup"><span data-stu-id="314a8-131">Note that BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) has added the ADT_A03_231_GLO_DEF.xsd schema to the BTAHL7V231Body project.</span></span>  
  
### <a name="to-assign-a-strong-key-and-deploy"></a><span data-ttu-id="314a8-132">指派強式金鑰和部署</span><span class="sxs-lookup"><span data-stu-id="314a8-132">To assign a strong key and deploy</span></span>  
  
1.  <span data-ttu-id="314a8-133">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Body**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="314a8-133">In Solution Explorer, right-click **BTAHL7V231Body**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="314a8-134">在 [BTAHL7V231Body 屬性頁] 對話方塊中，按一下**簽署**。</span><span class="sxs-lookup"><span data-stu-id="314a8-134">In the BTAHL7V231Body Property Page dialog box, click **Signing**.</span></span>  
  
3.  <span data-ttu-id="314a8-135">請檢查**簽署組件**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="314a8-135">Check **Sign the assembly** check box.</span></span>  
  
4.  <span data-ttu-id="314a8-136">在**選擇強式名稱金鑰檔**下拉式清單中，選取**\<瀏覽...\>.**</span><span class="sxs-lookup"><span data-stu-id="314a8-136">In **Choose a strong name key file** drop down list select **\<Browse…\>.**</span></span>  
  
5.  <span data-ttu-id="314a8-137">瀏覽至  **\<*磁碟機*\>: \Batching 教學課程 * *，選取**key.snk**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="314a8-137">Browse to **\<*drive*\>:\Batching Tutorial**, select **key.snk**, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="314a8-138">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Body**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="314a8-138">In Solution Explorer, right-click **BTAHL7V231Body**, and then click **Deploy**.</span></span> <span data-ttu-id="314a8-139">請在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="314a8-139">Ensure that a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="314a8-140">如果未出現 successful-deploy 訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="314a8-140">If a successful-deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
 <span data-ttu-id="314a8-141">若要繼續[步驟 4： 建立接收埠，以便接受批次訊息](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md)。</span><span class="sxs-lookup"><span data-stu-id="314a8-141">Proceed to [Step 4: Create a Receive Port for Accepting the Batch Message](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md).</span></span>