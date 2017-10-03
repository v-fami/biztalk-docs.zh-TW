---
title: "限制查詢及擷取清單 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, querying limitations
- querying, limitations [JD Edwards OneWorld adapters]
ms.assetid: 1b6f5d2a-d1e2-4c78-8f4a-f00d10f008b9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f2e0f813a793aa05756ef52925081375203f2f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-when-querying-and-retrieving-lists"></a>查詢及擷取清單的限制
JD Edwards OneWorld 通訊架構是單一訊息、單一回應的架構。 您不能傳回訊息清單或陣列。 基底程式碼是 C++，它會以單一結構的指標呼叫、在結構中進行變更，然後再結束。  
  
## <a name="querying-and-retrieving-lists"></a>查詢及擷取清單  
 由於 JD Edwards OneWorld 商務功能架構的限制，因此您不能使用 Microsoft BizTalk Adapter for JD Edwards OneWorld 根據搜尋準則來查詢及擷取記錄清單。  
  
 在 JD Edwards OneWorld 中，資料庫連線是利用一組專屬 (且複雜) 的內部功能呼叫來提供。 這些呼叫會透過要求非常明確及低階的呼叫建立要擷取或更新的資料行清單，以遮罩基底資料庫版本，並建立適用於排序或選擇的特定結構。 API 的集合不會透過 Java 或其他任何連線方法公開，因此記錄集無法透過商務功能來處理。  
  
 在 JD Edwards OneWorld 工具組內，您可以建立處理單一記錄或操作一組記錄的商務功能；不過，存取 JD Edwards OneWorld 工具外部的項目清單更為困難。  
  
 若要解決此問題，您可以建立根據查詢傳回記錄索引鍵清單的自訂商務功能。 您必須分割清單，因為 JDENET (JD Edwards OneWorld 內部專屬訊息 API) 對管理大型或未繫結結果集的訊息緩衝區大小有限制。 用戶端程式碼必須逐一查看對商務功能的後續呼叫 (或對其執行迴圈)，直到傳回指標，指出清單是完整的為止。  
  
## <a name="controlling-iteration"></a>控制反覆項目  
 JD Edwards OneWorld 商務功能的所有呼叫都沒有狀態，因此商務功能無法因應要求維護開啟的資料指標並傳回其他資料列。 每次呼叫時都必須將位置資訊傳遞至 JD Edwards OneWorld XE 商務功能。  
  
 以下列出用來控制反覆項目的技術：  
  
-   在 JD Edwards OneWorld 端，將結果集寫入暫存儲存檔案，這個檔案會傳回可在後續呼叫中提供的 ID (例如檔案名稱或工作號碼)，以及用來放置資料指標的記錄編號。 任何後續呼叫都會依據傳入的記錄編號放入清單內。  
  
    > [!NOTE]
    >  透過 BizTalk Adapter for JD Edwards OneWorld 呼叫可以保持負載平衡；不過，這些呼叫最後會由單一應用程式伺服器根據認證和呼叫的商務功能來處理。 因此，如果呼叫在伺服器上建立了暫存儲存檔案，其他呼叫都會由相同的伺服器處理。 如需詳細資訊，請參閱《JD Edwards OneWorld CNC 指南》(JD Edwards OneWorld CNC Guides) 中的＜物件組態對應＞(Object Configuration Mapping)。  
  
-   位置資訊 (例如主索引鍵值) 可在第二個和後續的呼叫中傳回，而且查詢可以根據索引鍵重新發出，做為額外的參數。 這個方法可用於 BizTalk Adapter for JD Edwards OneWorld 的儲存機制瀏覽程式碼。  
  
    > [!NOTE]
    >  在前兩項技術中，建議的方法是使用主索引鍵值並重新發出查詢。 這種方法需要最少量的程式碼，而且會對資料庫造成最佳化和快取負荷。  
  
-   呼叫端應用程式可以儲存一份主索引鍵 (例如交互參照).的清單。 例如，如果客戶關係管理 (CRM) 系統建立了客戶記錄，然後使用商務功能呼叫將它加入到 JD Edwards OneWorld 中，則加入客戶記錄的商務功能將會設定 AN8 欄位 (簡短的位址編號) 的值，並顯示在傳回緩衝區中。 接著這個編號就可以寫入原始客戶記錄上的參考欄位，或是儲存在自訂的交互參照資料表中。  
  
-   JD Edwards OneWorld 中的所有主要記錄大部分都有尋查或替代索引鍵的概念。 這個索引鍵可以用來儲存呼叫端系統的索引鍵資訊。 商務功能可以在 JD Edwards OneWorld 端執行尋查作業。 將參數傳遞到商務功能以建立客戶記錄時，將會設定完整的索引鍵值。  
  
 如需這些概念的詳細資訊，請參閱 JD Edwards OneWorld 說明系統中的＜互通性＞(Interoperability) 主題。  
  
## <a name="see-also"></a>另請參閱  
 [規劃與架構](../core/planning-and-architecture17.md)