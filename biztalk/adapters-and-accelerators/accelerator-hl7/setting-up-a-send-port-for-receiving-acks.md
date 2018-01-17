---
title: "設定傳送埠來接收 Ack |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, acknowledgements
- creating, send ports
- acknowledgements, send ports
- send ports, creating
ms.assetid: bb683e72-36e2-4a8f-acc2-8b37ed23746f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df0988a9edc2af81970237aad363315a778f821b
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-send-port-for-receiving-acks"></a>設定傳送埠來接收通知
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 即可單向傳送埠上接收通知 (ACK)。 當您設定新的單向傳送埠來接收相同的連接上認可時，您必須使該傳送埠為單向接收埠。  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝程式會建立單向接收埠 (稱為**TwoWayAckReceivePort**) 和接收位置 (稱為**TwoWayAckReceiveLocation**)。 接收位置會使用最少的較低層通訊協定 (MLLP) 傳輸類型、 具有 URI 的"127.0.0.1:65535"，並且使用**BTAHL72XReceivePipeline**。 以下是用於接收所需的設定和處理對訊息收到通知所送出[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送配接器，以雙向的模式。 此接收位置不應該刪除或用於其他任何用途。 永遠不會將資料傳送至這個接收位置。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]啟用此接收位置的預設值。  
  
 **TwoWayAckReceiveLocation**、 哪些[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝精靈 」 建立時，會使用**BizTalkServerApplication**的接收處理常式。 不過，如果您選擇建立新的主機，並作為 MLLP 的接收處理常式，則您必須執行下列命令以建立新**TwoWayAckReceiveLocation**:  
  
1.  建立單向接收埠。  
  
2.  建立單向 MLLP 的接收位置。  
  
3.  指定適當 MLLP 傳輸屬性的值。  
  
4.  指定適當的接收處理常式。  
  
5.  啟用接收位置。  
  
### <a name="to-create-a-send-port-enabled-to-receive-an-ack-on-the-same-socket"></a>若要建立傳送埠來接收通知，在相同的通訊端上已啟用  
  
1.  開啟 BizTalk 管理主控台，然後展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk應用程式 1**。 以滑鼠右鍵按一下**傳送埠**，指向 [新增]，然後按一下**靜態單向傳送埠**。  
  
2.  在**名稱**方塊中，輸入傳送埠的名稱。  
  
3.  在**傳輸** 區段中，針對**類型**，選取**MLLP**。  
  
4.  按一下  **設定**。  
  
5.  在 [MLLP 傳輸屬性] 對話方塊中，輸入連線名稱和主機 (例如， **localhost**)。  
  
6.  如**請求回應啟用**，選取**是**。 保留**提交接收位置 (URI) ACK**保留空白，，然後按一下 **確定**。  
  
    > [!NOTE]
    >  當您離開**提交接收位置**空白，BTAHL7 進入 URI 預設**TwoWayAckReceiveLocation**。 您可以確認後, 按一下**確定**步驟 6 中，依序按一下**組態**一次。 URI **TwoWayAckReceiveLocation** (127.0.0.1:65535) 輸入**提交接收位置 (URI) ACK**。  
  
    > [!NOTE]
    >  您必須建立傳送埠以接收通知訂閱或通知中會顯示暫止狀態，因為找不到任何訂用帳戶。 要訂閱的傳送埠所接收的通知，請使用篩選器，例如**BTS。MessageType = = \< *MessageType* \>** 和**BTS。ReceivePortName = = \< *ReceivePort*\>**。 針對靜態的通知訊息類型是**StaticAck**。  
  
7.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [ACK 訊息結構描述類型](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md)   
 [訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [通知錯誤狀況](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)