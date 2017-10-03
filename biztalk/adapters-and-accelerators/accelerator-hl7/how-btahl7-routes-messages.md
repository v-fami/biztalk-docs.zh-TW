---
title: "BTAHL7 將訊息路由 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- routing, about routing
- routing, messages
- messages, routing
- BTAHL7, message routing
ms.assetid: 555696c7-6023-44eb-b13d-cf7527bbc92f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61dd223a014ae8ea7de35d8d73f1a7cf7ef35449
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-btahl7-routes-messages"></a>BTAHL7 將訊息路由
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 的訊息處理功能會利用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，但還擴充它 HL7 訊息需求所特定的數個方式。  

## <a name="routing-overview"></a>路由概觀

HL7 從企業營運 (LOB) 系統接收訊息，並可能會收到使用 MLLP 配接器。 MLLP 配接器至 LOB 系統連接[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]透過 TCP 連接埠，然後再將訊息傳送至 MLLP 配接器。

在**[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]和較舊版本**，HL7 MLLP 接收傳輸配接器等候的遠端連線到 MLLP LOB 系統。 LOB 系統遠端 LOB 系統連線時，一旦傳送訊息使用到 MLLP [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 具體來說： 

1. 遠端部署 LOB 系統連線至 MLLP 配接器在本機[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用 TCP 連接埠 
2. BTA4HL7 使用接收位置 MLLP 配接器接受連線 
3. 遠端部署 LOB 系統會傳遞一或多個訊息 
4. 遠端部署 LOB 系統中斷連接

在**[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]和較新版本**MLLP 配接器，由起始連接至 LOB 系統，然後 MLLP LOB 系統推播通知訊息接收。 換句話說，遠端 LOB 系統的連接，再將訊息傳送至 MLLP 而等候。 具體來說： 

1. 本機[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]連線到遠端的 LOB 系統使用 TCP 連接埠 
2. BTA4HL7 使用接收位置 MLLP 配接器會起始連線 
3. 遠端部署 LOB 系統會傳遞一或多個訊息 
4. 遠端部署 LOB 系統中斷連接 

為了回溯相容性，您可以使用原始的預設行為遠端 LOB 系統會起始連線。 此選項為 MLLP 中可設定接收位置屬性。 
 
一旦收到 HL7 訊息，然後提交給 HL7 接收管線。 此管線中，內 HL7 解譯器就會剖析訊息，並將驗證根據適當的結構描述定義和驗證設定將訊息。 此時，可能會有通知訊息 HL7 產生 （成功或錯誤），根據訊息和相關的通知設定的有效性。 從這裡，管線就會送出的訊息執行個體和選擇性通知至 MessageBox 資料庫，以便進一步處理和路由。  
  
 一旦在 MessageBox 資料庫中，抵達的訊息執行個體[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]檢查篩選器為基礎的訂閱，並將訊息路由傳送至一個或多個傳送埠 （可能是 MLLP 連接埠） 透過 HL7 傳送管線。 傳送管線會驗證訊息執行個體，以根據適當的結構描述定義和驗證組態。 除了驗證，很可能覆寫指定外寄訊息的 MSH 區段中的欄位值。 如果多個連接埠已訂閱訊息，而且每個接收應用程式的 MSH 區段值內的唯一期望，覆寫這項功能就特別有用。  
  
 當然，所有其他[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]傳送和接收埠將提供給 HL7 訊息，以及一些功能，可能是唯一選取的連接埠的型別，例如 MLLP 傳送埠參數的功能。 相關的範例[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]功能會將轉換對應套用至外寄訊息的能力。  
  
## <a name="how-routing-works"></a>路由的運作方式

[!INCLUDE[btaBTAHL7NoNumber_md](../../includes/btabtahl7nonumber-md.md)]路由 HL7 訊息根據管理 MessageBox 資料庫的訂用帳戶的執行個體。 這些訂用帳戶會使用您定義的篩選條件，每個傳送埠。 範例篩選器可能會包括路由基礎在接收連接埠 ID 及/或 HL7 訊息類型 (ADT ^ A03，例如) 和/或傳送應用程式 （MSH3.1 值）。  
  
 除了設定[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]訂用帳戶，您需要執行一些 HL7 特定訊息設定會影響 HL7 訊息執行個體做為[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]路由傳送。 此額外的設定可讓您套用唯一 HL7 驗證規則，自動產生的通知，並覆寫的 MSH 值的能力。 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]套用此設定在合作對象層級。 您需要定義合作對象在 BizTalk 總管 中，執行中的相關的 HL7 組態[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]Configuration 總管。  
  
 若要套用至多個訂閱訊息的傳送埠的唯一 HL7 訊息的組態 （例如，驗證或 MSH 覆寫），您需要建立合作對象之間的關聯和傳送埠。 將合作對象的傳送埠關聯設定為在 BizTalk 總管 中的合作對象屬性。  
  
 如果您不需要將訊息路由 HL7 至多個傳送埠，或唯一 HL7 處理設定套用至多個傳送埠，您可以排除的步驟，將合作對象與傳送埠產生關聯。 在此情況下，[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]合作對象關聯接收應用程式訊息中的欄位 HL7 (MSH 3.1) 透過其 HL7 訊息組態。 這種情況下是最有可能發生在 HL7 interrogative （要求/回應） 訊息交換。  
  
## <a name="see-also"></a>另請參閱  
 [訊息驗證](../../adapters-and-accelerators/accelerator-hl7/message-validation.md)