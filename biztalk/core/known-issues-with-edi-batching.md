---
title: EDI 批次處理的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 510ac82b-8a02-4135-87b7-0a5f288f5317
caps.latest.revision: 38
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 537a0591ba45a209fd3f22c0a993a99baac58d7f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008215"
---
# <a name="known-issues-with-edi-batching"></a>EDI 批次處理的已知問題
本主題說明中批次處理的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
## <a name="subdocument-splitting-was-not-performed-even-though-the-subdocument-annotation-was-set-to-yes"></a>子文件分割並未執行，即使子文件註解設定為 [是]  
 **徵兆**  
  
 即使該交換之 HIPAA 結構描述內 subdocument_creation_break 註解設定為"Yes"。 不 HIPAA 交換分割成子文件  
  
 **可能的原因**  
  
-   輸入的批次處理選項傳送合作對象已設定為 「 保留交換 」。 HIPAA 文件就不會分割成子文件的情況下，即使 HIPAA 結構描述內 subdocument_creation_break 註解設定為"Yes"。  
  
-   Subdocument_break 註解設定為"Yes"，但未設定為"Yes"subdocument_creation_break 註解。  
  
 **解決方式**  
  
-   在**驗證和通知的產生設定**頁面**EDI 屬性**傳送合作對象 對話方塊設定**輸入批次處理**選項屬性任一**將交換分割為交易集-發生錯誤時暫停交易集**或**將交換分割為交易集-發生錯誤時暫停交換**。  
  
-   除非 subdocument_creation_break 註解設為 [是]，否則 HIPAA 文件不會分割成子文件。  
  
## <a name="validation-of-a-batch-may-fail-if-batch-configuration-settings-are-changed-while-the-batch-orchestration-is-activated"></a>如果在批次協調流程啟動時變更批次組態設定，驗證批次可能會失敗  
 當批次處理協調流程正在處理批次時，如果變更批次組態設定，該批次將不會套用新的組態設定。 這可能會在傳送管線中產生驗證錯誤。  
  
 這些設定位於 [EDI 屬性] 對話方塊的 [批次] 頁面。  
  
 若要解決這個問題，請重新啟動與批次處理協調流程相關的主控件執行個體。 這會讓批次組態設定的變更立即生效。  
  
## <a name="the-batchcontrolmessagerecvloc-receive-location-can-only-run-on-a-32-bit-computer-or-in-wow-on-a-64-bit-computer"></a>BatchControlMessageRecvLoc 接收位置只能在 32 位元電腦或 64 位元電腦上的 WOW 執行  
 SQL 配接器只能在 32 位元電腦或 64 位元電腦的 WOW64 模擬器下運作。 因此，由安裝程式安裝並使用 SQL 配接器的 BatchControlMessageRecvLoc 接收位置也只能在 32 位元電腦或 64 位元電腦的 WOW 下運作。 批次處理需要使用此接收位置。  
  
 在 64 位元電腦上的 WOW 下執行 BatchControlMessageRecvLoc 接收位置時，請在不同的主機中執行批次處理協調流程。 如果與接收位置在同一個主機上執行，則批次處理協調流程也會在 WOW 下執行，那麼就失去了在 64 位元電腦上執行的優勢。  
  
## <a name="a-batch-can-be-picked-up-by-an-unintended-send-port"></a>批次可能會由非指定的傳送埠取用  
 當批次處理協調流程發佈交換時，會升級兩個屬性： ToBeBatched = False 和 DestinationPartyName = \< *PartyName*\>。 訂閱其中一個屬性或兩個屬性都訂閱的傳送埠可以取用這些批次交換。 請確定已設定傳送埠的篩選條件，好讓傳送埠選取應該取用的批次交換。  
  
## <a name="a-batch-element-count-greater-than-the-required-number-of-transaction-sets-for-a-batch-may-not-prompt-batch-release"></a>雖然批次項目計數大於批次所需的交易集數，仍可能不會提示批次釋放  
 如果批次釋放準則是根據群組或交換的交易集數目為基礎，即使批次項目計數大於釋放批次所需的交易集數目，仍可能不會釋放批次。 如果您啟用通知，並設定批次篩選條件準則將這些通知加入批次，就可能會發生這種情況。 在這種情況下，群組 (或交換) 中的批次項目數目將大於群組 (或交換) 的交易集數目。 這時，如果群組 (或交換) 的交易集數目小於批次釋放所需的數目，但同時批次項目數目又可能大於批次釋放所需的交易集數目，那麼將不會釋放批次。  
  
