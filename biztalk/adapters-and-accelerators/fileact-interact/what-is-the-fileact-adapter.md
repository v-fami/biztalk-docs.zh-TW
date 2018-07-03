---
title: 何謂 FileAct 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05ec8f1e-57f9-4e2d-ab8b-22b5c4b28055
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc6fe9b28e4ea2b5eee087b61866827a766c3e3f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971487"
---
# <a name="what-is-the-fileact-adapter"></a>何謂 FileAct 配接器？
FileAct 配接器的 SWIFTNet 提供 BizTalk Server 與協會之間的連線能力的全球 Interbank 財務電信 (SWIFT) 安全 IP 網路 (SIPN) 傳輸檔案。 SIPN 傳輸安全的私人網路連線到金融機構、 金融業基礎結構和客戶的郵件和檔案。 FileAct 配接器使用 SWIFTNet 連結 (SNL) 應用程式開發介面 (API) s 要連接到 SIPN。  
  
 FileAct 配接器安全地提供 SWIFT 參與者的機制，並可靠地交換檔案和這些檔案的相關資訊。 它支援下列功能：  
  
-   傳送檔案至 SWIFTNet 使用者  
  
-   SWIFTNet 使用者從擷取的檔案  
  
-   確認檔案接收者收到的傳遞通知  
  
-   中止的進行中的傳輸  
  
-   檔案傳輸狀態監視  
  
-   並行的檔案傳輸  
  
-   資料的真實性和完整性的保證  
  
-   在傳輸過程中的檔案資料的機密性  
  
-   不可否認性的檔案傳輸  
  
-   時間戳記  
  
## <a name="the-fileact-service"></a>FileAct 服務  
 FileAct 配接器的 SWIFTNet 提供安全且可靠地傳輸檔案，例如批次的結構化的財務訊息或大型報表。 應用程式通常會包含重複的信用額度傳輸，例如年金或薪資付款、 證券附加價值的資訊和報告和法規報告。 SWIFTNet FileAct 提供各種不同的傳訊模式：  
  
- **儲存和轉寄檔案傳輸。** SWIFTNet FileAct 儲存和轉送功能會移除不確定性和擔心您的回覆者便都在線上時傳送檔案，請將您的不便。 當收件者已準備好接收其傳遞檔案。 如此一來，它會提供將檔案傳送到大量的回覆者便，其中有些可能會在不同時區的理想方式。  
  
- **即時的檔案傳輸。** 即時傳訊提供低成本替代方式來儲存和轉送目的地為傳輸時都在線上的回覆者便的檔案。 如此一來，它是適合用來傳送檔案至幾個大型的回覆者便或市場的基礎結構。  
  
- **擷取即時的檔案。** 這是通常用來擷取檔案的工作站為基礎的系統內容中，並經常搭配 SWIFTNet 瀏覽互動服務。 我們將支援這個模式。  
  
  （在以檔案的方式為單位） 的選擇性 SWIFTNet FileAct 功能包括：  
  
- **訊息優先權。** 檔案傳輸在訊息中，以提供適當處理您的回覆者便可標示為 「 Urgent 」。  
  
- **交貨通知 （即時和儲存和轉寄的模式）。** 提供您的對應已收到您的檔案的確認。  
  
- **不可否認性的發出和接收。** 發生爭議，可讓 SWIFT 確認檔案傳輸未宣告為會發生。  
  
  標準的 SWIFTNet FileAct 功能包括 SWIFTNet PKI 安全性<strong>。</strong> SWIFTNet FileAct 受到 SWIFTNet PKI，並提供訊息驗證和完整性控制。  
  
  所有的訊息和交換 SWIFTNet 上的檔案進行一組常用的檢查，以確保沒有任何使用者可以略過安全性、 驗證和路由規則的平台。 SWIFTAlliance 閘道 (SAG) 應用程式會執行這些檢查。  
  
## <a name="see-also"></a>另請參閱  
 [開始使用 FileAct 和 InterAct 配接器](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)   
 [何謂 SWIFTNet？](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md)   
 [何謂 InterAct 配接器？](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)