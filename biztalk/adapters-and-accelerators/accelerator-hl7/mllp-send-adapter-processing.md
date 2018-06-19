---
title: MLLP 傳送配接器處理 |Microsoft 文件
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
ms.openlocfilehash: 1644d699014f23ce90568034c4bd90f6f0c7b099
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207526"
---
# <a name="mllp-send-adapter-processing"></a>MLLP 傳送配接器處理
最小的較低層通訊協定 (MLLP) 傳送配接器支援單向和雙向傳輸模式中的下列設定：  
  
-   雙向請求-回應傳送配接器  
  
-   設定為接收通知 (Ack) 的單向傳送配接器  
  
-   單向傳送配接器設定為沒有傳回訊息  
  
## <a name="two-way-solicit-response-send-mllp-adapter"></a>雙向請求-回應傳送 MLLP 配接器  
 使用此配接器，則為 true 的端對端同步實例中。 因此，您只可以使用此配接器與一個目的地合作對象。 傳送配接器將會持續維持對遠端合作對象 (URL) 的開啟連接之前它會傳回訊息路由至要求回應接收埠。 請參閱下圖為要求回應請求/回應處理的架構。  
  
 當您使用此配接器時，您可以將系統上，以傳回特定業務應用程式的 ACK 或回應訊息。 您可以使用通知的路由設定至傳送管線中的要求回應接收埠設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。 選取此屬性，傳回通知，或取消選取它來傳回回應會議。  
  
 使用此配接器的傳送埠已順利傳送原始訊息中，一旦[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]刪除該訊息。 與此傳送埠關聯的接收管線將不會產生通知。 BizTalk 會轉寄原始碼應用程式值為何，該回應的 MSA2 欄位的查詢回應。  
  
## <a name="one-way-send-mllp-adapter-configured-to-receive-acks"></a>設定為接收通知的單向傳送 MLLP 配接器  
 此配接器會在相同的通訊端連線，傳送原始訊息，並將通知傳遞至接收位置上接收認可。 傳送配接器持續維護遠端合作對象 (URL)，針對開啟連接，即使沒有訊息正在等待[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]傳送至它。 如果數個連接埠都指向相同的遠端合作對象，傳送配接器會維護每個傳送埠的一個連線。  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 安裝程式安裝預設的接收位置，TwoWayAckReceiveLocation。 您可以使用這個接收位置 MLLP 傳送配接器的接收通知。 使用此配接器的傳送埠的此設定需要您將接收位置與傳送埠產生關聯。  
  
 如果您設定接收回應訊息 MSA 的欄位，或支援多個目的地，請使用此傳送埠。 雙向請求-回應配接器不會處理與 MSA 欄位或多個目的地。  
  
### <a name="acknowledgments-received-by-the-one-way-mllp-send-adapter"></a>單向 MLLP 所收到的通知傳送配接器  
 當針對通知設定單向 MLLP 傳送配接器會接收一個，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 MessageBox 資料庫刪除原始訊息、 重試，或暫停它，根據相同的類型 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析 ACK 分成兩個階段：  
  
-   第一階段是傳送配接器在其中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析欄位 MSA1 來判斷類型的通知。  
  
-   在第二個階段中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]執行完成的通知，所用的剖析，然後再提交至 MessageBox 資料庫的認可。  
  
 設定雙向傳送配接器必須要在通知[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。  
  
 下表顯示 MLLP 傳送配接器可以接收的通知傳送和產生的動作，原始訊息上。  
  
|收到的通知|原始訊息的動作|  
|------------------|------------------------------------|  
|接受認可，或接受應用程式|從 MessageBox 資料庫中刪除|  
|認可/應用程式、 拒絕通知或無效的通知|暫止|  
|認可/應用程式錯誤|重試/移動至備份傳輸/暫停|  
|靜態通知成功|從 MessageBox 資料庫中刪除|  
|靜態通知失敗|暫止|  
  
 下表顯示無效通知條件。  
  
|執行個體|條件|  
|--------------|---------------|  
|HL7 （原始、 予改良，可延後）|1.不包含 XML。<br />2.沒有已結構，因此無法擷取 MSA1 欄位;或 MSA1 欄位未包含其中一個 CA、 AA、 CR，AR、 CE （AE） 所允許的值。|  
|靜態|不符合其中一個允許的值，表示成功或失敗通知。|  
|包含 XML|視為接受 ACK （不論內容） 和刪除原始訊息。|  
  
### <a name="error-conditions"></a>錯誤狀況  
 下列可能會發生錯誤狀況或閒置時：  
  
-   如果外寄訊息會在序列化失敗，傳送配接器不會傳送訊息，除非它是批次訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]正在串流處理。 如果這種情況下，和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]偵測序列化失敗訊息的中間，配接器將不會傳送 EB/CR 自[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]尚未傳送完成訊息。 管線會記錄錯誤，且配接器嘗試重新傳送批次訊息。  
  
-   如果傳送作業失敗，配接器會嘗試一次，將訊息傳送至傳送埠組態設定中指定的重試次數。 之後耗盡重試次數，訊息會移至備份傳輸，如果有的話。 如果所有解決方案均失敗，則會擱置訊息。 擱置的訊息會在原始 (XML) 格式。  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以產生下列事件來描述錯誤條件：  
  
|事件|ID|錯誤狀況|  
|-----------|--------|---------------------|  
|ErrorSendingMessage|8450|無法傳送訊息到遠端合作對象。 最常見的原因是網路失敗或逾時。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]如果傳送管線無法序列化大型訊息時，可能會報告此錯誤。|  
|ErrorReceivingAck|8451|無法接收通知，因為發生網路失敗或逾時。|  
|ErrorConnecting|8453|無法建立 TCP 連線到遠端合作對象： 無法解析，主機名稱，或遠端的合作對象不接聽通訊埠，或已拒絕連線。|  
  
> [!NOTE]
>  （在原始訊息的 MSH5) 的目的合作對象組態可決定是否[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]需要 HL7 或靜態的通知。 如果不相符， [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ACK 視為無效。  
  
 MLLP 配接器處理序傳送通知之後，通知會傳遞到接收位置做為其本身的訊息。 解譯器會執行完整剖析的通知，這可能會導致剖析錯誤報告的接收管線和/或暫停狀態的通知。  
  
## <a name="see-also"></a>另請參閱  
 [處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [組態參數傳送和接收配接器](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [MLLP 的接收配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [設定傳送埠來接收通知](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)