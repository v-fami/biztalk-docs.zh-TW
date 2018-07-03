---
title: BTAHL7 如何路由傳送訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- routing, about routing
- routing, messages
- messages, routing
- BTAHL7, message routing
ms.assetid: 555696c7-6023-44eb-b13d-cf7527bbc92f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c64cd0620dacf835d3765510ea74c2a8cc80c4a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999287"
---
# <a name="how-btahl7-routes-messages"></a>BTAHL7 如何路由傳送訊息
Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會利用訊息處理功能的 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，但還擴充它專屬於 HL7 傳訊需求的數種方式中。  

## <a name="routing-overview"></a>路由概觀

HL7 從企業營運 (LOB) 系統中，接收訊息，而且可能會收到使用 MLLP 配接器。 LOB 系統連線至 MLLP 配接器上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]透過 TCP 連接埠，然後再將訊息傳送至 MLLP 配接器。

在   **[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]和舊版**，HL7 MLLP 接收遠端 LOB 系統連線至 MLLP 傳輸配接器等候。 一旦遠端 LOB 系統連線時，LOB 系統使用傳送訊息至 MLLP [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 具體來說： 

1. 遠端 LOB 系統連接到在本機上的 MLLP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用 TCP 連接埠 
2. BTA4HL7 接收位置使用 MLLP 配接器接受連線 
3. 遠端 LOB 系統會傳送一個或多個訊息 
4. 中斷遠端 LOB 系統的連線

在   **[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]和較新版本**MLLP 配接器起始連接至 LOB 系統，然後 MLLP LOB 系統的推播訊息接收。 換句話說，遠端 LOB 系統的連接，再將訊息傳送至 MLLP 而等候。 具體來說： 

1. 本機[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]連線到遠端的 LOB 系統使用 TCP 連接埠 
2. BTA4HL7 接收位置使用 MLLP 配接器起始連接 
3. 遠端 LOB 系統會傳送一個或多個訊息 
4. 中斷遠端 LOB 系統的連線 

為了回溯相容性，您可以使用原始的預設行為遠端 LOB 系統會起始連線。 此選項是可設定在 MLLP 接收位置屬性。 
 
一旦接收 HL7 訊息，然後提交給 HL7 接收管線。 此管線中，內 HL7 反組譯工具就會剖析訊息，並將驗證根據適當的結構描述定義和驗證組態訊息。 此時，HL7 通知訊息可能會產生 （成功或錯誤），根據訊息和相關的通知設定的有效性。 從這裡開始，管線就會提交至 MessageBox 資料庫，以便進一步處理和路由的選擇性通知與訊息執行個體。  
  
 一旦到達 MessageBox 資料庫中的訊息執行個體[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]檢查篩選為基礎的訂用帳戶，並會將訊息路由至一或多個傳送埠 （可能是 MLLP 連接埠） 透過 HL7 傳送管線。 傳送管線可以驗證訊息執行個體，根據適當的結構描述定義和驗證組態。 除了驗證，就可以覆寫指定外寄訊息的 MSH 區段中的欄位值。 如果多個連接埠已訂閱的訊息，而且每個接收應用程式唯一的期望 MSH 區段值範圍內，這項覆寫功能就特別有用。  
  
 當然，所有其他[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]傳送和接收連接埠功能可供 HL7 訊息，以及一些功能，可能是唯一選取的連接埠類型，例如 MLLP 傳送連接埠參數。 相關範例[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]功能是能夠套用至外寄訊息的轉換對應。  
  
## <a name="how-routing-works"></a>路由的運作方式

[!INCLUDE[btaBTAHL7NoNumber_md](../../includes/btabtahl7nonumber-md.md)]路由 HL7 訊息根據 MessageBox 資料庫所管理的訂用帳戶的執行個體。 這些訂用帳戶會使用您所定義的篩選器，每個傳送埠。 範例篩選器可能會包括路由以在接收連接埠識別碼和/或 HL7 訊息類型 (ADT ^ 將 adt^a03，例如) 及/或傳送應用程式 （MSH3.1 值）。  
  
 除了設定[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]訂用帳戶，您需要執行一些 HL7 特定訊息的組態會影響 HL7 訊息執行個體，做為[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]路由傳送。 此額外設定可讓您套用唯一 HL7 驗證規則、 自動產生的通知，以及能夠覆寫 MSH 值。 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] 適用於此合作對象層級的設定。 您需要定義合作對象，BizTalk 總管 中的，並執行相關的 HL7 組態內[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]組態總管。  
  
 若要套用至多個訂閱的訊息的傳送埠的唯一 HL7 傳訊組態 （例如驗證或 MSH 覆寫），您需要建立合作對象之間的關聯和傳送埠。 您可將合作對象-傳送埠關聯設定為 [BizTalk 總管] 中的合作對象屬性中。  
  
 如果您不需要將訊息路由 HL7 至多個傳送埠，或將唯一 HL7 處理組態套用至多個傳送埠，您可以避免將合作對象與傳送埠產生關聯的步驟。 在此情況下，[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]關聯接收 HL7 訊息 (MSH 3.1) 中的應用程式欄位透過其 HL7 傳訊組態的合作對象。 這種情況下是最有可能發生在 HL7 interrogative （要求/回應） 訊息交換。  
  
## <a name="see-also"></a>另請參閱  
 [訊息驗證](../../adapters-and-accelerators/accelerator-hl7/message-validation.md)