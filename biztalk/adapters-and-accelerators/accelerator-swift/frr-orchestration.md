---
title: FRR 協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, promoted properties
- orchestrations, message subscriptions
- promoted properties, messages
- FRR, orchestrations
- subscriptions, messages
- orchestrations, reconciliation time-out
- messages, message/response correlation
- message/response correlation
- promoted properties, FIN Response Reconciliation
- orchestrations, FRR
- outbound messages
- FIN Response Reconciliation, promoted properties
- direct bindings
- reconciliation time-out
- bindings, direct
- messages, subscriptions
- subscriptions, orchestrations
- messages, outbound
- MessageBox database
ms.assetid: ea8d31c2-ac3b-44ac-8064-d008da4f7f72
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f56b16f59b967ccd9e57d03d38f86e64795da477
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967876"
---
# <a name="frr-orchestration"></a>FRR 協調流程
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]實作 FRR 透過 FRR 協調流程。 協調流程判斷是否相互關聯語彙基元 FIN 回應符合原始訊息的訊息識別碼。 傳送埠將訊息傳送至 SAA，所執行的傳送函式與 SAA 從接收訊息的接收位置所執行的接收函式，它就會處理該訊息以平行方式。  
  
 在最高的層級，協調流程執行個體就會執行下列處理：  
  
1.  快取原始輸出訊息的複本繫結 SAA 透過 MessageBox 上接聽。  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]建立協調流程的執行個體時[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會將原始訊息路由至 MessageBox。  
  
2.  等候[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]發佈至 MessageBox SAA FIN 回應。  
  
3.  設定升級 FIN 回應的本質而定，原始訊息的複製的內容。  
  
4.  將原始訊息的副本發佈回 MessageBox。 自訂處理常式可以訂閱擷取，並處理該訊息所需。  
  
## <a name="subscription-to-outbound-messages"></a>輸出訊息的訂閱  
 FRR 協調流程直接繫結至 MessageBox。 FRR 協調流程會訂閱所有輸出訊息的 SWIFT 網路繫結不包含驗證錯誤，藉由訂閱的下列屬性：  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = false （SWIFT 解譯器驗證程序所設定）  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Swiftbound = = true （SWIFT 解譯器組態程序所設定）  
  
## <a name="messageresponse-correlation"></a>/ 回應訊息的相互關聯  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]與要輸入 FIN 回應訊息的原始輸出 FIN 訊息相互關聯藉由比較下列屬性：  
  
-   FIN 回應 MQMD_CorrelID 內容屬性  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken 輸出 MTXYY 訊息屬性。 這個屬性會由接收管線的合作對象解析階段升級。  
  
 這些屬性的值必須相同。 訊息的傳送管線的編碼器階段繫結的 SWIFT 設定外寄訊息的 MQMD_MsgID 屬性的值[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken 屬性。 SAA 設定回應訊息的 MQMD_CorrelID 屬性 MQMD_MsgID 的值。  
  
## <a name="setting-of-promoted-properties"></a>升級屬性的設定  
 接收 FIN 回應並建立相互關聯的原始訊息的副本之後, FRR 協調流程會設定根據回應的本質，原始訊息的複本的升級下列屬性：  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]為 True，如果回應 ACK 或 False 的回應是 NAK 如果 _FRRFailed  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]其中一個下列的值，如果回應 NAK _FRRFailedReason:  
  
    -   *\<ErrorCode\>*  （從 MTS21_FIN_ACKNAK 負值通知訊息的 405 欄位）  
  
    -   TransportError （從 MQ 系列取景位置調整/NAN 訊息）  
  
    -   DelayedNAK （從 MT015 (DNK) 訊息）  
  
    -   AbortReceived (從 MT019 （中止通知） 訊息)  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]逾時的 _FRRFailedReason 如果[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]未在逾時期限內收到回應。 如需 FRR 延遲逾時的詳細資訊，請參閱下方的 [對帳逾時] 區段或[設定 FRR 延遲逾時](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md)。  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]若要 _SendingServiceType [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService  
  
-   BTS。作業的訊息回應型別對應的值。 如需詳細資訊，請參閱[FRR 傳送埠建立的自訂處理常式的傳送](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendTransport MQ 系列取景位置調整/NAN 訊息 (MQ Series 傳輸層級 ACK/NAK)  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend010NDW MT010 訊息 （非傳遞警告）  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend011Delivered MT011 訊息 （傳送通知）  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend012SenderACK MT012 訊息 （寄件者通知）  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend015DNK MT015 訊息 （DNK 或延遲 NAK）  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend019Abort MT019 訊息 （中止通知）  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendS21ACK MTS21_FIN_ACKNAK 通知訊息 (ACK 傳送 LT FIN 訊息)  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendS21NAK MTS21_FIN_ACKNAK 負值通知訊息 (NAK 傳送 LT FIN 訊息)  
  
## <a name="direct-binding"></a>直接繫結  
 輸入接收協調流程會由協調流程對 MessageBox 訂閱。 內容屬性，以及由協調流程升級值定義協調流程發佈到 MessageBox 的訊息的傳送輸出。 此 messagebox 直接繫結，因為協調流程就可以從下列分隔：  
  
-   實體接收位置會接收來自後端應用程式，以路由至 SAA 輸出訊息  
  
-   傳送輸出的傳送埠 FIN 訊息從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]SWIFT 聯盟存取 (SAA)  
  
-   從 SAA 接收連入 FIN 回應訊息的接收位置  
  
-   實體由 SAA 均存放 FIN 回應的 MQSeries 佇列  
  
## <a name="reconciliation-time-out"></a>重新調整逾時  
 當[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]FRR 協調流程，在等候 FIN 回應的協調流程啟動的新執行個體。 在執行階段，您必須設定協調流程的逾時時間後一些持續時間，使它不會等待回應無限期。 當逾時期間到期時，會升級 FRR 協調流程[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason 屬性並將它設定為逾時。 然後，將出的訊息發佈到 MessageBox，並終止。 如果您的時間，相互關聯識別碼會消失。  
  
 您可以建立自訂的處理常式來處理逾時訊息 （原始輸出訊息的複本）。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會完成這項作業使用待命圖形在協調流程中。 如需詳細資訊，請參閱[設定 FRR 延遲逾時](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md)。