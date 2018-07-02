---
title: MLLP 傳送配接器處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, send adapters
- send adapters
- MLLP adapters, send adapters
ms.assetid: b8e47c7f-4a69-4f0c-86b4-26ed9c70613c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 396905f9b4cc8c1ebb0dbd1d3051b6f40566662a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971911"
---
# <a name="mllp-send-adapter-processing"></a>MLLP 傳送配接器處理
最小的較低層通訊協定 (MLLP) 傳送配接器支援單向和雙向傳輸模式，下列組態：  
  
-   雙向請求-回應傳送配接器  
  
-   設定為接收通知 (Ack) 的單向傳送配接器  
  
-   針對任何傳回的訊息設定的單向傳送配接器  
  
## <a name="two-way-solicit-response-send-mllp-adapter"></a>雙向請求-回應傳送 MLLP 配接器  
 使用此配接器，則為 true 的端對端同步實例中。 因此，您只可以使用此配接器與一個目的地合作對象。 傳送配接器將會持續維護對遠端合作對象 (URL) 的開啟連接之前它會傳回的訊息路由至要求回應接收埠。 請參閱下圖中的要求回應請求/回應處理的架構。  
  
 當您使用此配接器時，您可以指示系統傳回的特定業務應用程式的 ACK 或回應訊息。 您可以使用通知的路由設定至傳送管線中的要求回應接收埠設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。 選取此屬性，傳回 ACK，或取消選取它，以傳回回應會議。  
  
 使用此配接器的傳送埠成功傳送原始訊息中，一旦[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]刪除該訊息。 與此傳送埠關聯的接收管線不會產生通知。 BizTalk 會轉送到原始碼應用程式的值為何，該回應的 MSA2 欄位的查詢回應。  
  
## <a name="one-way-send-mllp-adapter-configured-to-receive-acks"></a>設定為接收通知的單向傳送 MLLP 配接器  
 此配接器在相同的通訊端連線，將原始訊息傳送，並將通知傳遞至接收位置收到 Ack。 傳送配接器持續維護遠端合作對象 (URL)，針對開啟的連接，即使沒有訊息正在等待[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將它們傳送給它。 如果數個連接埠都指向相同的遠端合作對象，傳送配接器會維護每個傳送埠的一個連線。  
  
 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 安裝程式會安裝預設的接收位置，TwoWayAckReceiveLocation。 您可以使用這個來接收 Ack 接收 MLLP 傳送配接器的位置。 使用此配接器的傳送埠的此設定會要求您傳送埠相關聯的接收位置。  
  
 如果您設定來接收回應訊息與 MSA 欄位中，或以支援多個目的地，請使用此傳送埠。 雙向請求-回應配接器無法使用 MSA 欄位或多個目的地。  
  
### <a name="acknowledgments-received-by-the-one-way-mllp-send-adapter"></a>通知接收的單向 MLLP 傳送配接器  
 當針對通知設定單向 MLLP 傳送配接器接收，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 MessageBox 資料庫刪除原始的訊息、 重試，或暫停它根據相同的類型 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 在兩個階段會剖析將通知設定：  
  
- 第一個階段是傳送配接器在其中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析欄位 MSA1 來判斷類型的通知。  
  
- 在第二個階段中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]執行完成的通知，所用的剖析，然後再提交至 MessageBox 資料庫的認可。  
  
  設定雙向傳送配接器會預期要有 ACK[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。  
  
  下表會顯示原始的訊息上的 MLLP 傳送配接器可以接收的通知和產生的動作。  
  
|收到的通知|原始訊息時採取的動作|  
|------------------|------------------------------------|  
|接受認可，或接受應用程式|從 MessageBox 資料庫刪除|  
|認可/應用程式、 拒絕通知或無效的通知|暫止|  
|認可/應用程式錯誤|重試/移動至備份傳輸/暫停|  
|靜態通知成功|從 MessageBox 資料庫刪除|  
|靜態通知失敗|暫止|  
  
 下表顯示不是有效的通知條件。  
  
|執行個體|條件|  
|--------------|---------------|  
|HL7 （原始、 增強，延後）|1.不包含 XML。<br />2.沒有已結構，因此無法擷取 MSA1 欄位;或 MSA1 欄位未包含其中一個 CA、 AA、 CR，AR、 CE （AE） 允許的值。|  
|靜態|不符合其中一個允許的值，表示成功或失敗通知。|  
|包含 XML|視為接受 ACK （不論內容），並刪除原始的訊息。|  
  
### <a name="error-conditions"></a>錯誤狀況  
 會發生下列狀況時的錯誤條件或無活動狀態：  
  
- 如果外寄訊息無法在序列化中，傳送配接器不會傳送訊息，除非它是批次訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]正在串流處理。 如果是這樣，和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]偵測到序列化失敗中途訊息，配接器不會傳送 EB/CR 自[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]已不會傳送完整的訊息。 管線記錄錯誤，而且配接器會嘗試重新傳送批次訊息。  
  
- 如果傳送作業失敗，配接器會嘗試一次，將訊息傳送至傳送埠組態設定中指定的重試次數。 之後耗盡重試次數，訊息會移至備份傳輸，如果有的話。 如果所有解決方案均失敗，則會擱置訊息。 擱置的訊息會進入原始 (XML) 格式。  
  
  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 可以產生下列事件來描述錯誤條件：  
  
|        事件        |  ID  |                                                                                                                                   錯誤狀況                                                                                                                                   |
|---------------------|------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ErrorSendingMessage | 8450 | 無法將訊息傳送至遠端合作對象。 最常見的原因是網路失敗或逾時。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 如果傳送管線無法序列化大型訊息時，可能會報告此錯誤。 |
|  ErrorReceivingAck  | 8451 |                                                                                                       可能不會收到通知，由於網路失敗或逾時。                                                                                                       |
|   ErrorConnecting   | 8453 |                                                    無法建立 TCP 連線到遠端合作對象： 無法解析，主機名稱，或遠端的合作對象未接聽該連接埠，或已拒絕連線。                                                     |
  
> [!NOTE]
>  （在原始訊息的 MSH5) 的目的合作對象的設定會決定是否[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]預期 HL7 或靜態的通知。 如果不相符， [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ACK 視為無效。  
  
 MLLP 傳送配接器處理序的通知之後，就會通知傳送到本身的訊息的接收位置中。 解譯器會執行完整剖析的通知，這會導致剖析錯誤所報告的接收管線和/或遭到擱置的通知。  
  
## <a name="see-also"></a>另請參閱  
 [處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [組態參數，傳送和接收配接器](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [MLLP 接收配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [設定傳送埠來接收 ACK](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)