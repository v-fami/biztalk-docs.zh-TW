---
title: "動態解析和路由概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9a32491-132b-4b25-ac8c-4a927052f0be
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 341b8389530ac85fdc459816f5691f3b814fbd56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-resolution-and-routing-overview"></a>動態解析和路由概觀
ESB 解析程式類別支援下列執行階段解析：  
  
-   訊息傳遞端點  
  
-   轉換的對應  
  
-   端點組態  
  
-   自訂的服務中繼資料  
  
-   伺服器端行程  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]嘗試解析對應和端點的訊息到達時使用解析程式的連接字串。 這些連接字串可能存在於路線的 SOAP 標頭的訊息到達時，或它們可能會在自訂管線中使用下列管線元件的其中一個設定時： ESB 行程選取器中，ESB 發送器或 ESB 發送器反組譯。 使用 ESB 解析器和配接器提供者架構元件的 「 在 just-in-time 」 (JIT) 解析功能在處理生命週期的更新版本中進行解析。  
  
 比方說，如果動態轉換代理程式收到的訊息，必須將對應，但尚未決定對應名稱，它會嘗試使用相關聯的解析程式執行的解決方式。 如果 JIT 解析失敗，這會歸類為錯誤，系統會產生例外狀況訊息。  
  
 下列資料存放區或解析機制，可以查詢解析器和配接器提供者架構：  
  
-   硬式編碼對應或端點都不會發生動態結案不  
  
-   商務規則引擎 (BRE) 原則  
  
-   實作自訂組件**IResolveProvider**介面  
  
-   在訊息上的 XPath 查詢  
  
-   通用描述、 探索與整合 (UDDI) 查閱