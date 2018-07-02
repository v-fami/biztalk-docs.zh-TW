---
title: 支援擴充編碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a40fa6-d0da-416e-97fb-675ddde3f005
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f12412e42eda63400260c466bf4c9b34f93881db
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989319"
---
# <a name="extended-encoding-support"></a><span data-ttu-id="d7eae-102">支援擴充編碼</span><span class="sxs-lookup"><span data-stu-id="d7eae-102">Extended Encoding Support</span></span>
<span data-ttu-id="d7eae-103">根據預設，接收 HL7 管線，BTAHL72X，僅支援 ASCII 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="d7eae-103">By default, the HL7 receive pipeline, BTAHL72X, only supports ASCII encoding.</span></span> <span data-ttu-id="d7eae-104">這表示，對等的值大於 127 會被取代的輸入訊息中的任何字元"？"。</span><span class="sxs-lookup"><span data-stu-id="d7eae-104">This means that any characters in an input message with an equivalent value greater than 127 are replaced with "?".</span></span> <span data-ttu-id="d7eae-105">這是因為具有相等值大於 127 的字元不會出現在 ASCII 字元集。</span><span class="sxs-lookup"><span data-stu-id="d7eae-105">This is because characters with an equivalent value greater than 127 are not represented in the ASCII character set.</span></span>  
  
 [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]<span data-ttu-id="d7eae-106"> 提供兩個新的編碼方式的支援：</span><span class="sxs-lookup"><span data-stu-id="d7eae-106"> provides support for two new encodings:</span></span>  
  
- <span data-ttu-id="d7eae-107">西歐語系</span><span class="sxs-lookup"><span data-stu-id="d7eae-107">Western European</span></span>  
  
- <span data-ttu-id="d7eae-108">UTF-8</span><span class="sxs-lookup"><span data-stu-id="d7eae-108">UTF-8</span></span>  
  
  <span data-ttu-id="d7eae-109">您建立並建置自訂管線元件實作擴充的編碼支援。</span><span class="sxs-lookup"><span data-stu-id="d7eae-109">You create and build a custom pipeline component to implement extended encoding support.</span></span> <span data-ttu-id="d7eae-110">自訂管線元件會使用 BTAHL7 2.X 反組譯工具。</span><span class="sxs-lookup"><span data-stu-id="d7eae-110">The custom pipeline component uses the BTAHL7 2.X Disassembler.</span></span> <span data-ttu-id="d7eae-111">您建立使用自訂管線來處理訊息的接收位置。</span><span class="sxs-lookup"><span data-stu-id="d7eae-111">You create a receive location that uses the custom pipeline to process messages.</span></span> <span data-ttu-id="d7eae-112">若要測試的接收位置和自訂管線，您可以建立使用 BTAHL7 2.XSendPipeline 的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d7eae-112">To test the receive location and custom pipeline, you create a send port that uses the BTAHL7 2.XSendPipeline.</span></span>  
  
### <a name="to-create-a-custom-pipeline"></a><span data-ttu-id="d7eae-113">若要建立的自訂管線</span><span class="sxs-lookup"><span data-stu-id="d7eae-113">To create a custom pipeline</span></span>  
  
1. <span data-ttu-id="d7eae-114">在  [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]，新增**空白 BizTalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="d7eae-114">In [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)], add a new **Empty BizTalk Server Project**.</span></span>  
  
2. <span data-ttu-id="d7eae-115">在 [方案總管] 中，以滑鼠右鍵按一下新的專案中，按一下**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="d7eae-115">In Solution Explorer, right-click the new project, click **Add**, and then click **New Item**.</span></span>  
  
3. <span data-ttu-id="d7eae-116">在 **加入新項目**對話方塊方塊中，加入新**接收管線**。</span><span class="sxs-lookup"><span data-stu-id="d7eae-116">In the **Add New Item** dialog box, add a new **Receive Pipeline**.</span></span>  
  
4. <span data-ttu-id="d7eae-117">從管線工具箱，拖曳**BTAHL7 2.X 反組譯工具**到管線編輯器並放置**解譯**階段**放在此處**目標。</span><span class="sxs-lookup"><span data-stu-id="d7eae-117">From the pipeline toolbox, drag the **BTAHL7 2.X Disassembler** to the pipeline editor and drop it onto the **Disassemble** stage **Drop Here** target.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d7eae-118">如果 BTAHL7 2.7 解譯器不在 工具箱 中，以滑鼠右鍵按一下工具箱 中，按一下**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="d7eae-118">If the BTAHL7 2.7 Disassembler is not in the toolbox, right-click in the toolbox, and click **Choose Items**.</span></span> <span data-ttu-id="d7eae-119">在 **選擇工具箱項目**對話方塊的  **BizTalk 管線元件**索引標籤上，選取**BTAHL7 2.X 反組譯工具**核取方塊，然後**確定**.</span><span class="sxs-lookup"><span data-stu-id="d7eae-119">In the **Choose Toolbox Items** dialog box, on the **BizTalk Pipeline Component** tab, select the **BTAHL7 2.X Disassembler** check box, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="d7eae-120">在 [屬性] 窗格**BTAHL7 2.X 反組譯工具**，從**編碼字元集**下拉式清單中，選取**西歐**或**UTF8**編碼方式。</span><span class="sxs-lookup"><span data-stu-id="d7eae-120">In the Properties pane for the **BTAHL7 2.X Disassembler**, from the **Encoding charset** drop-down list, select **Western European** or **UTF8** encoding.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d7eae-121">HL7 僅支援 ASCII （預設值）、 歐洲西部和 UTF8 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="d7eae-121">HL7 only supports ASCII (the default), Western European, and UTF8 encoding.</span></span> <span data-ttu-id="d7eae-122">請勿選取其他編碼的選項，因為 HL7 不支援它們。</span><span class="sxs-lookup"><span data-stu-id="d7eae-122">Do not select the other encoding options because HL7 does not support them.</span></span>  
  
