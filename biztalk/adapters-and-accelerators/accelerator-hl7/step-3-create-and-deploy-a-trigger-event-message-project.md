---
title: 步驟 3： 建立及部署觸發程序事件 （訊息） 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, trigger events
- trigger events
ms.assetid: 5d21a923-fc2c-4d50-b146-daca0aa26e2a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: deb9d6160fc0b094f0af6f75ab4ab8e5be22462c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998687"
---
# <a name="step-3-create-and-deploy-a-trigger-event-message-project"></a><span data-ttu-id="0cd56-102">步驟 3： 建立及部署觸發程序事件 （訊息） 專案</span><span class="sxs-lookup"><span data-stu-id="0cd56-102">Step 3: Create and Deploy a Trigger Event (Message) Project</span></span>
<span data-ttu-id="0cd56-103">在此步驟中，您可以建立結構描述觸發程序事件訊息。</span><span class="sxs-lookup"><span data-stu-id="0cd56-103">In this step, you create the schema for your trigger event message.</span></span> <span data-ttu-id="0cd56-104">比方說，您可能會是許可出院和傳輸系統 (ADT) 傳送訊息至醫院資訊系統 (HIS)。</span><span class="sxs-lookup"><span data-stu-id="0cd56-104">For example, you might be the Admissions Discharge and Transfer system (ADT) who sends a message to the Hospital Information System (HIS).</span></span> <span data-ttu-id="0cd56-105">您需要此結構描述來定義訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="0cd56-105">You need this schema to define the format of your message.</span></span>  
  
### <a name="to-create-the-project-for-the-trigger-event-message"></a><span data-ttu-id="0cd56-106">若要建立觸發程序事件訊息的專案</span><span class="sxs-lookup"><span data-stu-id="0cd56-106">To create the project for the trigger event message</span></span>  
  
1. <span data-ttu-id="0cd56-107">在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下**專案**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-107">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, then click **Project**.</span></span>  
  
2. <span data-ttu-id="0cd56-108">在 [新增專案] 對話方塊中，在**專案類型**區段中，展開**BizTalk 專案**，然後按一下**BTAHL7Projects**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-108">In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then click **BTAHL7Projects**.</span></span>  
  
3. <span data-ttu-id="0cd56-109">在 範本 區段中，按一下  **BTAHL7 的空白專案**，請在**名稱**方塊中，輸入**BTAHL7V231Body 專案**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-109">In the Templates section, click **Empty BTAHL7 Project**, in the **Name** box, type **BTAHL7V231Body Project**, and then click **OK**.</span></span>  
  
4. <span data-ttu-id="0cd56-110">在 [方案總管] 節點下的新專案，以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-110">In Solution Explorer, under the node for your new project, right-click **References**, and then click **Add Reference**.</span></span>  
  
5. <span data-ttu-id="0cd56-111">在加入參考 對話方塊中上,**專案**索引標籤上，選取**BTAHL7V231Common Project1**，按一下**新增**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-111">In the Add Reference dialog box, on the **Projects** tab, select **BTAHL7V231Common Project1**, click **Add**, and then click **OK**.</span></span>  
  
## <a name="step-3a-add-the-schema"></a><span data-ttu-id="0cd56-112">步驟 3A： 新增結構描述</span><span class="sxs-lookup"><span data-stu-id="0cd56-112">Step 3A: Add the Schema</span></span>  
 <span data-ttu-id="0cd56-113">使用下列程序，將新的結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="0cd56-113">Use the following procedure to add the new schema to the project.</span></span>  
  
#### <a name="to-add-the-schema-to-the-project"></a><span data-ttu-id="0cd56-114">將結構描述加入至專案</span><span class="sxs-lookup"><span data-stu-id="0cd56-114">To add the schema to the project</span></span>  
  
1.  <span data-ttu-id="0cd56-115">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V231Body 專案**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-115">In Solution Explorer, right-click **BTAHL7V231Body Project**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="0cd56-116">在 新增新項目對話方塊中，於**分類**區段中，展開**BizTalk 專案項目**，然後選取**BTAHL7 結構描述**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-116">In the Add New Item dialog box, in the **Categories** section, expand **BizTalk Project Items**, and then select **BTAHL7 Schemas**.</span></span>  
  
3.  <span data-ttu-id="0cd56-117">在 [範本] 區段中，按兩下**BTAHL7 結構描述**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-117">In the Templates section, double-click **BTAHL7 Schemas**.</span></span>  
  
