---
title: "步驟 8： 檢視 BTARN 資料庫中的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, viewing
- loopback tutorial, viewing messages
- databases, viewing messages
ms.assetid: c549670c-4428-483c-906c-eff163ddef9a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2324cca59a9104d8f40b5b6b69eca76af1004384
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-view-messages-in-the-btarn-databases"></a><span data-ttu-id="c7791-102">步驟 8： 檢視 BTARN 資料庫中的訊息</span><span class="sxs-lookup"><span data-stu-id="c7791-102">Step 8: View Messages in the BTARN Databases</span></span>
<span data-ttu-id="c7791-103">在此步驟中，您將使用 SQL Query Analyzer 檢視 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 資料庫中儲存的企業營運系統 (LOB) 訊息，以確認回送實例能夠正確運作。</span><span class="sxs-lookup"><span data-stu-id="c7791-103">In this step, you use SQL Query Analyzer to view line-of-business (LOB) messages stored in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] database to verify that your loop-back scenario is working correctly.</span></span>  
  
 <span data-ttu-id="c7791-104">在 LOB 應用程式公用程式產生 LOB 訊息並提交至 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 後，啟動者 (組織) 和回應者 (交易夥伴) 會發生以下事件：</span><span class="sxs-lookup"><span data-stu-id="c7791-104">After the LOB Application utility generates an LOB message and submits it to [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the following events occur for the initiator (home) and the responder (partner):</span></span>  
  
 <span data-ttu-id="c7791-105">啟動者工作流程</span><span class="sxs-lookup"><span data-stu-id="c7791-105">Initiator Workflow</span></span>  
  
-   <span data-ttu-id="c7791-106">SubmitRNIF 會將 LOB 訊息提交到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA 資料庫的 MessagesFromLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="c7791-106">SubmitRNIF submits the LOB message to the MessagesFromLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA database.</span></span>  
  
-   <span data-ttu-id="c7791-107">SQL 配接器接收位置會挑出訊息，然後送到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7791-107">The SQL adapter receive location picks up the message and delivers it to the MessageBox database.</span></span> <span data-ttu-id="c7791-108">SQL 配接器每執行一次 `GetMessagesFromLOB` 預存程序，就會挑出一個訊息。</span><span class="sxs-lookup"><span data-stu-id="c7791-108">The SQL adapter picks up one message at a time running the `GetMessagesFromLOB` stored procedure.</span></span>  
  
-   <span data-ttu-id="c7791-109">私用啟動者會從 MessageBox 資料庫挑出訊息，然後加上額外的升級內容屬性後，再次放到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7791-109">The private initiator picks the message from the MessageBox database and then drops it again to the MessageBox database with additional promoted context properties.</span></span>  
  
-   <span data-ttu-id="c7791-110">公開啟動者則根據訂閱篩選從 MessageBox 資料庫挑出訊息。</span><span class="sxs-lookup"><span data-stu-id="c7791-110">The public initiator picks the message from the MessageBox database based on the subscription filter.</span></span>  
  
-   <span data-ttu-id="c7791-111">HTTP 傳送埠會根據訂閱挑出具有 RNIFSend 管線的訊息，</span><span class="sxs-lookup"><span data-stu-id="c7791-111">The HTTP send port picks the message with the RNIFSend pipeline based on the subscriptions.</span></span> <span data-ttu-id="c7791-112">為不可否認性目的，將訊息儲存於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 封存資料庫的 MessageStorageOut 資料表，然後再將訊息傳送到 RNIFSend.aspx 頁面。</span><span class="sxs-lookup"><span data-stu-id="c7791-112">It saves the message in the MessageStorageOut table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Archive database for non-repudiation, and then sends the message over to the RNIFSend.aspx page.</span></span>  
  
-   <span data-ttu-id="c7791-113">RNIFSend.aspx 頁面會接收具有查詢字串變數的 MIME 編碼訊息，那些變數中包含訊息的最終目的地 (交易夥伴組織 URL)。</span><span class="sxs-lookup"><span data-stu-id="c7791-113">The RNIFSend.aspx page receives the MIME-encoded message with query string variables that include the final destination of the message (partner organization URL).</span></span>  
  
 <span data-ttu-id="c7791-114">回應者工作流程</span><span class="sxs-lookup"><span data-stu-id="c7791-114">Responder Workflow</span></span>  
  
-   [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="c7791-115"> 會將 RNIF 訊息傳送到 RNIFReceive.aspx 頁面，在該頁面中已移除 MIME 解碼包裝函式。</span><span class="sxs-lookup"><span data-stu-id="c7791-115"> sends the RNIF message to the RNIFReceive.aspx page where the MIME-decoded wrapper is removed.</span></span> <span data-ttu-id="c7791-116">訊息會被識別為同步或非同步，接著再轉寄到同步或非同步接收位置 (RNIF_Sync_Receive 或 RNIF_Async_Receive)。</span><span class="sxs-lookup"><span data-stu-id="c7791-116">The message is identified as either synchronous or asynchronous, and then forwarded to either the synchronous or asynchronous receive location (RNIF_Sync_Receive or RNIF_Async_Receive).</span></span>  
  
-   <span data-ttu-id="c7791-117">HTTP 接收位置首先會為不可否認性目的，將訊息以傳輸格式儲存於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 封存資料庫的 MessageStorageIn 資料表內，</span><span class="sxs-lookup"><span data-stu-id="c7791-117">The HTTP receive location first saves the wire format of the message in the MessageStorageIn table for non-repudiation of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Archive database.</span></span> <span data-ttu-id="c7791-118">然後解碼、解密 (適用 RNIF 2.0)、驗證簽章、解譯 XML 訊息部分、根據簽章進行授權，最後加上正確的升級屬性後，放置到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7791-118">The HTTP receive location then decodes, decrypts (for RNIF 2.0), validates on its signature, disassembles the XML message parts, authorizes based on the signature, and then drops it in the MessageBox database with the correct promoted properties</span></span>  
  
-   <span data-ttu-id="c7791-119">公用回應者會根據訂閱挑出訊息，然後依照正確的 RNIF 標準驗證及處理訊息。</span><span class="sxs-lookup"><span data-stu-id="c7791-119">The public responder picks the message parts based on subscription, and then validates and processes the message based on the correct RNIF standard.</span></span> <span data-ttu-id="c7791-120">服務內容部分會加上正確的內容屬性，然後將訊息放置於 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7791-120">The service content part drops the message into the MessageBox database with the correct context properties.</span></span>  
  
-   <span data-ttu-id="c7791-121">SQL 傳送埠會根據訂閱篩選挑出訊息，</span><span class="sxs-lookup"><span data-stu-id="c7791-121">The SQL send port picks the message based on the subscription filter.</span></span> <span data-ttu-id="c7791-122">然後將訊息儲存至 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA 資料庫的 MessagesToLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="c7791-122">It then saves the message in the MessagesToLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7791-123">在回應者端，公用回應者負責產生接收通知或例外信號回到起始端。</span><span class="sxs-lookup"><span data-stu-id="c7791-123">On the responder side, the Public Responder is responsible for generating the acknowledgement receipt or the exception signal back to the initiator.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="c7791-124">不會儲存在 MessagesFromLOB 資料表中的信號訊息。</span><span class="sxs-lookup"><span data-stu-id="c7791-124"> does not save the signal message in the MessagesFromLOB table.</span></span> <span data-ttu-id="c7791-125">因為 LOB 應用程式不會產生信號訊息。</span><span class="sxs-lookup"><span data-stu-id="c7791-125">This is because the LOB application does not generate the signal message.</span></span> <span data-ttu-id="c7791-126">動作訊息將繼續通過「私用回應者」，且 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將它儲存至 MessagesToLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="c7791-126">The Action message will continue through the Private Responder, and [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] saves it to the MessagesToLOB table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7791-127">雙向動作 Pip，回應者端的 LOB 是負責產生回應訊息。</span><span class="sxs-lookup"><span data-stu-id="c7791-127">For double-action PIPs, the LOB on the responder side is responsible for generating a response message.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="c7791-128">卸除它 MessagesFromLOB 資料表移到起始端程序相同的程序。</span><span class="sxs-lookup"><span data-stu-id="c7791-128"> drops it to the MessagesFromLOB table to go through the same process as the initiator-side process.</span></span> <span data-ttu-id="c7791-129">在這個情形下，啟動者端的「公開啟動者程序」會傳回接收通知或例外信號做為回應訊息。</span><span class="sxs-lookup"><span data-stu-id="c7791-129">In this case, the Public Initiator Process on the initiator side sends back an acknowledgement receipt or exception signal for the response message.</span></span>  
  
### <a name="to-view-messages-in-the-btarn-databases"></a><span data-ttu-id="c7791-130">檢視 BTARN 資料庫中的訊息</span><span class="sxs-lookup"><span data-stu-id="c7791-130">To view messages in the BTARN databases</span></span>  
  
1.  <span data-ttu-id="c7791-131">按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="c7791-131">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="c7791-132">在 連接到伺服器 對話方塊中，按一下 **連接**。</span><span class="sxs-lookup"><span data-stu-id="c7791-132">In the Connect to Server dialog box, click **Connect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7791-133">在 [物件總管] 窗格中，確認 SQL Server Agent 是否已啟動。</span><span class="sxs-lookup"><span data-stu-id="c7791-133">In the Object Explorer pane, verify that the SQL Server Agent is started.</span></span> <span data-ttu-id="c7791-134">如果沒有，請以滑鼠右鍵按一下**SQL Server Agent**，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="c7791-134">If not, right-click **SQL Server Agent**, and click **Start**.</span></span>  
  
3.  <span data-ttu-id="c7791-135">在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。</span><span class="sxs-lookup"><span data-stu-id="c7791-135">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="c7791-136">在 [空白的查詢] 視窗中，輸入以下程式碼：</span><span class="sxs-lookup"><span data-stu-id="c7791-136">In the Blank Query window, type the following:</span></span>  
  
    ```  
    use BTARNArchive  
    SELECT * FROM         MessageStorageIn ORDER BY TIMECREATED ASC  
    SELECT * FROM         MessageStorageOut ORDER BY TIMECREATED ASC  
  
    use BTARNData  
    SELECT     * FROM         MessagesFromLOB ORDER BY TIMECREATED ASC  
    SELECT     * FROM         MessagesToLOB ORDER BY TIMECREATED ASC  
    SELECT     * FROM         Attachments ORDER BY TIMECREATED ASC  
    ```  
  
5.  <span data-ttu-id="c7791-137">在 Microsoft SQL Server Management Studio 中，按一下  **Execute**。</span><span class="sxs-lookup"><span data-stu-id="c7791-137">In the Microsoft SQL Server Management Studio, click **Execute**.</span></span>  
  
 <span data-ttu-id="c7791-138">您將看到 MessagesFromLOB 資料表中的動作訊息。若在數分鐘內再次執行查詢 (取決於您系統的組態時間可能不同)，您將看到 MessagesToLOB 資料表中產生兩個訊息，分別具有 AsyncAckSignal (25) 和 AsyncAction (10) 的 MessageCategory 值。</span><span class="sxs-lookup"><span data-stu-id="c7791-138">You will see an action message in the MessagesFromLOB table, and if you run the query again in several minutes (time may vary depending on your system configuration), you will see two messages generated in the MessagesToLOB table with MessageCategory values of AsyncAckSignal (25) and AsyncAction (10).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7791-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7791-139">See Also</span></span>  
 <span data-ttu-id="c7791-140">[回送](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md) </span><span class="sxs-lookup"><span data-stu-id="c7791-140">[Loopback](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md) </span></span>  
 [<span data-ttu-id="c7791-141">回送教學課程</span><span class="sxs-lookup"><span data-stu-id="c7791-141">Loopback Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/loopback-tutorial.md)