## <a name="no-batch-elements-were-saved-when-start-was-clicked"></a>按一下啟動時沒有儲存任何批次項目  
 **徵兆**  
  
 當**啟動**已按下在合作對象的批次 頁面上，針對批次收集任何訊息。  
  
 **可能的原因**  
  
 日期時間**啟動**已按下早於輸入的日期時間**啟用**> 一節。 如此一來，協調流程執行個體已啟動，但針對批次所收集的任何訊息。 如需詳細資訊，請參閱[設定外寄批次](../core/configuring-an-outgoing-batch.md)。  
  
 **解決方式**  
  
 按一下**停止**的批次組態發生此問題的批次 頁面中。 設定**啟用**為**立即開始**或輸入日期時間早於目前的時間，然後按一下**啟動**。 當系統提示您重設**啟動**日期時間到目前的時間，按一下**確定**。 BizTalk Server 這時便會開始收集批次的訊息。  
  
## <a name="the-number-of-bytes-in-an-edifact-batch-may-depend-upon-the-character-set-used"></a>EDIFACT 批次中的位元組數目可能會視使用的字元集而定  
 某些 EDIFACT 字元集中的字元可能是雙位元組字元，而其他 EDIFACT 字元集中的字元則可能是單一位元組字元。 因此，當您根據交換中的字元數來設定批次的釋放準則時，交換中的位元組數可能會根據使用的字元集而有所不同。  
  
## <a name="the-characters--and--must-be-represented-in-their-encoded-form-in-the-envelope-of-a-batch"></a>字元"<"和"&"必須以批次的信封中的其編碼格式表示  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不支援下列字元常值格式中建立的批次 EDI 交換的信封欄位時:"<"和"&"。  
  
 如果使用 EdiSend 管線序列化交換，則若在外寄批次交換的信封欄位中使用其中任一字元的常值，將會導致訊息遭擱置。  
  
 如果需要在批次的信封欄位中使用上述其中一個字元，當您在「BizTalk 系統管理員」中設定信封欄位時，可以使用下表中經過適當編碼的值：  
  
|字元|編碼方式|  
|---------------|--------------|  
|<|&lt;|  
|&|&amp;|  
  
 當您使用其中一種編碼的形式時，將編碼格式中的每個字元將會計算為個別字元時 BizTalk Server 會驗證其長度的限制 BizTalk Server 中的夥伴協議管理員 (PAM) 螢幕中的欄位管理主控台。 比方說，即使編碼"&lt;"代表單一字元"\<"在批次 EDI 交換，BizTalk Server 將它算成四個字元驗證符合特定欄位的長度限制時. 只有 PAM 才會發生此問題，「EDI 組合器」則無此問題。  
  
## <a name="an-exeption-occurs-during-the-execution-of-the-upgrade-batch-orchestration"></a>升級的批次協調流程的執行期間發生例外狀況  
 **徵兆**  
  
 使用自訂管線元件時，設定 EDI。內送文件上的 DestinationPartyId 屬性，您可能會收到中應用程式事件記錄檔指出，在升級的批次協調流程的執行期間發生例外狀況的錯誤。  
  
 **可能的原因**  
  
 如果 ErrorMessage =「找不到批次」，此錯誤表示升級批次協調流程無法成功識別內送文件的批次。  
  
 **解決方式**  
  
 升級的批次協調流程會使用 EDI。Destinationpartyid 設定為查閱合作對象名稱。 接著使用這個合作對象名稱、EDI.EncodingType 與字串 “Default” 建構一個字串，然後尋找具有相符批次名稱的批次組態。 如果沒有批次組態存在具有這個名稱，應用程式事件記錄檔會記錄此錯誤，協調流程執行個體被擱置。  
  
> [!NOTE]
>  例如，如果合作對象名稱為 Contoso，EDI.EncodingType 為 X12，則協調流程會尋找名為 ‘ContosoX12Default’ 的批次。  
  
 若要解決這個問題，請確認批次存在會符合升級的批次協調流程所建構之字串的名稱。  
  
