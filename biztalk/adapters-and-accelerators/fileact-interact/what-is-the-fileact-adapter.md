---
title: FileAct 配接器為何？ | Microsoft Docs
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
ms.openlocfilehash: 62b83fc723bbebce857eb442384b14179c1072ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225318"
---
# <a name="what-is-the-fileact-adapter"></a>FileAct 配接器為何？
SWIFTNet 的 FileAct 配接器提供 BizTalk Server 與協會之間連線的全球 Interbank 財務 Telecommunication (SWIFT) 保護 IP 網路 (SIPN) 傳輸檔案。 SIPN 傳輸透過安全的私人網路連接金融機構、 財務產業的基礎結構和客戶的訊息和檔案。 FileAct 配接器會使用 SWIFTNet 連結 (SNL) 應用程式開發介面 (API) s 連接到 SIPN。  
  
 FileAct 配接器的 SWIFT 參與者會安全地提供一個機制，並可靠地交換檔案和這些檔案的相關資訊。 它支援下列功能：  
  
-   將檔案傳送到 SWIFTNet 使用者  
  
-   SWIFTNet 使用者從擷取檔案  
  
-   確認收件者所接收的檔案傳遞通知  
  
-   中止的傳輸正在進行中  
  
-   檔案傳輸狀態監視  
  
-   並行的檔案傳輸  
  
-   資料的真實性和完整性 assurance  
  
-   在傳輸過程中的檔案資料的機密性  
  
-   不可否認性的檔案傳輸  
  
-   時間戳記  
  
## <a name="the-fileact-service"></a>FileAct 服務  
 SWIFTNet 的 FileAct 配接器提供的檔案，例如批次結構化之財務訊息或大型報表的安全而可靠的傳輸。 一般應用程式包含重複的信用額度傳送，例如 pension 或薪資付款、 股票所分配到加值資訊和報表，以及設定報告的法規。 SWIFTNet FileAct 提供各種不同的訊息模式：  
  
-   **儲存和轉送的檔案傳輸。** SWIFTNet FileAct 儲存和轉送功能中移除的不確定性和擔心對應您的時間在線上傳送檔案，您的不便。 收件者已準備好接收它之後儘速傳遞檔案。 如此一來，它會提供將檔案傳送到大量的對應，其中有些可能會在不同時區的理想方式。  
  
-   **即時的檔案傳輸。** 即時訊息提供低成本的替代方式來儲存和轉送的檔案傳輸的時間在線上的相關者為目標。 如此一來會適用於幾個大型的對應或市場基礎結構傳送檔案。  
  
-   **即時檔案擷取。** 這是通常用來擷取檔案的工作站系統內容中，且通常搭配 SWIFTNet 瀏覽互動服務。 我們將會支援這個模式。  
  
 （根據檔案的檔案） 的選擇性 SWIFTNet FileAct 功能包括：  
  
-   **訊息優先順序。** 檔案傳輸可以標示為 「 緊急 」，在訊息中，以提供適當處理您的對應。  
  
-   **傳遞通知 （即時和儲存和轉送模式）。** 提供您的對應已收到您的檔案的確認。  
  
-   **不可否認性的發出和接收。** 發生爭議，可讓 SWIFT 確認檔案傳送未宣告為會發生。  
  
 標準的 SWIFTNet FileAct 功能包括 SWIFTNet PKI 安全性 **。** SWIFTNet FileAct 受到 SWIFTNet PKI，並提供訊息驗證和完整性控制。  
  
 所有的訊息和檔案上 SWIFTNet 交換接受一組常用的檢查，以確保沒有任何使用者可以略過安全性、 驗證和平台的路由規則。 SWIFTAlliance 閘道 (SAG) 應用程式會執行這些檢查。  
  
## <a name="see-also"></a>另請參閱  
 [開始使用 FileAct 和 InterAct Adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)   
 [SWIFTNet 是什麼？](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md)   
 [什麼是互動配接器？](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)