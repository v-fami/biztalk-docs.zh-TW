---
title: "FRR 處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, processing
- FRR, components
- FRR, process flow
ms.assetid: 8b064d18-5ee7-44fd-95d1-9a0d66f1ad1a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2b0d34ccffd2bf09148bcfc5544b38ea5d0033d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="frr-processing"></a>FRR 處理
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FIN 回應對帳 (FRR) 功能與原始訊息相互關聯 FIN 訊息從 SWIFT 聯盟存取 (SAA) [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] SAA 訊息回應。 每當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]傳送原始訊息時，FRR 快取繫結為 SWIFT 和任何訊息的複本有未處理失敗。 然後它會監視之回應訊息傳回至 SAA MessageBox [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，並挑選任何 ACK/NAK 訊息對應至快取的訊息複本。  
  
 FRR 建立外寄訊息和內送訊息之間的相互關聯，藉由比較相互關聯識別碼屬性。 FRR 設定根據回應，本質，原始訊息的複本的升級的屬性，然後將原始訊息路由至 MessageBox 做進一步處理。  
  
## <a name="frr-components"></a>FRR 元件  
 FRR 包括持續的程序 （協調流程） 來監視傳出和傳入的訊息，並針對每個傳出或傳入的訊息，將會用於比較的識別屬性升級。 一系列的[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]元件一起 FRR 協調流程、 路由內 FRR 元件之間的訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，和之間[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]和 SAA。 以下列出這些元件：  
  
-   FRR 接收位置從後端應用程式接收原始訊息。  
  
-   FRR 協調流程會監視傳出和傳入的訊息，並建立它們之間的相互關聯。  
  
-   FRR 傳送原始訊息的傳送埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]SAA 至。  
  
-   BizTalk Adapter for MQSeries 可之間資料傳輸[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 SAA （這會使用 MQSeries 佇列）。  
  
-   FRR 接收接收來自 SAA FIN 回應訊息的位置。  
  
-   FRR 傳送埠，其中每個傳送從特定類型的相互關聯的訊息的一組[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]至後端應用程式的自訂處理。  
  
 上述的元件，您可以加入處理 FRR 已設定其中的升級的屬性的原始訊息的後端自訂處理常式。  
  
## <a name="frr-process-flow"></a>FRR 程序流程  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]在下列程序中執行重新調整：  
  
1.  後端應用程式傳送原始訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。  
  
2.  FRR 接收位置接收訊息、 處理在相關聯的接收管線中，並將其路由傳送到 BizTalk MessageBox。  
  
    > [!NOTE]
    >  您可以搭配使用 FRR [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair 和 New Submission 功能或分開。 如果您已安裝訊息修復和新送出，您可以設定在步驟 2 之後的訊息修復系統。 訊息修復協調流程修復/確認/核准會將訊息路由到 BizTalk MessageBox 進行後續 FRR 處理。  
  
3.  如果 MessageBox 中的訊息 for SWIFT 繫結，並已通過驗證，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]啟動 FRR 協調流程執行個體。 協調流程會保留外寄訊息的複本。 接著，它的啟動狀態 SAA，讓它可以比對任何內送回應外寄訊息的回應的等候時間。 這個執行個體的協調流程只會處理該特定的外寄訊息和任何相互關聯的回應，該訊息。 任何其他訊息，即使屬於相同的類型中，會由另一個協調流程執行個體處理。  
  
4.  在相同時間[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]FRR 協調流程執行個體，就會啟動[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會將訊息路由至傳送埠將訊息傳送至 SAA。 傳送管線會升級訊息識別屬性和處理 MQSeries 所需的屬性。 它會傳送訊息給 BizTalk Adapter for MQSeries。  
  
5.  BizTalk Adapter for MQSeries 傳輸 SAA 在適當的 MQSeries 佇列的訊息。  
  
6.  SAA 會產生直接路由至立即回應[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 SAA 然後會將訊息路由至 SWIFT 網路。 SWIFT 網路會產生其他回應將它傳送到 SAA 路由傳回[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 SAA 設定 FIN 回應訊息的相互關聯語彙基元屬性的原始訊息的訊息識別碼值。  
  
7.  透過 BizTalk Adapter for MQSeries FIN 回應傳送給 SAA 傳輸[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。  
  
8.  FRR 接收位置接收回應，並會透過 FRR 訊息路由傳送的接收管線處理回應的相互關聯 token。 然後，就會將回應 BizTalk MessageBox 中。  
  
9. FRR 協調流程執行個體從 MessageBox 具有等於原始訊息的複本的訊息 ID 屬性的相互關聯語彙基元取用任何訊息。  
  
10. 此回應指出原始訊息已成功處理由 SAA/SWIFT，如果 FRR 協調流程執行個體的原始訊息複本的升級 A4SWIFT_Failed 屬性設為 False，並 BTS。作業屬性設為適當的值。  
  
11. 如果原始訊息未成功處理 SAA/SWIFT，FRR 協調流程執行個體設定 BTS。作業屬性為適當的值，並再將修復的訊息指定 A4SWIFT_Failed 設為 True，並將升級 A4SWIFT_FRRFailedReason 屬性設定為 失敗的原因。  
  
12. FRR 協調流程執行個體的回應訊息，就會捨棄，然後將原始訊息的副本 （與升級的屬性，指出回應） 路由傳送至 MessageBox。  
  
13. 其中 FRR 傳送連接埠設定來路由傳送至一個或多個自訂處理常式拾取的升級屬性的原始訊息的副本的回應。  
  
14. 自訂處理常式或處理常式訂閱、 擷取，並處理所需的後端應用程式的原始訊息的複本。