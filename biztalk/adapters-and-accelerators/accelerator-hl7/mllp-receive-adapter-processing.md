---
title: "MLLP 的接收配接器處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, receive adapters
- MLLP adapters, send adapters
- receive adapters
ms.assetid: 03c9a5f6-6f23-454f-8bab-e7c7b6057efa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28713e22c37c12ef6f2cb9f8df8d228759d00c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mllp-receive-adapter-processing"></a>MLLP 的接收配接器處理
最小的較低層通訊協定 (MLLP) 接收配接器支援這兩個單向和雙向要求回應模式。 配接器會接聽並接受連線。  
  
 當 MLLP 的接收配接器仍會雙向模式運作，配接器不會收到一封新郵件來自連接直到管線已產生通知 (ACK) 的前一個訊息。  
  
## <a name="configuration-parameters"></a>組態參數  
 接收處理常式的參數在 BizTalk 主控件層級設定，而且適用於所有與它相關聯的 MLLP 接收位置。  
  
|參數|使用|  
|---------------|---------|  
|*最大接受連線限制*|限制並行接收配接器將會接受的開啟連接數目。|  
  
## <a name="acknowledgments-with-the-two-way-mllp-receive-adapter"></a>與雙向 MLLP 通知接收配接器  
 當收到雙向 MLLP 配接器接收訊息時， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 可以產生下列類型的通知：  
  
-   HL7 增強認可 ACK： 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送相同的連接上認可的通知。 它會送出不同的傳送埠上的應用程式接受通知。  
  
-   應用程式接受 ACK： 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送相同的連接上的應用程式接受通知。  
  
-   靜態 ACK: 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]相同的連接上傳送的通知。  
  
-   產生的通知類型取決於[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管設定之合作對象傳送訊息。 值欄位 MSH 15 16 個別訊息可以覆寫此設定。 不過，對於應用程式必須是靜態的 Ack，組態可以只能透過設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。  
  
## <a name="error-conditions"></a>錯誤狀況  
 錯誤狀況或非使用狀態時，就會發生下列事件：  
  
-   如果已停用接收位置或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]關閉，則發生下列情況：  
  
    -   接收位置不再接受新連線。  
  
    -   對於現有的連線，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]完全接收目前的訊息，並關閉連線。  
  
-   偵測到無活動時 （在指定的逾時時間內接收位置接收到沒有承載資料），配接器關閉連接。  
  
-   如果[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]收到不完整的訊息時，收到的部分會暫停。 收到的訊息 （之前在新的連接，EB/CR 和 SB 的下一個訊息之間的第一個 SB) 之外的所有位元組都會被都忽略。  
  
-   如果管線無法剖析訊息，訊息仍會傳遞至 MessageBox 資料庫，與升級屬性**ParseError = true**。  
  
-   如果訊息失敗，因為沒有訂用帳戶，或因結構錯誤，在頁首中，而[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]擱置訊息的原始 「 纜線 」 形式 （如果之前正在剖析）。 否-訂用帳戶失敗的常見原因是缺少的升級屬性。 因為[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]擱置未剖析的訊息， **BTS。MessageType**會是空白。  
  
 下表列出 MLLP 的接收配接器傳回的錯誤。  
  
|事件|ID|錯誤狀況|  
|-----------|--------|---------------------|  
|**ErrorListening**|8448|無法繫結到本機通訊端 （可能有其他本機應用程式正在使用相同的 IP 位址/連接埠編號組合）。|  
|**ErrorAcceptingConnection**|8449|無法建立與遠端合作對象的 TCP 連接。 任一[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]達到最大連接，或資源不足。|  
|**ErrorSubmittingMessage**|8452|MessageBox 資料庫無法接受訊息。 任一[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]已無法使用或資源不足。|  
|**ErrorSendingAck**|8454|[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]無法傳回通知，因為連線無法使用。|  
  
## <a name="performance-counters"></a>效能計數器  
 下表列出 MLLP 配接器會使用效能計數器。  
  
|計數器|意義|  
|-------------|-------------|  
|Bytes|所有文件接收或傳送的裝載大小。|  
|位元組數/秒|目前裝載接收或傳送的輸送量。|  
|處理文件數|**MLLP 接收**:<br /><br /> 已成功傳送到 MessageBox 資料庫的文件數。<br /><br /> **MLLP 傳送**:<br /><br /> 已成功傳送到遠端應用程式的文件數。|  
|失敗的文件|**MLLP 接收**:<br /><br /> 未成功傳遞到 MessageBox 資料庫的文件數目。<br /><br /> **MLLP 傳送**:<br /><br /> 未成功傳遞到遠端應用程式的文件數目。|  
|連線狀態|配接器連線，狀態 1 或 0 (1 = 連接)。|  
  
 效能計數器執行個體使用下列命名結構：  
  
```  
{recv|trans} : connection name : remote IP address : remote port ID  
```  
  
 MLLP 的接收配接器使用的 「 接收 」 前置詞，並 MLLP 傳送配接器會使用 「 交易 」。  
  
> [!NOTE]
>  認可傳送的接收埠 （例如，配接器在雙向模式中操作），並傳送連接埠 （可以接收相同的通訊端連線的 Ack 運作） 都不會計入。  
  
## <a name="see-also"></a>另請參閱  
 [處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [組態參數傳送和接收配接器](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [MLLP 傳送配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [設定傳送埠來接收通知](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)