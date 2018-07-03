---
title: 依序傳遞訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backing up, message order
- file transport, message order
- Messaging Engine, transports
- messages, performance
- dynamic send ports, message order
- BTS.SuspendAsNonResumable message context property
- performance, message order
- Messaging Engine, performance
- Messaging Engine, message order
- MessageBox database, message order
- messages, sorting
- backing up, backup transports
- adapters, custom receive adapters
- adapters, messages
- customizing, receive adapters
ms.assetid: 39e0bba6-81f5-4ae0-af92-837b225bc801
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52798c5f34c1f436d5c55954f61c6e18fcb2a398
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013015"
---
# <a name="ordered-delivery-of-messages"></a>訊息的排序傳遞
訊息的排序傳遞可確保以指定順序發佈至 MessageBox 資料庫的訊息是以與發佈至 MessageBox 的相同順序傳遞給每一個相符的訂閱者。  
  
## <a name="configuring-ordered-message-delivery"></a>設定訊息的排序傳遞  
 可在下列位置設定訊息的排序傳遞：  
  
-   **接收**協調流程中的圖形  
  
-   傳送埠  
  
## <a name="ordered-delivery-with-existing-transports"></a>具備現有傳輸的排序傳遞  
 在特定傳輸之下的通訊協定，像是 FILE 和 HTTP，與排序傳遞的概念並不一致。 不過，即使具備這類傳輸，若與傳輸繫結的連接埠標示為排序的傳遞，則 BizTalk Server 會藉由保證除非已成功傳送目前的輸出訊息，否則傳輸不會取得下一個輸出訊息，以強制排序的傳遞。 BizTalk Server 執行這項工作的方法是將每個訊息以單一批次傳遞給傳輸的配接器，並等待配接器成功從 MessageBox 刪除訊息後，再以另一個批次傳遞下一個訊息給配接器。  
  
### <a name="ordered-delivery-for-custom-adapters"></a>自訂配接器的排序傳遞  
 自訂接收配接器有一些特殊的考量。 若您正在撰寫可支援接收時排序傳遞的自訂配接器，則配接器應執行下列動作：  
  
- 提交訊息批次之後, 您的自訂接收配接器應該等待**BatchComplete**從 BizTalk Server 才能提交下一個批次的回呼。 如需詳細資訊，請參閱 < [Batch-Supported 接收配接器介面](../core/interfaces-for-a-batch-supported-receive-adapter.md)。  
  
- 若訊息在管線中失敗，應該被擱置，最好標示為不可繼續。 使用**BTS。SuspendAsNonResumable**訊息中的內容屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]適當地加上旗標的訊息。  
  
> [!NOTE]
>  若在稍後繼續擱置的訊息，則會中斷訊息順序。 若您不希望中斷順序，請擱置失敗的訊息並設為不可繼續。  
  
 如需建置自訂的配接器的詳細資訊，請參閱 <<c0> [ 開發自訂配接器](../core/developing-custom-adapters.md)。  
  
## <a name="conditions-for-end-to-end-ordered-message-processing"></a>端對端排序訊息處理的條件  
 若要提供端對端排序的傳遞，必須符合下列條件：  
  
- 必須以保留提交訊息給 BizTalk Server 的訊息順序之配接器接收訊息。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，這類配接器的範例包括 MSMQ 和 MQSeries。 此外，HTTP 或 SOAP 配接器可以用來提交訊息順序，但在此情況下 HTTP 或 SOAP 用戶端必須強制執行一次提交一個訊息的順序。  
  
- 您必須訂閱這些訊息與傳送埠具有**排序的傳遞**選項設定為`True`。  
  
- 如果應該使用的訊息，協調流程中的單一執行個體的程序來協調流程，協調流程應該設定為使用循序群組中，而**排序的傳遞**屬性協調流程的接收埠應該設定為`True`。  
  
## <a name="restrictions"></a>限制  
 下列各項不支援訊息的排序傳遞：  
  
- 動態傳送埠中[!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]與更舊版本

- 動態傳送連接埠[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]（和任何較新版本） 這些配接器類型**不**靜態傳送埠上的排序傳遞的支援
  