6. <span data-ttu-id="d7eae-123">按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="d7eae-123">On the **File** menu, click **Save All**.</span></span>  
  
7. <span data-ttu-id="d7eae-124">部署專案。</span><span class="sxs-lookup"><span data-stu-id="d7eae-124">Deploy the project.</span></span>  
  
    <span data-ttu-id="d7eae-125">建立新接收位置，以繼續。</span><span class="sxs-lookup"><span data-stu-id="d7eae-125">Create a new receive location to continue.</span></span>  
  
### <a name="to-create-a-receive-location-that-uses-the-custom-pipeline"></a><span data-ttu-id="d7eae-126">若要建立接收位置使用自訂管線</span><span class="sxs-lookup"><span data-stu-id="d7eae-126">To create a receive location that uses the custom pipeline</span></span>  
  
1. <span data-ttu-id="d7eae-127">上**開始**功能表上，按一下**程式**，指向[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d7eae-127">On the **Start** menu, click **Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="d7eae-128">在 BizTalk Server 管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開**BizTalk 群組**，依序展開**應用程式**，依序展開 應用程式您指定的管線組件 (根據預設， **BizTalk Application 1**)，以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="d7eae-128">In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, expand the application you designated for your pipeline assembly (by default, **BizTalk Application 1**), right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
3. <span data-ttu-id="d7eae-129">在 **接收位置屬性**對話方塊中，於**接收管線**下拉式清單中，選取的自訂名稱管線所建立。</span><span class="sxs-lookup"><span data-stu-id="d7eae-129">In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, select the name of the custom pipeline you created.</span></span> <span data-ttu-id="d7eae-130">(這是自訂的管線物件，而不 BTAHL7 名稱 2 X 管線。)</span><span class="sxs-lookup"><span data-stu-id="d7eae-130">(This is the name of the custom pipeline object, not the BTAHL7 2X pipeline.)</span></span>  
  
### <a name="to-create-a-send-port-to-test-the-receive-location-and-pipeline"></a><span data-ttu-id="d7eae-131">若要建立要測試的接收位置和管線的傳送埠</span><span class="sxs-lookup"><span data-stu-id="d7eae-131">To create a send port to test the receive location and pipeline</span></span>  
  
1. <span data-ttu-id="d7eae-132">上**開始**功能表上，按一下**程式**，指向[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d7eae-132">On the **Start** menu, click **Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="d7eae-133">在 BizTalk Server 管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開**BizTalk 群組**，依序展開**應用程式**，依序展開 應用程式您指定的管線組件 (根據預設， **BizTalk Application 1**)，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下  **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d7eae-133">In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, expand the application you designated for your pipeline assembly (by default, **BizTalk Application 1**), right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
3. <span data-ttu-id="d7eae-134">在 **傳送埠屬性**對話方塊中，於**傳送管線**下拉式清單中，選取**BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="d7eae-134">In the **Send Port Properties** dialog box, in the **Send pipeline** drop-down list, select **BTAHL72XSendPipeline**.</span></span>  
  
### <a name="to-test-the-receive-location-and-pipeline"></a><span data-ttu-id="d7eae-135">若要測試的接收位置和管線</span><span class="sxs-lookup"><span data-stu-id="d7eae-135">To test the receive location and pipeline</span></span>  
  
-   <span data-ttu-id="d7eae-136">卸除包含特殊字元，並使用相同的接收位置中指定的位置在自訂管線中所指定的編碼儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="d7eae-136">Drop a file containing special characters and saved with the same encoding you specified in the custom pipeline into the location designated in the receive location.</span></span> <span data-ttu-id="d7eae-137">在 輸出位置的檔案應該保留的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="d7eae-137">The file at the output location should preserve the special characters.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7eae-138">如果您嘗試使用不受支援的編碼方式將檔案處理 （請記住，只有 ASCII 西歐上，支援、 和 UTF8），錯誤會記錄在應用程式事件檢視器，錯誤識別碼： 5633。</span><span class="sxs-lookup"><span data-stu-id="d7eae-138">If you attempt to process a file that uses a non-supported encoding (remember that only ASCII, Western European, and UTF8 are supported), an error is logged in the Application Event Viewer with error ID: 5633.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7eae-139">如果您要測試自訂管線設定為 UTF8 編碼方式，您應該附加位元組順序標記 (BOM) 字元所傳遞的訊息。</span><span class="sxs-lookup"><span data-stu-id="d7eae-139">If you are testing a custom pipeline configured for UTF8 encoding, you should attach Byte Order Mark (BOM) characters to the message you are passing.</span></span> <span data-ttu-id="d7eae-140">如果您要測試自訂管線設定為 [西歐] 文字編碼方式，不要附加 BOM 字元。</span><span class="sxs-lookup"><span data-stu-id="d7eae-140">If you are testing a custom pipeline configured for Western European encoding, do not attach BOM characters.</span></span>