## <a name="messages-marked-with-editobebatched--true-and-edidestinationparties-are-suspended"></a>標記為 EDI 訊息。ToBeBatched = True 和 EDI。將暫止 DestinationParties  
 **徵兆**  
  
 當使用自訂管線元件來標示藉由設定 EDI 批次處理的訊息。ToBeBatched = True 和 EDI。DestinationParties 給清單中的合作對象的識別碼，將會擱置訊息，與路由失敗，表示沒有任何訂閱者。  
  
 **可能的原因**  
  
 在舊版的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應處理訊息時，由多個批次組態中，您可以將 EDI。DestinationParties 屬性，以空格分隔合作對象識別碼的清單。 路由協調流程會訂閱具有 EDI.ToBeBatched = True 與 EDI.DestinationParties 屬性的訊息，並使用 EDI.DestinationParties 屬性中包含的合作對象識別碼清單為每個識別碼建立訊息，然後將訊息傳遞給批次處理協調流程。  判斷使用合作對象的批次識別碼已使用，因為每個合作對象組態可能會有一個批次組態。  
  
 在 BizTalk Server 中，每個合作對象可以有多個批次組態，因此便不再使用來決定要使用的批次組態的合作對象識別碼。  若要指出多個批次組態必須處理訊息，訊息必須 EDI。Batchid 屬性設定為一個空格分隔批次訊息應傳送至的識別碼的清單。  
  
> [!NOTE]
>  處理訊息加上只有一個合作對象識別碼使用 EDI。DestinationPartyId 屬性升級批次處理協調流程會處理訊息。 如需詳細資訊，請參閱[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。  
  
 **解決方式**  
  
 升級自訂管線元件，以便將 EDI。而不是 EDI Batchid 屬性。DestinationParties。  特定批次的批次識別碼可以在針對每個合作對象的 EDI 屬性 的 批次設定 頁面上找到。  
  
> [!NOTE]
>  如果使用 BatchMarker 管線元件來標示批次處理的訊息，則不會發生這個問題。  
  
## <a name="batch-filter-refresh-timeout-is-hardcoded-to-fifteen-minutes"></a>批次篩選條件重新整理逾時是硬式編碼至 15 分鐘  
 修改時批次篩選條件準則，需要 15 分鐘的時間所做的變更才會生效。 無法修改此重新整理間隔。 若要篩選器會立即生效，請重新啟動 BizTalk Server 主控件程序。  
  
## <a name="the-routingorchestration-suspends-after-reporting-an-uncaught-exception"></a>RoutingOrchestration 會回報無法攔截的例外狀況之後暫停  
 **徵兆**  
  
 在處理文件為目標的多個批次組態時，您可能會收到錯誤的應用程式事件日誌中的 XLANG/s 啟動 Microsoft.BizTalk.Edi.RoutingOrchestration.BatchRoutingService 失敗，因為發生無法攔截例外狀況。  
  
 **可能的原因**  
  
 RoutingOrchestration 嘗試傳送訊息至 BatchingOrchestration 且 BatchingOrchestration 執行個體不會啟動時，會發生此錯誤。  
  
 **解決方式**  
  
 確定 BatchingOrchestration 執行個體正在執行之前送出要批次處理的文件。  
  
## <a name="many-active-batches-may-cause-the-biztalkmsgboxdb-logfile-to-grow-large"></a>許多作用中批次可能會造成 BizTalkMsgBoxDb 記錄檔變得大  
 **徵兆**  
  
 啟動數個批次之後, 您可能會注意到 BizTalk messagebox 資料庫 (BizTalkMsgBoxDb) 的交易記錄檔增長到大型大小。  
  
 **可能的原因**  
  
 如果您有大量的批次釋放準則以啟動，導致批次的版本 （例如，批次釋放每分鐘排定） 之間在短時間內，可能會發生此問題。  
  
 啟動批次時，會建立批次處理協調流程執行個體是長時間執行的程序之後釋放批次中保存到資料庫。 協調流程持續發生，每次交易記錄檔可以成長交易因為參與持續性。  
  
> [!NOTE]
>  批次處理協調流程將會在保存期間在成長大約 30 kb 交易記錄檔。  
  
 **解決方式**  
  
 若要解決這個問題，請修改釋放準則，以增加批次釋放之間的時間。 如需詳細資訊，請參閱[設定批次處理 (X12)](../core/configuring-batching-x12.md)。  
  
## <a name="see-also"></a>請參閱  
 [設定 EDI 通知](../core/configuring-edi-acknowledgments.md)   
 [處理內送的批次](../core/processing-incoming-batches.md)   
 [批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)   
 [設定 EDI 批次](../core/configuring-edi-batches.md)