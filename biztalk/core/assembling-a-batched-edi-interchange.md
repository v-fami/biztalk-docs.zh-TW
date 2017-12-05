---
title: "組合批次的 EDI 交換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18f64595-935e-4d52-9ec2-5edf7c2b9e83
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c4274362e5ec8441e203d0b2b97f27e95235fd9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="assembling-a-batched-edi-interchange"></a>組合批次 EDI 交換
若要將個別的交易集批次元素組合成 EDI 交換， [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 和 AS2 會進行下列作業：  
  
-   識別用於批次處理的批次元素  
  
-   在收到批次元素時個別進行驗證及緩衝處理  
  
-   擷取特定批次項目，並將批次的交換的組合，符合釋放準則時  
  
 個別訊息集合組合成批次的開始時間是由批次啟動準則所決定， 而釋放批次的時間則是由批次釋放準則所決定。 如需這兩個集合的準則的詳細資訊，請參閱[設定外寄批次](../core/configuring-an-outgoing-batch.md)。  
  
## <a name="message-flow-for-outgoing-batched-messages"></a>外寄批次訊息的訊息流程  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定為批次處理外送訊息時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件將會執行一系列如下的步驟，以準備傳送批次的訊息。 這一系列步驟說明的案例是以具有 BatchMarker 管線元件的 EDIReceive 管線來處理收到的交換，而這些交換中包含要進行批次處理以供傳送的交易集。  
  
1.  EDIReceive 管線中的 BatchMarker 管線元件會透過合作對象屬性的 EDI 批次篩選條件設定，判斷需要進行批次處理的訊息 (這是唯一可查看批次篩選條件設定並根據這些設定運作的批次處理元件)。  
  
2.  如果只有一個批次組態的篩選設定訂閱了訊息，BatchMarker 元件將會升級 `EDI.ToBeBatched = True` 屬性。 這可確保批次處理或協調流程一定會收取訊息。  
  
3.  如果多個批次組態的篩選設定符合訊息的內容，BatchMarker 元件會升級屬性`EDI.ToBeRouted = True`並設定`EDI.BatchIds`屬性，以空格分隔清單，其中包含相符的批次識別碼。  這可確保路由或協調流程一定會訂閱訊息。  
  
    > [!NOTE]
    >  您可以升級自訂接收管線或自訂協調流程中適當的內容屬性。 自訂接收管線可以使用 BatchMarker 管線元件，或是不使用 BatchMarker 管線元件，直接升級屬性。  
  
4.  路由協調流程才能收取任何交易集的`EDI.ToBeRouted = True`和`EDI.BatchIds`升級，而且接著會建立交易集，確保識別碼包含在每個批次的副本份`EDI.BatchIds`。 路由協調流程設定`EDI.ToBeBatched = True`和`EDI.BatchId`設為相符批次設定針對每個複本的交易集的批次識別碼。 這可確保批次處理協調流程將會收取交易集以進行批次處理。  
  
5.  批次處理協調流程會收取已升級下列屬性的所有訊息：  
  
    -   `EDI.ToBeBatched = True`和 EDI。批次識別碼 = 批次處理協調流程的這個執行個體相關聯的批次的批次識別碼。  
  
    -   `EDI.ToBeBatched = True`和 EDI。BatchName = 設定批次和 EDI 的名稱。DestinationPartyName = 包含批次組態的合作對象名稱。  
  
     當 EDIReceive 管線處理內送訊息 (使用 BatchMarker 管線元件) 時，批次處理協調流程只會批次處理 X12 或 EDIFACT 編碼的交易集。  
  
    > [!NOTE]
    >  每個作用中批次組態都有一個批次處理協調流程執行個體，而且每個執行個體都會訂閱特定批次識別碼。 當建立新的批次組態中的批次識別碼值會自動設定**識別**區段**批次組態**單向協議索引標籤的頁面**協議屬性** 對話方塊。  
  
6.  批次處理協調流程會驗證要批次處理的每個交易集。 如果交易集驗證失敗，它會設定`EDI.BatchItemValidationFailure`內容屬性為"True"。 **BatchSuspend**協調流程收取該內容屬性為基礎的訊息、 發佈錯誤資訊，和再擱置訊息。  
  
7.  當已符合批次釋放準則時，批次處理協調流程會將批次元素組合成一個批次，並建立信封。  
  
8.  批次處理協調流程完成交換的批次處理後，它會升級該交換上的下列屬性： EDI。DestinationPartyName = %partyname%EDI。BatchEncodingType = X12 或 EDIFACT，以及 EDI。ToBeBatched = False。  
  
9. 傳送埠會拾取 EDI 為基礎的批次的交易集。DestinationPartyName = \<PartyName\>，EDI。BatchEncodingType = EDIFACT 或 X12，以及 EDI。ToBeBatched = False。  
  
## <a name="batching-orchestration-control-messages"></a>批次處理協調流程控制訊息  
 批次處理協調流程由下列控制訊息啟動、終止或覆寫：  
  
-   **BatchActivation**： 當協調流程收到這個訊息，會建立批次處理協調流程執行個體，而且協調流程作用狀態以便接收批次元素 （其是否符合批次啟動準則）。 按一下 [傳送這個控制訊息**啟動**按鈕上的批次組態的**批次組態**單向協議索引標籤的頁面**協議屬性** ] 對話方塊。  
  
-   **BatchTermination**： 當協調流程收到這個訊息時，從現有的批次元素建立批次、 將訊息發佈至 MessageBox，並終止。 按一下 [傳送這個控制訊息**停止**按鈕上的批次組態的**批次組態**單向協議索引標籤的頁面**協議屬性** ] 對話方塊。  
  
    > [!NOTE]
    >  如果在達到指定的時間內，也會終止協調流程**結尾所**屬性**終止**區段**批次組態**頁面單向協議索引標籤**協議屬性** 對話方塊。  
  
-   **BatchOverride**： 協調流程收到這個訊息時，它從現有的項目建立批次、 將訊息發佈至 MessageBox，，然後等候下一個批次的訊息。 按一下 [傳送這個控制訊息**覆寫**按鈕上的批次組態的**批次組態**單向協議索引標籤的頁面**協議屬性** ] 對話方塊。  
  
 批次處理協調流程會透過 BatchControlMessageRecvLoc 接收位置接收控制訊息。 這個 SQL 接收位置的輪詢間隔預設為 30 秒，但是可以變更在**SQL 傳輸屬性**接收位置 對話方塊。 縮短輪詢間隔可確保在您執行傳送控制訊息的動作之後 (例如在您啟動批次處理協調流程時)，BatchControlMessageRecvLoc 接收位置可以立即收到控制訊息。  
  
 啟動批次協調流程時執行的步驟如下：  
  
1.  當您按一下**啟動** 按鈕，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會指出您要啟用的批次協調流程的合作對象和批次識別碼的表格建立記錄。  
  
2.  與 BatchControlMessageRecvLoc 接收位置關聯的 SQL 配接器會進行輪詢，確定資料庫中是否有該筆記錄。  
  
3.  如果記錄存在，SQL 配接器會使用記錄中的資訊建置控制訊息。  
  
    > [!NOTE]
    >  以這種方式建置訊息可確保無效的控制訊息將無法啟動協調流程。  
  
4.  BatchControlMessageRecvLoc 接收位置接收控制訊息，和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]啟動批次處理協調流程執行個體。  
  
