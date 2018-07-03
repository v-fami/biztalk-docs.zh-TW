---
title: FRR 處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, processing
- FRR, components
- FRR, process flow
ms.assetid: 8b064d18-5ee7-44fd-95d1-9a0d66f1ad1a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30c343d214a97895e90bae2bc3a041180c0cc8e3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987007"
---
# <a name="frr-processing"></a>FRR 處理
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FIN 回應對帳 (FRR) 功能與原始訊息相互關聯 FIN 訊息從 SWIFT Alliance 存取 (SAA) [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] SAA 訊息回應。 每當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]傳送原始訊息時，FRR 快取任何 SWIFT 和繫結的訊息副本不處理失敗。 然後它會監視 SAA 至所傳回的回應訊息的 MessageBox [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，並挑選對應至快取的訊息複本的任何通知/NAK 訊息。  

 FRR 會藉由比較相互關聯識別碼屬性來建立外寄訊息和內送訊息之間的相互關聯。 FRR 設定根據回應的本質，原始訊息的複本的升級的屬性，然後將原始訊息路由傳送至 MessageBox 做進一步處理。  

## <a name="frr-components"></a>FRR 元件  
 FRR 包括進行中的程序 （協調流程） 來監視傳出和傳入訊息，並為每個傳出或傳入的訊息，將它用來進行比較的識別屬性升級。 一系列[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]FRR 協調流程中，將訊息內的 FRR 元件之間路由搭配運作的元件[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，和之間[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]和 SAA。 以下列出這些元件：  

- FRR 接收來自後端應用程式接收原始訊息的位置。  

- FRR 協調流程會監視傳出和傳入訊息，並建立它們之間的相互關聯。  

- FRR 傳送埠傳送原始訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]SAA 到。  

- BizTalk Adapter for MQSeries 可之間的資料傳輸[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 SAA （這會使用 MQSeries 佇列）。  

- FRR 接收位置，接收來自 SAA FIN 回應訊息。  

- FRR 傳送埠，其中每個傳送相互關聯的訊息，從特定類型的一組[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]至後端應用程式的自訂處理。  

  上述的元件，您可以新增後端的自訂處理常式，以處理升級的屬性，其中已設定 FRR 原始訊息。  

## <a name="frr-process-flow"></a>FRR 處理流程  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 在下列程序中執行重新調整：  

1. 後端應用程式傳送原始訊息的目標[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。  

2. FRR 接收位置接收訊息、 處理在相關聯的接收管線中，並將其路由傳送到 BizTalk MessageBox。  

   > [!NOTE]
   >  您可以搭配使用 FRR [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair 和 New Submission 的功能，或分別。 如果您已安裝訊息修復和新送出，您可以設定在步驟 2 之後的訊息修復系統。 訊息修復協調流程修復/驗證/核准會將訊息路由至 BizTalk MessageBox 進行後續的 FRR 處理。  

3. 如果所繫結的 SWIFT MessageBox 中的訊息，而且已通過驗證，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]啟動 FRR 協調流程執行個體。 協調流程會保留外寄訊息的複本。 它然後等候回應 SAA，因此它會比對任何內送回應外寄訊息處於啟動狀態。 協調流程的這個執行個體只會處理該特定的外寄訊息和任何相互關聯的回應，該訊息。 任何其他訊息，即使是相同的型別，是由另一個協調流程執行個體處理。  

4. 在相同時間[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]啟動 FRR 協調流程執行個體，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會將訊息路由至傳送埠將訊息傳送至 SAA。 傳送管線會升級訊息識別屬性和處理 MQSeries 所需的屬性。 然後，將傳送訊息至 BizTalk Adapter for MQSeries。  

5. BizTalk Adapter for MQSeries 傳輸 SAA 在適當的 MQSeries 佇列的訊息。  

6. SAA 會產生路由直接傳回立即回應[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 SAA 然後會將訊息傳送至 SWIFT 網路。 SWIFT 網路會產生其他回應，它會傳送回路由至 SAA [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 SAA 設定 FIN 回應訊息的相互關聯語彙基元屬性的原始訊息的訊息識別碼值。  

7. 透過 BizTalk Adapter for MQSeries FIN 回應傳送給 SAA 傳輸[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。  

8. FRR 接收位置接收回應，然後將路由傳送訊息的 FRR 接收管線處理回應的相互關聯 token。 然後，就會將回應 BizTalk MessageBox 中。  

9. FRR 協調流程執行個體從具有等於原始訊息複本的訊息 ID 屬性的相互關聯權杖在 MessageBox 中挑選出任何訊息。  

10. 如果此回應指出原始訊息已成功處理由 SAA/SWIFT，FRR 協調流程執行個體設定 A4SWIFT_Failed 升級屬性的原始訊息的複本設為 False，並設定 BTS。作業屬性設為適當的值。  

11. 如果原始訊息已無法順利處理 SAA/SWIFT，FRR 協調流程執行個體設定 BTS。作業屬性，以適當的值，並再將修復的訊息指定 A4SWIFT_Failed 設為 True，並將升級的 A4SWIFT_FRRFailedReason 屬性設定為失敗的原因。  

12. FRR 協調流程執行個體的回應訊息中，就會捨棄，然後將原始訊息的副本 （使用升級的屬性，指出回應） 路由傳送至 MessageBox。  

13. 其中一個的 FRR 傳送埠設定來回應路由到一或多個自訂處理常式拾取的升級屬性的原始訊息的副本。  

14. 自訂處理常式或處理常式訂閱、 擷取，並處理所需的後端應用程式的原始訊息的副本。