- 備份傳輸  

  
## <a name="interactions"></a>互動  
 當傳送埠設定為排序的傳遞時，請注意與 BizTalk Server 中其他設定的行為之下列互動：  
  
-   相同傳送埠上的 [目前訊息失敗之後停止傳送後續訊息] 設定：  
  
    -   **值為 false。** 只會擱置失敗的訊息 (不可繼續) 並繼續處理所有後續訊息。 這會保留未失敗訊息的順序，但會造成順序的間斷。 例如，若收到順序 101、102 和 103，並擱置順序 102，則繼續依序處理順序 101 和 103。  
  
    -   **則為 true。** 若任何訊息處理失敗，則擱置傳送埠執行個體。 這會造成訊息排序集合中的所有後續訊息被擱置。 這是藉由在失敗的訊息傳遞之前，防止後續訊息的傳遞，以保留訊息順序。  
  
-   若請求-回應傳送埠將 [目前訊息失敗之後停止傳送後續訊息] 屬性設定為 `true`，且回應的接收管線之解譯階段已設定為可復原交換處理，則在解譯回應中發生可復原的錯誤時，傳送埠不會停止傳送訊息 (也就是說，不會擱置執行個體)。  
  
-   刪除排序的傳送埠之前，請確定沒有與其相關聯的執行個體。 若有相關聯的執行個體，應該在刪除傳送埠之前先終止它們。  
  
## <a name="ordered-delivery-to-file-transport"></a>檔案傳輸的排序傳遞  
 訊息依序到達 FILE 配接器。 FILE 配接器可能附加訊息到單一檔案或寫出檔案順序，結果如下：  
  
-   若訊息資料附加到單一檔案，則依序附加個別訊息。 在傳送埠上使用 FILE 配接器進行依序傳遞的選項，只有在傳送埠可在附加模式下作用時才有意義。  
  
-   若訊息寫入個別檔案，則依序命名的檔案名稱可反映順序。 在此情況下，若是由配接器寫入的檔案，則與時間相關的檔案系統屬性 (例如，檔案建立時間或修改時間) 不一定要反映訊息到達的順序。  
  
## <a name="performance-impact-of-ordered-delivery"></a>排序傳遞的效能影響  
 為執行排序的傳遞，BizTalk Server 必須在訊息路徑上的不同點序列化處理排序的訊息。 這是藉由向外延展的技術達成，像是使用多個主控件執行個體以供平行處理訊息。 使用排序的傳遞時，即使連接埠設定為在多個主控件執行個體上執行，仍然只在單一主控件執行個體上執行，以確保排序的傳遞。 不過，在此情況下，還是可以維持高可用性，因為處理訊息的排序傳遞之主控件執行個體的失敗，會使得失敗的訊息在另一個可用的主控件執行個體上重新處理。  
  
 啟用排序的傳遞時，預設值**重試間隔**為 5 分鐘。 若要改善效能，設定的重試間隔的最小的值，也就是 1 分鐘。 **重試間隔**屬性可接受值為零 (0)，但零 (0) 無效。 **重試計數**也可以微調以所需的重試次數。 例如，如果您知道要求應該處理中 < 1 分鐘到傳送埠目的地一律可以存取，這兩個值設為 1。  
  
 若要變更的重試值，請前往[如何設定傳輸進階選項的傳送埠](http://go.microsoft.com/fwlink/p/?LinkID=267697)。  
  
 如需其他有關排序的傳遞的詳細資訊，請參閱下列：  
  
 [BizTalk： 端對端排序訊息處理選項](http://social.technet.microsoft.com/wiki/contents/articles/12887.biztalk-end-to-end-ordered-message-processing-options.aspx)  
  
 [BizTalk： 排序的傳遞](http://social.technet.microsoft.com/wiki/contents/articles/6681.biztalk-ordered-delivery.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [依序傳遞訊息與 MSMQ 配接器](../core/ordered-delivery-of-messages-with-the-msmq-adapter.md)   
 [使用 MQSeries 配接器依序傳遞訊息](../core/ordered-delivery-of-messages-with-the-mqseries-adapter.md)