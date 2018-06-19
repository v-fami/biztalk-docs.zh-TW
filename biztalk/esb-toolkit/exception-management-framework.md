---
title: 例外狀況管理架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b5aebc0-2467-4f48-a385-056507ed1c1e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4d4d19caebb667e822b15b937d9045a26493a57
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008239"
---
# <a name="exception-management-framework"></a>例外狀況管理架構
ESB 例外狀況管理架構提供一個統一的訊息導向錯誤產生機制，來管理所有 BizTalk Server 環境中可能發生的例外狀況。 在 ESB 例外狀況管理架構可以接收透過例外狀況 Publishing Service，除了從 BizTalk Server 失敗訊息路由機制的訊息發佈的例外狀況訊息。  
  
 架構會提供應用程式開發介面，用於錯誤訊息建立、 發行集及管理從協調流程，複寫 BizTalk Server 2006 第一次引進的 BizTalk Server 的失敗的訊息路由功能。 此外，架構提供了功能正規化充實，套用商務活動監控 (BAM) 追蹤及發行最終輸出到顯示的例外狀況管理資料庫以及 ESB 中報告的所有例外狀況管理入口網站。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含下列管線元件可支援 ESB 例外狀況管理架構：  
  
-   **例外狀況錯誤處理器管線元件。** 這個元件是關聯 ESB 例外狀況匝道的管線的一部分。 此匝道訂閱所有 ESB 產生錯誤訊息，以及 BizTalk Server 失敗訊息路由機制所產生的例外狀況。 元件路由錯誤訊息至 ESB 例外狀況管理 ESB 管理入口網站資料庫，或可以設定為路由到其他位置。 管線元件也會加速功能的所有錯誤訊息和例外狀況與中繼資料，並將其正規化成通用格式。  
  
-   **BAM 追蹤的管線元件。** 這個元件會攔截，並記錄在 BizTalk Server BAM 子系統內的例外狀況資訊會以獨佔方式使用例外狀況錯誤處理器中的管線例外狀況管理架構。 隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例會示範如何使用 BAM 做為選擇性的追蹤功能，如例外狀況資訊。  
  
 如需例外狀況管理架構的詳細資訊，請參閱[使用 ESB 例外狀況管理](../esb-toolkit/using-esb-exception-management.md)。