4.  <span data-ttu-id="0cd56-118">在 [HL7 結構描述選取器] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0cd56-118">In the HL7 Schema Selector dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="0cd56-119">使用</span><span class="sxs-lookup"><span data-stu-id="0cd56-119">Use this</span></span>|<span data-ttu-id="0cd56-120">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0cd56-120">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0cd56-121">**Message 類別**</span><span class="sxs-lookup"><span data-stu-id="0cd56-121">**Message Class**</span></span>|<span data-ttu-id="0cd56-122">保留預設值**V2.X**選取。</span><span class="sxs-lookup"><span data-stu-id="0cd56-122">Leave the default of **V2.X** selected.</span></span>|  
    |<span data-ttu-id="0cd56-123">**版本(Version)**</span><span class="sxs-lookup"><span data-stu-id="0cd56-123">**Version**</span></span>|<span data-ttu-id="0cd56-124">選取  **2.3.1**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-124">Select **2.3.1**.</span></span>|  
    |<span data-ttu-id="0cd56-125">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="0cd56-125">**Message Type**</span></span>|<span data-ttu-id="0cd56-126">選取  **ADT**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-126">Select **ADT**.</span></span>|  
    |<span data-ttu-id="0cd56-127">**觸發程序事件**</span><span class="sxs-lookup"><span data-stu-id="0cd56-127">**Trigger Event**</span></span>|<span data-ttu-id="0cd56-128">選取 **將 adt^a03**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-128">Select **A03**.</span></span>|  
  
5.  <span data-ttu-id="0cd56-129">按一下 **完成**將結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="0cd56-129">Click **Finish** to add the schema to the project.</span></span>  
  
## <a name="step-3b-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="0cd56-130">步驟 3B： 指派強式金鑰組件和部署</span><span class="sxs-lookup"><span data-stu-id="0cd56-130">Step 3B: Assign a Strong Key to the Assembly and Deploy</span></span>  
 <span data-ttu-id="0cd56-131">使用下列程序組件指派強式金鑰，然後再部署組件。</span><span class="sxs-lookup"><span data-stu-id="0cd56-131">Use the following procedure to assign a strong key to the assembly and then deploy the assembly.</span></span>  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a><span data-ttu-id="0cd56-132">指派強式金鑰，並部署組件</span><span class="sxs-lookup"><span data-stu-id="0cd56-132">To assign a strong key and deploy the assembly</span></span>  
  
1. <span data-ttu-id="0cd56-133">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V231Body 專案**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-133">In Solution Explorer, right-click **BTAHL7V231Body Project**, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="0cd56-134">在 [專案屬性頁] 頁面中，按一下**組件**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-134">In the Project Property Pages page, click **Assembly**.</span></span>  
  
3. <span data-ttu-id="0cd56-135">在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0cd56-135">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (**…**) button.</span></span>  
  
4. <span data-ttu-id="0cd56-136">在 組件金鑰檔案 對話方塊中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>加速器 HL7\SDK\End 端對端教學課程中，按一下  **key.snk**，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-136">In the Assembly Key File dialog box, browse to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial, click **key.snk**, and then click **Open**.</span></span>  
  
5. <span data-ttu-id="0cd56-137">在 [專案屬性頁] 對話方塊中，按一下**確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="0cd56-137">In the Project Property Pages dialog box, click **OK** to save your changes.</span></span>  
  
6. <span data-ttu-id="0cd56-138">在 [方案總管] 中以滑鼠右鍵按一下**BTAHL7V231Body 專案**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="0cd56-138">In Solution Explorer right-click **BTAHL7V231Body Project**, and then click **Deploy**.</span></span> <span data-ttu-id="0cd56-139">請確定在 [輸出] 視窗中會出現成功訊息。</span><span class="sxs-lookup"><span data-stu-id="0cd56-139">Ensure a success message appears in the output window.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="0cd56-140">如果不成功的部署訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0cd56-140">If a successful deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
   <span data-ttu-id="0cd56-141">請繼續進行[步驟 4： 建立接收埠，以接受 ADT ^ 來自 ADT 系統使用 MLLP 配接器將 adt^a03 訊息](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)。</span><span class="sxs-lookup"><span data-stu-id="0cd56-141">Proceed to [Step 4: Create the Receive Port for Accepting ADT^A03 Messages from ADT Systems Using the MLLP Adapter](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md).</span></span>