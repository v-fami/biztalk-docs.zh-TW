---
title: "訊息啟動者 BTARN 中的流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Accelerator for RosettaNet, message flow
- BTARN, components
- messages, message flow
- initiator BTARN
ms.assetid: 315f3d4c-5e40-4b8e-b135-9da98dc2db1e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85fed6404627fd8abfa9d50e7d56d98ff7306f09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-flow-in-the-initiator-btarn"></a>啟動者 BTARN 中的訊息流程
啟動者電腦上的訊息流程是從接收來自後端商務營運系統應用程式的專屬格式訊息開始， 其中牽扯將該訊息轉換為 RosettaNet 實作架構 (RNIF) 相容訊息，然後透過網際網路傳送訊息至回應者電腦。  
  
 若交易夥伴介面程序 (PIP) 是單向動作，則唯一的回應是通知信號訊息。 如需有關單向動作訊息流程的詳細資訊，請參閱本主題稍後的＜初始訊息的流程＞。 如果 PIP 是雙向動作，則除了單向訊息流程之外，啟動者還會接收回應訊息，然後回覆確認。  
  
 若 PIP 為非同步，透過網際網路傳送的每個訊息都會使用不同的 HTTP 連線。 若 PIP 為同步，每個訊息傳輸會使用相同的連線，程序完成前 HTTP 配接器會一直保留此連線。 在雙向同步實例中，回應者電腦不會為了回應初始要求訊息而傳送通知給啟動者電腦。 回應訊息是做為通知使用。  
  
## <a name="btarn-components-on-the-initiator-computer"></a>啟動者電腦上的 BTARN 元件  
 當訊息流程透過啟動者電腦上的 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 時，下列元件將會處理訊息：  
  
-   SQL adapter (SQL 配接器)  
  
-   XML 接收管線  
  
-   啟動者私用程序  
  
-   啟動者公開程序  
  
-   XML 傳送管線  
  
-   HTTP 配接器  
  
-   RNIFSend.aspx 頁面  
  
 如需有關這些元件，以及它們如何處理訊息的詳細資訊，請參閱[BTARN 中的訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)。  
  
## <a name="flow-of-an-initiated-message"></a>初始訊息的流程  
 下列步驟描述初始訊息透過啟動者 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 電腦的訊息流程。 下圖顯示這個程序。  
  
 ![](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-initiator-send-message-flow.gif "RN3_Initiator_Send_Message_Flow")  
  
1.  特定業務應用程式傳送訊息以[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]。  
  
2.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 從 [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫傳送訊息至 SQL 配接器。  
  
3.  XML 接收管線對訊息執行簡單的 XML 驗證。  
  
4.  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 會將訊息傳送至 MessageBox 資料庫。  
  
5.  私用程序會處理訊息的服務內容。  
  
6.  公開程序會處理訊息的 RNIF 標頭。  
  
7.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將訊息傳回至 MessageBox 資料庫。  
  
8.  傳送管線會執行組件，並簽署/加密/編碼訊息。  
  
9. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將訊息傳送至 HTTP 配接器。  
  
10. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將訊息傳送至 RNIFSend.aspx 頁面，此頁面會透過網際網路傳送訊息至目的地。  
  
## <a name="see-also"></a>另請參閱  
 [BTARN 中的訊息流程](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)   
 [回應者 BTARN 中的訊息流程](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-the-responder-btarn.md)   
 [BTARN 中的訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)