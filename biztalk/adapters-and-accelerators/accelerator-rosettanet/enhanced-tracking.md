---
title: "進階追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tracking
ms.assetid: 8adf78f0-ab0f-44d4-aa5b-9546e2bdf01f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0212caafb34ca76988e1a863899021b44ac416fb
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="enhanced-tracking"></a>增強的追蹤
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]提供追蹤程序和訊息的加強的功能。 原生功能的商務活動監控 (BAM) 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]為追蹤僅為中繼資料。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]追蹤訊息內容 — 服務內容和標頭。  
  
 下表顯示 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 資料追蹤的完整範圍。 本主題說明程序和訊息追蹤。 如需有關不可否認性資料的詳細資訊，請參閱[RNIF 訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/rnif-message-processing.md)。  
  
|追蹤的資訊|功能|使用者存取|  
|-------------------------|-------------|-----------------|  
|RosettaNet 程序和訊息追蹤|透過中繼資料的 BAM (具有資料庫資料表與資料檢視) 以及訊息本文的專屬介面|BAM 使用者介面或自訂使用者介面|  
|錯誤和事件|透過 [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] 事件日誌|事件日誌|  
|不可否認性資料|透過專屬介面 (儲存傳輸格式的訊息)|[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive 資料庫中的 MessageStorageIn 與 MessageStorageOut 資料表，且透過 SDK|  
  
## <a name="process-and-message-tracking"></a>程序和訊息追蹤  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]會追蹤兩種基本活動： 程序活動和訊息活動。 程序活動追蹤在公開程序協調流程中處理的訊息； 訊息活動則是追蹤在傳送或接收管線中處理的訊息。  
  
 程序活動追蹤完整的訊息中繼資料； 訊息活動追蹤程序活動中繼資料和訊息內容。  
  
### <a name="process-activity"></a>程序活動  
 只要初始化公開程序協調流程 (啟動者或回應者)，公開程序就會在 BAM 追蹤資料庫中建立程序活動記錄。 在公開程序中不同的點上，協調流程會儲存追蹤中繼資料。 協調流程停止時，程序活動就會停止。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會在下列兩種情況中追蹤程序的完整中繼資料：  
  
-   當 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 是回應者且接收要求動作訊息。  
  
-   當 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 是啟動者且接收來自商務營運系統 (LOB) 應用程式的要求訊息。  
  
 只要 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送或接收訊息，公開程序便會更新程序活動的狀態。  
  
### <a name="message-activity"></a>訊息活動  
 訊息活動透過傳送或接收管線追蹤訊息。 只要傳送或接收管線處理訊息，管線就會建立訊息活動。 管線會在 BAM 追蹤資料庫中建立訊息活動記錄，並在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive 資料庫中建立訊息記錄。  
  
 訊息活動會儲存訊息的內容，包括服務內容及標頭。 在接收管線中，如果 MIME 解碼器成功執行，活動便會以文字格式將訊息內容的四個部分儲存為 XML，放置於 MessageContent 資料表的 ContentXml 資料行。 如果 MIME 解碼器執行失敗，活動便會以二進位格式將訊息內容儲存於 MessageContent 資料表的 ContentBinary 資料行。  
  
### <a name="use-of-tracking-data-in-correlation"></a>將追蹤資料運用在相互關聯上  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 追蹤關聯每個程序與特定 PIP (正或負信號、以及要求和回應信號) 所有已交換訊息所需的資訊。 如果 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送該 PIP 的「失敗通知」，它也會追蹤用來關聯 0A1 訊息的資訊。 PIP 執行個體識別碼、啟動者合作對象名稱及目的合作對象名稱的組合決定與活動相關的訊息。  
  
### <a name="tracking-databases"></a>追蹤資料庫  
 程序和訊息活動會將追蹤中繼資料儲存於 BAMPrimaryImport [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫。 在此資料庫中，資料表名稱以前置詞 "bam_Process" 開頭的資料表儲存程序活動追蹤資料，而資料表名稱以前置詞 "bam_Message" 開頭的資料表儲存訊息活動追蹤資料。 每個不同的程序或訊息活動在資料表中都有與其對應的單一記錄。 名稱以前置詞 "bam_Metadata" 開頭的中繼資料資料表則儲存這兩種活動的相關資訊，以及中繼資料追蹤的資訊。  
  
 您可以使用下列檢視取用 BAMPrimaryImport 追蹤資料庫中的資料。 這些和其他檢視中可用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]節點[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管理主控台。  
  
|追蹤檢視|data|  
|-------------------|----------|  
|bam_Process_AllInstances|PIP 定義的 RosettaNet 程序狀態|  
|bam_Message_AllInstances|所有訊息的狀態|  
|bam_Process_CompletedInstances|已完成程序的狀態|  
  
 訊息活動會將訊息內容儲存於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive 資料庫的 MessageContent 資料表。 若要查看內容，您可以使用訊息的唯一識別碼，對 MessageContent 資料表執行查詢。 活動會將唯一識別碼儲存於訊息活動追蹤資料表 (前置詞為 "bam_Message") 的 ContentKey 資料行中。  
  
> [!IMPORTANT]
>  訊息活動會在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive 資料庫的 MessageContent 資料表中以純文字共用訊息內容。 在所有追蹤實例中都是如此，包括已加密或簽署的訊息在內。 如果您擔心他人存取訊息內容，可以對 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive 資料庫設定存取限制。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 使用 BAM 追蹤 API 儲存追蹤資料。  
  
### <a name="status-codes"></a>狀態碼  
 BAMPrimaryImport 資料庫中的 bam_Process_Active 和 bam_Process_Completed 資料表包括了表示程序狀態的 Status 資料行。 下表顯示各種狀態碼的值。  
  
|狀態碼|程序狀態|  
|-----------------|-------------------|  
|-1000|ActivityNotPresentFatalError|  
|-500|UnexpectedFatalError|  
|-100|Initiated0A1|  
|-99|TerminatedOnError<br /> （任何其他終止由 0A1）|  
|-85|TerminatedBy0A1|  
|-75|TimedOutOnResponseSignal|  
|-50|TimedOutOnResponse|  
|-25|TimedOutOnActionSignal|  
|0|RegisteredActivity|  
|1|ActivityToBeInitiated|  
|10|ReceivedAction 或 SentAction|  
|25|ReceivedActionSignal 或 SentActionSignal|  
|35|ReceivedActionSignal2 或 SentActionSignal2<br /> （訊號 2 適用於 RNIF v11）|  
|50|ReceivedResponse 或 SentResponse|  
|75|ReceivedResponseSignal 或 SentResponseSignal|  
|85|ReceivedResponseSignal2 或 SentResponseSignal2<br /> （訊號 2 適用於 RNIF v11）|  
|100|ActivityCompleted|  
  
### <a name="activity-definition-file"></a>活動定義檔  
 活動定義檔案會定義您在 BAM 中追蹤的欄位以及檢視欄位的方式。 如需有關這個檔案的詳細資訊，請參閱[使用追蹤活動定義檔案](../../adapters-and-accelerators/accelerator-rosettanet/working-with-the-tracking-activity-definition-file.md)。  
  
 如需有關 BAM 的詳細資訊，請參閱 「 商務活動監控 (BAM) 」 在 BizTalk Server 說明中。  
  
## <a name="see-also"></a>請參閱  
 [使用追蹤活動定義檔案](../../adapters-and-accelerators/accelerator-rosettanet/working-with-the-tracking-activity-definition-file.md)   
 [BizTalk Accelerator for RosettaNet 在 BizTalk Server 中新增的項目](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)