## <a name="batch-components"></a>批次元件  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 批次處理成 EDI 交換，使用下列元件的 XML 交易集：  
  
-   EDI 接收管線中的 BatchMarkerReceivePipelineComponent  
  
-   路由協調流程  
  
-   批次處理協調流程  
  
-   升級批次處理協調流程  
  
-   BatchSuspend 協調流程  
  
-   EDI 傳送管線  
  
 當您安裝並設定這些元件都會安裝成 Dll [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 和 AS2。  
  
> [!NOTE]
>  中的批次處理元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 和 AS2 不保證批次中交易的順序設定。  
  
### <a name="batchmarkerreceivepipelinecomponent"></a>BatchMarkerReceivePipelineComponent  
 EDI 接收管線中的 BatchMarkerReceivePipelineComponent 可讓批次處理協調流程收取要批次處理的訊息。 這個管線元件是在 EDI 接收管線中的解譯器之後套用。 這個元件會評估設定的篩選準則**篩選**區段**批次組態**單向協議索引標籤的頁面**協議屬性**對話方塊中，並標示交易集與下列內容屬性來處理路由和批次處理協調流程  
  
-   如果單一合作對象訂閱要批次處理的訊息，它會升級 `ToBeBatched = True`，而且 BatchId 會設定為相符批次組態之批次識別碼的值。 這可讓批次處理協調流程收取訊息。  
  
-   如果多個批次訂閱要批次處理的訊息，它會升級`ToBeRouted = True`，並設定`EDI.BatchIds`屬性設定為以空格分隔批次識別碼的清單。 這啟用路由協調流程收取。  
  
-   如果沒有任何訂閱存在，它就不會升級內容屬性。 這表示交易集不會進行批次處理。  
  
 管線元件會忽略 XML 以外的訊息，並使用訊息`ReuseEnvelope`（保留批次） 的屬性。 如果不要對通知進行批次處理，此管線元件便會忽略 ACK 訊息類型 (CONTRL、TA1 和 997)。 為了讓路由和批次處理協調流程達到最佳效果，如果解譯器將訊息內容屬性 `MessageDestination` 設定為 "SuspendedQueue"，BatchMarkerPipelineComponent 便會將訊息傳遞到 MessageBox。  
  
 如果您使用的是自訂管線，而不是 EDIReceive 管線，可以使用自訂管線中的 BatchMarker 元件。 如果您不是使用 EDIReceive 管線，而且要從協調流程發佈訊息，則必須升級 `ToBeBatched = True` 並將 `BatchID` 設定為其中一個元件內作用中批次的識別碼。  
  
### <a name="routing-orchestration"></a>路由協調流程  
 路由協調流程會訂閱具有內容屬性 `ToBeRouted = True`，並將內容屬性 `EDI.BatchIds` 設定為批次識別碼之空格分隔清單的任何訊息。 會發生這種情況是當多個批次篩選條件訂閱要批次處理的訊息。 路由協調流程會針對 `EDI.BatchIds` 中包含的每個批次識別碼建立訊息的複本。 加上戳記每個複本的兩個新的內容屬性：  
  
-   `EDI.BatchID`會設定為僅供這則訊息批次的識別碼。  
  
-   `EDI.ToBeBatched`會設定為 True。  
  
 接著，它會將這些複本傳送到 MessageBox，供批次處理協調流程收取。 每個目的地的批次識別碼將相同的協調流程的單一執行個體使用特定批次識別碼的篩選  
  
### <a name="batching-orchestration"></a>批次處理協調流程  
 批次處理協調流程是一種可設定狀態的服務，它會緩衝一段時間內的批次元素 (交易集)、將它們組合成交換，然後再根據釋放準則將交換釋放到傳送管線。  
  
 之後啟動批次處理協調流程執行個體可以開始批次處理到指定的合作對象的特定編碼類型的訊息 (如果**啟動**經過 datetime)。 在任何一個時間點，每個合作對象的批次處理協調流程可以具有許多執行個體，但是每個作用中批次組態只能有一個執行個體。 批次處理協調流程的單一執行個體可以發行單一批次組態的多個批次。 在符合結束準則後，批次處理協調流程執行個體將會終止。 批次處理協調流程的新執行個體必須以手動方式建立交易夥伴管理 (TPM) 從使用**啟動** 按鈕。  
  
 如果批次協調流程啟動之前顯示的開始日期時間中**啟用**區段的**批次組態**單向協議索引標籤的頁面**協議屬性**對話方塊中，它只會接收啟動範圍中指定的訊息。 不會接收在開始日期時間之前傳送的訊息。  
  
 批次處理協調流程執行的作業包括：  
  
-   訂閱具有下列內容屬性的 XML 批次元素：`EDI.ToBeBatched = True` 以及 `EDI.BatchId` = 批次組態識別碼，或是 `EDI.ToBeBatched = True`、EDI.BatchName = 已設定批次的名稱，以及 EDI.DestinationPartyName = 包含批次組態的合作對象名稱。 它會接收批次項目使用**接收**動作在迴圈中的作業。  
  
    > [!NOTE]
    >  批次處理協調流程不會批次處理的篩選區段中設定的篩選準則為基礎的交易集**批次組態**單向協議索引標籤的頁面**協議屬性**  對話方塊。 它會訂閱已設定前述內容屬性的交易集。 BatchMarker 管線元件會根據合作對象屬性中的篩選設定來設定及升級這些內容屬性。  
  
-   擷取中所識別的合作對象的批次組態設定`BatchId`內容屬性。  
  
-   根據合作對象設定來驗證批次元素 (交易集)。  
  
-   如果批次項目中有錯誤，批次處理協調流程將會升級該交易集的下列屬性： `EDI.BatchItemValidationFailure = True`。 **BatchElementSuspend**協調流程會訂閱設定已升級這個屬性的任何交易。 這個協調流程將會提供在批次處理交換時所遇到的第一個錯誤。  
  
-   如果批次元素中沒有任何錯誤，則保留該批次元素的參考。  
  
-   當收到適當的控制訊息或符合批次處理釋放準則時，中斷**接收**動作 」 迴圈、 從 MessageBox 擷取所有批次元素並組合交換。  
  
-   將內容屬性設定`ToBeBatched = False`針對交換和內容屬性 DestinationPartyName = %partyname%其中 %partyname%是訊息適用之合作對象名稱。  
  
    > [!NOTE]
    >  如果傳送埠訂閱一個或兩個屬性`EDI.ToBeBatched = False`和 EDI。DestinationPartyName = %partyname%、 傳送埠可以收取批次交換。 請確定傳送埠的篩選條件已設定成讓傳送埠只收取它應該收取的批次交換。  
  
    > [!NOTE]
    >  批次處理協調流程放入 MessageBox 中的交換必須只有屬性`EDI.ToBeBatched = False`，EDI。DestinationPartyName = %partyname%以及 EDI。BatchEncodingType ="X12"或"EDIFACT"升級至內容。 原始交易集裡的所有內容屬性都會遺失。  
  
-   針對 X12 編碼的交換，將下列屬性套用到信封：  
  
    -   ISA6： 交換傳送者識別碼  
  
    -   ISA8： 交換接收者識別碼  
  
    -   ISA15：使用狀況指示符號  
  
    -   ISA_Blob (寫入內容中)  
  
-   針對 EDIFACT 編碼的交換，將下列屬性套用到信封：  
  
    -   UNB2.1：交換傳送者識別碼  
  
    -   UNB3.1：交換收件者識別碼  
  
    -   UNB2.3：反向路由的位址  
  
    -   UNB11：使用狀況指示符號  
  
    -   UNA_Blob (寫入內容中)  
  
    -   UNB_Blob (寫入內容中)  
  
-   將批次交換傳送至 MessageBox，供 EDI 傳送管線收取。  
  
### <a name="upgradebatching-orchestration"></a>UpgradeBatching 協調流程  
 UpgradeBatching 協調流程會處理將 `EDI.ToBeBatched` 屬性設定為 true，但是沒有設定 `EDI.BatchID` 屬性的訊息。  
  
 在舊版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，每個合作對象都只能有一個批次組態。  處理將 `EDI.ToBeBatched` 設定為 true 的訊息時，`EDI.DestinationPartyId` 就會用來判斷合作對象，然後從協議屬性中讀取批次組態。  
  
 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，每個合作對象可以有多個批次組態相關聯，所以`EDI.DestinationPartyId`不提供足夠的資訊來決定應使用哪一個批次組態。  當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收訊息，`EDI.BatchId`屬性用來識別處理訊息時，就應該使用哪一個特定批次組態。  
  
 升級到之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可能仍有使用的自訂管線`EDI.DestinationPartyId`以指定的合作對象組態屬性。 當收到的訊息具有`EDI.ToBeBatched`設為 true，且具有`EDI.DestinationPartyID`而不是 EDI 設定。批次識別碼，UpgradeBatching 協調流程會嘗試決定應使用哪一個批次組態。  
  
 UpgradeBatching 協調流程會使用下列訂用帳戶篩選來訂閱被標示為要批次處理，但不是指定批次識別碼的文件：  
  
-   `EDI.ToBeBatched=True`  
  
-   `EDI.EncodingType`存在  
  
-   `EDI.DestinationPartyId`存在  
  
 當協調流程接收訊息時，它會嘗試尋找相符的批次組態訊息所使用的合作對象名稱和編碼類型。  `EDI.DestinationPartyID`屬性用來判斷合作對象名稱，以及協調流程接著會尋找符合批次名稱\<PartyName\>+\<EncodingType\>+ 預設值。  例如，如果合作對象名稱是 Contoso，且值`EDI.EncodingType`為 X12，則協調流程會尋找名為 ContosoX12Default 批次。  
  
 如果找到相符的批次組態，訊息會放入訊息方塊具有下列屬性：  
  
-   `EDI.ToBeBatched = True`  
  
-   `EDI.ToBeRouted = False`  
  
-   EDI。批次識別碼 = 相符的批次的批次識別碼  
  
 批次處理協調流程接著會處理訊息  
  
> [!NOTE]
>  如果找到相符的批次，則會發生下列：  
>   
>  -   將訊息傳送至 BatchSuspend 協調流程。  
> -   UpgradeBatching 協調流程執行個體和訊息將遭擱置。  
> -   錯誤會記錄到事件記錄檔指出找不到批次。  
  
### <a name="batchsuspend-orchestration"></a>BatchSuspend 協調流程  
 BatchSuspend 協調流程可處理批次處理協調流程所收到的無效訊息。 BatchSuspend 是必要的協調流程，因為沒有任何方法可以直接從協調流程 (在此案例中為批次處理協調流程) 擱置訊息，而不需要停止執行協調流程執行個體。  
  
 當批次處理協調流程的執行個體收到訊息時，它會嘗試驗證該訊息。 如果訊息驗證失敗，批次處理協調流程便會建立 BatchSuspend 協調流程的執行個體，並將 `EDI.BatchItemValidationFailure` 內容屬性設定為 True。 BatchSuspend 協調流程訂閱與該內容屬性設定為 True 的所有訊息。 在將無效的交易集傳送至 BatchSuspend 協調流程之後，BatchSuspend 協調流程執行個體便會擱置。  
  
 BatchSuspend 協調流程會提供遇到的第一個錯誤的詳細錯誤資訊。  
  
 您可以建立自訂協調流程，利用篩選條件中的 `EDI.BatchElementValidationFailure` 屬性，依據批次處理協調流程來處理驗證失敗的交易集。  
  
### <a name="edi-send-pipeline"></a>EDI 傳送管線  
 從批次處理協調流程接收批次交換之後，EDI 傳送管線會執行下列動作：  
  
-   針對 X12 編碼的交換，傳送管線會將下列屬性套用到信封：  
  
    -   ISA2：授權資訊  
  
    -   ISA4： 安全性資訊  
  
    -   ISA9： 交換日期  
  
    -   ISA10： 交換時間  
  
    -   ISA13： 交換控制編號  
  
    -   GS4： 日期  
  
    -   GS5： 時間  
  
    -   GS6： 群組控制編號  
  
    -   ST2： 交易集控制編號  
  
-   針對 EDIFACT 編碼的交換，傳送管線會將下列屬性套用到信封：  
  
    -   UNB4.1： 日期  
  
    -   UNB4.2：時間  
  
    -   UNB5：交換控制參考  
  
    -   UNB6.1：收件者參考密碼  
  
    -   UNG4.1：日期  
  
    -   UNG4.2：時間  
  
    -   UNG5：功能群組參考  
  
    -   UNG8：應用程式密碼  
  
-   透過關聯配接器傳遞訊息  
  
## <a name="see-also"></a>請參閱  
 [批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)