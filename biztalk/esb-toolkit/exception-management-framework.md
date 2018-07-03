---
title: 例外狀況管理架構 |Microsoft Docs
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
ms.openlocfilehash: 1fc334dd93c0ad53737b1fe36d50355cecae565a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017840"
---
# <a name="exception-management-framework"></a>例外狀況管理架構
ESB 例外狀況管理架構提供的統一的訊息導向的錯誤產生機制來管理所有 BizTalk Server 環境中可能發生的例外狀況。 ESB 例外狀況管理架構可以接收例外狀況發行服務，但除了訊息從 BizTalk Server 失敗訊息路由機制透過發佈的例外狀況訊息。  
  
 架構會提供錯誤訊息建立、 發行集，和從協調流程，將 BizTalk Server 2006 第一次引進的 BizTalk Server 的失敗的訊息路由功能的複寫管理的 API。 此外，「 架構 」 提供正規化豐富，將商務活動監控 (BAM) 追蹤和發行最終輸出到顯示的例外狀況管理資料庫和報告中的 ESB 套用的所有例外狀況的功能管理入口網站。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含下列管線元件可支援 ESB 例外狀況管理架構：  
  
- <strong>例外狀況錯誤處理器管線元件。</strong>此元件是使用 ESB 例外狀況出口匝相關聯的管線的一部分。 此出口匝訂閱所有的 ESB 產生錯誤訊息，以及 BizTalk Server 失敗訊息路由機制所產生的例外狀況。 元件路由錯誤訊息至 ESB 例外狀況管理 ESB 管理入口網站資料庫，或可以將它設定要路由到其他位置。 管線元件也會擴充所有錯誤訊息和例外狀況和中繼資料，並將它們正規化成常見的格式。  
  
- <strong>BAM 追蹤的管線元件。</strong>此元件會攔截並記錄例外狀況資訊的 BizTalk Server BAM 子系統內並完全由例外狀況管理架構內的例外狀況錯誤處理器管線。 隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例會示範如何使用 BAM 做為選擇性的追蹤功能，如例外狀況的詳細資訊。  
  
  如需有關例外狀況管理架構的詳細資訊，請參閱[使用 ESB 例外狀況管理](../esb-toolkit/using-esb-exception-management.md)。