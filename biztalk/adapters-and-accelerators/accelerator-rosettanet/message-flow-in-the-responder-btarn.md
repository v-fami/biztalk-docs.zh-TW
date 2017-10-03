---
title: "訊息回應者 BTARN 中的流程 |Microsoft 文件"
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
- responder BTARN
ms.assetid: 66de8694-a248-47e8-9483-9eedf2324b33
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ad33db4f67336f41ac868a7a14e1266a85dd45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-flow-in-the-responder-btarn"></a>回應者 BTARN 中的訊息流程
回應者電腦上的訊息流程一開始會透過網際網路接收來自啟動者電腦的訊息。 其中牽涉將該訊息從 RosettaNet 實作架構 (RNIF) 相容訊息轉換為後端應用程式專屬格式的訊息，然後將訊息傳送到商務營運系統應用程式。  
  
 若交易夥伴介面程序 (PIP) 是單向動作，則唯一的回應是通知信號訊息。 如果 PIP 是雙向動作，回應者將處理並傳送回應訊息，隨後接收該回應的確認結果。  
  
 若 PIP 為非同步，透過網際網路傳送的每個訊息都會使用不同的 HTTP 連線。 若 PIP 為同步，每個訊息傳輸會使用相同的連線，程序完成前 HTTP 配接器會一直保留此連線。 在雙向同步實例中，回應者電腦不會為了回應初始要求訊息而傳送通知給啟動者電腦。 回應訊息是做為通知使用。  
  
## <a name="btarn-components-on-the-responder-computer"></a>回應者電腦上的 BTARN 元件  
 當訊息流程透過[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]的回應者電腦上，下列元件會處理訊息：  
  
-   RNIFReceive.aspx 頁面  
  
-   HTTP 配接器  
  
-   接收管線  
  
-   回應者公開程序  
  
-   回應者私用程序  
  
-   SQL adapter (SQL 配接器)  
  
-   傳送管線  
  
 如需有關這些元件，以及它們如何處理訊息的詳細資訊，請參閱[BTARN 中的訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)。  
  
## <a name="message-flow-on-the-responder-computer"></a>回應者電腦上的訊息流程  
 透過 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 回應者電腦，接收訊息的訊息流程如下：  
  
 ![](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-responder-receive-message-flow.gif "RN3_Responder_Receive_Message_Flow")  
  
1.  RNIFReceive aspx 頁面接收來自啟動者的內送訊息。  
  
2.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將訊息提交給 HTTP 配接器，它會將訊息提交給接收管線。  
  
3.  接收管線會針對訊息進行解碼、解譯與合作對象解析，然後轉換訊息為後端商務營運系統應用程式的專屬格式。  
  
4.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將訊息傳送至 MessageBox 資料庫。  
  
5.  公開程序會處理訊息的 RNIF 標頭。  
  
6.  私用程序會處理訊息的服務內容。 它會產生通知，傳回到公開程序、MessageBox 資料庫、傳送管線，再傳回到 HTTP 配接器，透過網際網路傳回給啟動者。  
  
7.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將訊息傳送至 MessageBox 資料庫。  
  
8.  傳送管線會組譯訊息，然後簽署/加密/編碼訊息。  
  
9. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將訊息傳送至 SQL 配接器。  
  
10. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將訊息提交到 [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，再到後端的商務營運系統應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [BTARN 中的訊息流程](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)   
 [啟動者 BTARN 中的訊息流程](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-the-initiator-btarn.md)