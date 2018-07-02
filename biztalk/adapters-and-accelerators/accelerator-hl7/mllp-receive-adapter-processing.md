---
title: MLLP 接收配接器處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, receive adapters
- MLLP adapters, send adapters
- receive adapters
ms.assetid: 03c9a5f6-6f23-454f-8bab-e7c7b6057efa
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbb5932d65bce2b17ebfca3645b8c755549b9a9c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968135"
---
# <a name="mllp-receive-adapter-processing"></a>MLLP 接收配接器處理
最小的較低層通訊協定 (MLLP) 接收配接器支援這兩個單向和雙向要求回應模式。 配接器會接聽，並接受連線。  
  
 當 MLLP 接收配接器在雙向的模式下運作，配接器將不會收到一封新郵件連接直到管線已產生通知 (ACK) （如先前的訊息。  
  
## <a name="configuration-parameters"></a>組態參數  
 接收處理常式的參數在 BizTalk 主控件層級設定，並套用至與它相關聯的所有 MLLP 接收位置。  
  
|參數|使用|  
|---------------|---------|  
|*最大可接受的連線限制*|接收配接器會接受同時開啟的連線數目限制。|  
  
## <a name="acknowledgments-with-the-two-way-mllp-receive-adapter"></a>通知使用雙向 MLLP 接收配接器  
 當雙向 MLLP 接收配接器接收訊息時，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 可以產生下列類型的通知：  
  
- HL7 增強認可通知： 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]相同的連接上傳送認可的通知。 它會送出不同的傳送埠上的應用程式接受通知。  
  
- 應用程式接受通知： 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送相同的連接上的應用程式接受通知。  
  
- 靜態通知： 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]相同的連接上傳送通知。  
  
- 產生的通知類型取決於[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管設定的合作對象傳送訊息。 在欄位 MSH 15 和 16 個別訊息的值可以覆寫此設定。 不過，對於必須是靜態的 Ack 時，應用程式，設定只能設定透過[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。  
  
## <a name="error-conditions"></a>錯誤狀況  
 錯誤條件或無活動時，就會發生下列事件：  
  
- 如果已停用接收位置或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]關閉，會發生下列情況：  
  
  - 接收位置不再接受新連線。  
  
  - 對於現有的連線，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]完全接收 目前的訊息，並再關閉連線。  
  
- 偵測到非使用狀態時 （在指定的逾時時間內接收位置接收到沒有承載資料），配接器會關閉連線。  
  
- 如果[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]收到未完成訊息時，暫停接收到的部分。 收到一則訊息 （在之前針對新的連接，EB/CR 和 SB 的下一個訊息之間的第一個 SB) 以外的所有位元組會被都忽略。  
  
- 如果管線無法剖析訊息，訊息仍然會被傳送到 MessageBox 資料庫，與升級的屬性**ParseError = true**。  
  
- 如果訊息失敗，因為沒有訂用帳戶，或在標題中的結構錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]原始"wire"格式 （如果之前正在剖析） 擱置訊息。 沒有訂用帳戶失敗的常見原因是缺少的升級屬性。 由於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]擱置未剖析的訊息， **BTS。MessageType**會是空白。  
  
  下表列出 MLLP 接收配接器傳回的錯誤。  
  
|            事件             |  ID  |                                                                                                          錯誤狀況                                                                                                           |
|------------------------------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **ErrorListening**      | 8448 |                                                   無法繫結至本機通訊端 （最有可能其他本機應用程式使用相同的 IP 位址/連接埠編號組合）。                                                    |
| **ErrorAcceptingConnection** | 8449 | 無法建立與遠端的一方的 TCP 連線。 任一[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]達到連線數上限，或資源不足。 |
|  **ErrorSubmittingMessage**  | 8452 |                   MessageBox 資料庫不可以接受該訊息。 任一[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]變得無法使用或資源不足。                   |
|     **ErrorSendingAck**      | 8454 |                                [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 無法傳回通知，因為連線無法使用。                                 |
  
## <a name="performance-counters"></a>效能計數器  
 下表列出使用 MLLP 配接器的效能計數器。  
  
|計數器|意義|  
|-------------|-------------|  
|Bytes|已接收或傳送的所有文件的內容的大小。|  
|位元組/秒|目前裝載接收或傳送的輸送量。|  
|處理文件數|**MLLP 接收**:<br /><br /> 文件數目成功傳遞到 MessageBox 資料庫。<br /><br /> **MLLP 傳送**:<br /><br /> 已成功傳送給遠端應用程式的文件的數目。|  
|失敗的文件|**MLLP 接收**:<br /><br /> 未成功傳遞到 MessageBox 資料庫的文件數目。<br /><br /> **MLLP 傳送**:<br /><br /> 未成功傳遞到遠端應用程式的文件數目。|  
|連線狀態|配接器連線中，狀態 1 或 0 (1 = 連接)。|  
  
 效能計數器執行個體可以使用下列命名配置：  
  
```  
{recv|trans} : connection name : remote IP address : remote port ID  
```  
  
 MLLP 接收配接器使用的 「 接收 」 前置詞，並 MLLP 傳送配接器會使用 「 交易 」。  
  
> [!NOTE]
>  所傳送的通知接收埠 （例如，配接器在雙向模式中操作），並傳送連接埠 （在相同的通訊端連線接收 Ack 操作） 不會計算。  
  
## <a name="see-also"></a>另請參閱  
 [處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [組態參數，傳送和接收配接器](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [MLLP 傳送配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [設定傳送埠來接收 ACK](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)