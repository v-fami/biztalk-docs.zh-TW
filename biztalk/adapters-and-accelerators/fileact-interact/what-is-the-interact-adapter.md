---
title: 何謂 InterAct 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a09063df-c6c4-41b9-96a1-e5059777fa72
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fc2f29f08edda2fb8d2b0cf05f3ba5b2b786e8f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967079"
---
# <a name="what-is-the-interact-adapter"></a>何謂 InterAct 配接器？
SWIFTNet 互動配接器會提供訊息的傳輸中的 BizTalk Server 與 SWIFT 安全 IP 網路 (SIPN) 之間的連線。 SIPN 互連金融機構、 金融業基礎結構和客戶的安全私人網路傳輸訊息和檔案。 InterAct 配接器使用 SWIFTNet 連結 (SNL) 應用程式開發介面 (API) s 要連接到 SIPN。  
  
 SWIFTNet 互動提供安全且可靠的個別結構化財務訊息交換。 SWIFT 客戶的傳訊需求而有所不同，客戶，但也從訊息至訊息。  
  
 它支援下列功能：  
  
- PKI 安全性  
  
- 訊息驗證  
  
- 可設定的中央路由  
  
- 訊息優先順序  
  
- 存放與轉寄訊息的傳遞通知  
  
- 不可否認性的發出和回條。  
  
  您用於互動的介面卡 SWIFTNet 與外部提供的應用程式若要使用的互動功能。 此配接器有沒有要傳送，而且將不稽核和驗證訊息的內容，除了交換基本類型的訊息內容的相關知識。  
  
## <a name="interact-message-exchange"></a>InterAct 訊息交換  
 SWIFTNet 互動提供安全且可靠的個別結構化財務訊息交換。 SWIFT 客戶的傳訊需求而有所不同，客戶，但也從訊息至訊息。 SWIFTNet 互動，提供您廣泛的電信模式：  
  
- **儲存和轉寄的訊息。** SWIFTNet 互動的儲存和轉送功能被設計用於訊息目的地的大量的回覆者便，其中有可能不在線上，傳輸的時間。 它會移除的不確定性和擔心您的回覆者便為線上傳送訊息時所造成的不便。 當收件者已準備好接收其傳遞訊息。 如此一來，它會提供最理想的方式傳送到大量的回覆者便，其中有些可能會在不同的時區中的個別指示、 確認及報表。  
  
- **即時傳訊。** 即時傳訊提供儲存和轉送的訊息目的地為傳輸時都在線上的回覆者便是低成本替代方案。 如此一來，很適合用來傳送個別的指示、 確認及報告，幾個大型的回覆者便或市場基礎結構的訊息。  
  
  （根據訊息的訊息） 的選擇性 SWIFTNet 互動功能包括：  
  
- **訊息優先權。** 訊息在訊息中，以提供適當處理您的回覆者便可標示為 「 Urgent 」。  
  
- **交貨通知 （儲存和轉送模式）。** 提供您的對應已收到您的訊息的確認  
  
- **不可否認性的發出和接收。** 發生爭議，可讓 SWIFT 確認訊息交換未如宣告會發生。  
  
  標準的 SWIFTNet 互動功能包括 SWIFTNet PKI 安全性。 SWIFTNet FileAct 受到 SWIFTNet PKI，並提供訊息驗證和完整性控制。  
  
  所有的訊息和交換 SWIFTNet 上的檔案進行一組常用的檢查，以確保沒有任何使用者可以略過安全性、 驗證和路由規則的平台。 SWIFTAlliance 閘道 (SAG) 應用程式會執行這些檢查。  
  
## <a name="see-also"></a>另請參閱  
 [開始使用 FileAct 和 InterAct 配接器](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)   
 [何謂 SWIFTNet？](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md)   
 [何謂 FileAct 配接器？](../../adapters-and-accelerators/fileact-interact/what-is-the-fileact-adapter.md)