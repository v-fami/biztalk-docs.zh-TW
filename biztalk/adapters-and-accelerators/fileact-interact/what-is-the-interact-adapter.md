---
title: "什麼是互動配接器？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a09063df-c6c4-41b9-96a1-e5059777fa72
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25877b95a440faef802d3d2ba7861687d7e4b108
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-interact-adapter"></a>什麼是互動配接器？
SWIFTNet 互動配接器會提供 BizTalk Server 與 SWIFT 保護 IP 網路 (SIPN) 之間的連線傳送的訊息。 SIPN 傳輸連接金融機構、 財務產業的基礎結構和客戶在安全私人網路上的訊息和檔案。 InterAct 配接器會使用 SWIFTNet 連結 (SNL) 應用程式開發介面 (API) s 連接到 SIPN。  
  
 SWIFTNet 互動提供安全、 可靠的個別結構化財務訊息交換。 SWIFT 客戶傳訊需求不同客戶的但也從訊息至訊息。  
  
 它支援下列功能：  
  
-   PKI 安全性  
  
-   訊息驗證  
  
-   可設定的中央路由  
  
-   訊息優先順序  
  
-   存放與轉寄訊息的傳遞通知  
  
-   不可否認性的發出和接收。  
  
 您互動的介面卡的 SWIFTNet 搭配使用外部提供的應用程式使用互動功能。 此配接器不了解將傳輸，並不會稽核也不驗證訊息的內容，除了交換基本型別之訊息的內容。  
  
## <a name="interact-message-exchange"></a>InterAct 訊息交換  
 SWIFTNet 互動提供安全、 可靠的個別結構化財務訊息交換。 SWIFT 客戶傳訊需求不同客戶的但也從訊息至訊息。 SWIFTNet 互動提供廣泛的電信模式：  
  
-   **儲存和轉送訊息。** SWIFTNet 互動的儲存和轉送功能被設計用於目的地為大量的對應，許多使用者可能無法線上傳輸時訊息。 它會移除的不確定性和的擔心您的對應為線上傳送訊息時所造成的不便。 收件者已準備好接收它之後儘速傳遞訊息。 如此一來，它會提供將個別的指示、 確認及報表傳送到大量的對應，其中有些可能會在不同時區的理想方式。  
  
-   **即時訊息。** 即時訊息提供低成本的替代方式來儲存和轉送訊息目的地為傳輸的時間在線上的對應。 如此一來，很適合用來傳送個別的指示，確認和報表，少數的大型對應或行銷的基礎結構訊息。  
  
 （根據訊息的訊息） 的選擇性 SWIFTNet 互動功能包括：  
  
-   **訊息優先順序。** 訊息可以標示為 「 緊急 」，在訊息中，以提供適當處理您的對應。  
  
-   **傳遞通知 （儲存和轉送模式）。** 提供您的對應已收到訊息的確認  
  
-   **不可否認性的發出和接收。** 發生爭議，可讓 SWIFT 確認訊息交換未宣告為會發生。  
  
 標準的 SWIFTNet 互動功能包括 SWIFTNet PKI 安全性。 SWIFTNet FileAct 受到 SWIFTNet PKI，並提供訊息驗證和完整性控制。  
  
 所有的訊息和檔案上 SWIFTNet 交換接受一組常用的檢查，以確保沒有任何使用者可以略過安全性、 驗證和平台的路由規則。 SWIFTAlliance 閘道 (SAG) 應用程式會執行這些檢查。  
  
## <a name="see-also"></a>另請參閱  
 [開始使用 FileAct 和 InterAct Adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)   
 [SWIFTNet 是什麼？](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md)   
 [FileAct 配接器為何？](../../adapters-and-accelerators/fileact-interact/what-is-the-fileact-adapter.md)