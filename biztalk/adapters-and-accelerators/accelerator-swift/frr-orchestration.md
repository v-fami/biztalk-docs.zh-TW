---
title: FRR 協調流程 |Microsoft Docs
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
ms.openlocfilehash: 3ad5d9dd1b582aefa9a440508650ecd0e653dbfe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998372"
---
# <a name="frr-orchestration"></a>FRR 協調流程
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 實作 FRR 透過 FRR 協調流程。 協調流程判斷是否相互關聯語彙基元的 FIN 回應符合原始訊息的訊息識別碼。 與傳送埠將訊息傳送至 SAA，所執行的傳送函式和從 SAA 接收訊息的接收位置所執行的接收函式，它就會處理該訊息以平行方式。  
  
 在最高的層級，協調流程執行個體就會執行下列處理：  
  
1. 藉由接聽 messagebox 的 SAA 的繫結的原始輸出訊息的複本快取。  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 建立協調流程的執行個體時[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會將原始訊息路由至 MessageBox。  
  
2. 等候[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]發佈到 MessageBox SAA FIN 回應。  
  
3. 設定升級 FIN 回應的本質而定，原始訊息的複本的屬性。  
  
4. 將原始訊息的副本發佈回 MessageBox。 自訂處理常式可以訂閱若要擷取，並處理該訊息所需。  
  
## <a name="subscription-to-outbound-messages"></a>輸出訊息的訂用帳戶  
 FRR 協調流程直接繫結至 MessageBox。 FRR 協調流程會訂閱所有輸出訊息繫結的 SWIFT 網路不包含驗證錯誤，藉由訂閱的下列屬性：  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = false （SWIFT 解譯器驗證程序所設定）  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Swiftbound = = true （SWIFT 解譯器設定程序所設定）  
  
## <a name="messageresponse-correlation"></a>訊息/回應相互關聯  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 與要輸入 FIN 回應訊息的原始輸出 FIN 訊息相互關聯藉由比較下列屬性：  
  
- FIN 回應 MQMD_CorrelID 內容屬性  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken 輸出 MTXYY 訊息屬性。 這個屬性會由接收管線的合作對象解析階段中升級。  
  
  這些屬性的值必須相同。 訊息的傳送管線的編碼器階段繫結的 SWIFT 設定外寄訊息的 MQMD_MsgID 屬性的值[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken 屬性。 SAA MQMD_MsgID 的值來設定回應訊息的 MQMD_CorrelID 屬性。  
  
## <a name="setting-of-promoted-properties"></a>升級屬性的設定  
 接收 FIN 回應，並建立相互關聯的原始訊息複本之後, FRR 協調流程會設定根據回應的本質，原始訊息的複本升級的下列屬性：  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]為 True，如果回應是通知或 False 的回應是否 NAK _FRRFailed  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]其中一個下列的值，如果回應是 NAK 至 _FRRFailedReason:  
  
  -   *\<ErrorCode\>*  （從 MTS21_FIN_ACKNAK 負值通知訊息的 「 405 欄位）  
  
  -   TransportError （從 MQ 系列移動瀏覽/NAN 訊息）  
  
  -   DelayedNAK （從 MT015 (DNK) 訊息）  
  
  -   AbortReceived (從 MT019 （中止通知） 訊息)  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]為 TimedOut _FRRFailedReason 如果[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]未在逾時期限內收到回應。 如需有關 FRR 延遲逾時的詳細資訊，請參閱下方的 [調整逾時] 區段或[設定 FRR 延遲逾時](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md)。  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]若要 _SendingServiceType [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService  
  
- BTS。作業的回應訊息類型的對應值。 如需詳細資訊，請參閱 <<c0> [ 傳送至自訂處理常式建立 FRR 傳送埠](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendTransport MQ 系列移動瀏覽/NAN 訊息 (MQ Series 傳輸層級通知/NAK)  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend010NDW MT010 訊息 （非傳遞警告）  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend011Delivered MT011 訊息 (Delivery Notification)  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend012SenderACK MT012 訊息 （寄件者通知）  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend015DNK MT015 訊息 （DNK 或延遲 NAK）  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend019Abort MT019 訊息 （中止通知）  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendS21ACK MTS21_FIN_ACKNAK 通知訊息 (由 l 傳送 FIN 訊息的 ACK)  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendS21NAK MTS21_FIN_ACKNAK 負值通知訊息 (NAK 的 FIN 訊息傳送的 L)  
  
## <a name="direct-binding"></a>直接繫結  
 協調流程由協調流程會到 MessageBox 的訂用帳戶接收的輸入。 內容屬性，以及協調流程所提升的值會定義協調流程發佈到 MessageBox 的訊息的傳送輸出。 因為此 messagebox 直接繫結，就會與下列分離協調流程：  
  
- 實體接收位置會從後端應用程式，以路由至 SAA 接收輸出的訊息  
  
- 傳送輸出的傳送埠 FIN 訊息從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]SWIFT Alliance 存取 (SAA)  
  
- 從 SAA 接收連入 FIN 回應訊息的接收位置  
  
- 實體由 SAA 均存放 FIN 回應的 MQSeries 佇列  
  
## <a name="reconciliation-time-out"></a>調整逾時  
 當[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]建立 FRR 協調流程中，等候 FIN 回應在協調流程啟動的新執行個體。 在執行階段，您必須設定逾時後段期間，協調流程，使它不會等待回應無限期。 FRR 協調流程時逾時期限到期時，會升級[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason 屬性並將其設為 TimedOut。 然後，它會將輸出訊息發佈到 MessageBox，並終止。 如果您的時間，相互關聯識別碼變不見了。  
  
 您可以建立自訂的處理常式，來處理逾時訊息 （原始輸出訊息的複本）。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 會完成這項作業使用待命圖形在協調流程中。 如需詳細資訊，請參閱 <<c0> [ 設定 FRR 延遲逾時](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md)。