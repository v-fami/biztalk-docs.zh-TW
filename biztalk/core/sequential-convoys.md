---
title: "循序群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- convoy sets
- correlation sets, sequential receive tasks
ms.assetid: f05ff42c-2236-42a3-8166-19700e0c3d97
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 329d0f56d9f092cd146a900c42ed48d5206a6393
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sequential-convoys"></a>循序群組
循序群組可讓多個單一訊息聯結在一起，以達成所需的結果。 循序群組是具有預先定義順序的相關訊息組。 雖然訊息不需要完全相同，但 BizTalk Server 必須以循序方式接收這些訊息。  
  
 例如，假設線上零售公司在一天當中，接到從直屬客戶以及經銷商傳來的新訂單。 所有在下午 2:00 之前接到的訂單都必須以單一批次傳送給倉庫，且必須保存接收訂單的順序。 這樣如果倉庫有缺貨的情況，較早接到的訂單將擁有優先權。 批次訂單的建立方式，是將當天的所有訂單組合到單一檔案中，並附上批次標頭資訊。 在下午 2:00 時，當天所有的訂單都會傳送到倉庫進行處理。 在下午 2:00 以後收到的所有訂單都將放入新的批次，等候次日處理。  
  
 前述的案例是需要對內送訊息進行循序群組處理的範例。 根據商務需求指出，在特定日下午 2:00 之前接到的所有單一訂單，都應該合併批次處理。 為此，第一個收到的訊息必須啟動新的協調流程執行個體，並初始化相互關聯集合。 此時，如果收到該訊息類型的其他訂單，都會路由至已經執行的協調流程執行個體。 若要達成此目的，您將**接聽**圖形 (包含**接收**圖形和**延遲**圖形) 內**迴圈**圖形。 在到達延遲之後，迴圈就會結束。 這樣可以在相同的商務程序中接收未知數目的訂單。  
  
## <a name="implementing-sequential-convoys"></a>實作循序群組  
 您可以使用 BizTalk Server 中的「相互關聯的循序接收」傳訊設計模式來實作循序群組。 相互關聯的循序接收是與之前的接收相互關聯的接收行為。  
  
 如果接收的相互關聯集合是由其他接收初始化，就會發生群組處理。  
  
 對於需要群組處理的接收而言，適用下列的限制：  
  
-   構成特定接收之循序群組集合的相互關聯集合必須由之前的接收初始化。  
  
-   需要循序群組處理之接收的連接埠，必須與初始化群組集合之接收的連接埠相同。 跨連結埠的群組不受支援。  
  
-   需要群組處理之接收的訊息類型，必須符合初始化群組集合之接收的訊息類型，除非接收陳述式是在排序的傳遞連接埠上運作。  
  
-   參與循序群組的所有接收，都必須遵循由初始化接收所初始化 (或遵循) 的所有相互關聯集合，除非是在排序的傳遞連接埠上運作。  
  
-   如果循序群組是由啟動接收陳述式所初始化，則啟動接收不能具有篩選條件運算式，除非是在排序的傳遞連接埠上運作。  
  
-   如果循序群組是由啟動接收所初始化，則其後的接收不能位在巢狀的協調流程內。  
  
 如需循序群組實作的範例，請參閱[彙總工具 （BizTalk Server 範例）](../core/aggregator-biztalk-server-sample.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用群組實例](../core/working-with-convoy-scenarios.md)   
 [平行群組](../core/parallel-convoys.md)