---
title: 提升的效能，封存和清除程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- archiving [Tracking database], system performance
- DTA Purge and Archive job, performance
- purging, limitations
- performance, archiving
- performance, purging
- purging, system performance
ms.assetid: d65da58d-65e0-4f6c-8b15-5d4448049b42
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3876021fec4d604960d672671cab8bf4be1dc0a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257838"
---
# <a name="improving-the-performance-of-the-archiving-and-purging-process"></a>改善封存及清除程序的效能
視您設計 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實例的情況、[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實例處理訊息的大小和數量以及您設定的追蹤方式而定，儲存在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫中的資料量可能會非常快速地擴增。 將資料庫大小保持在狀況良好的限度，處理起來會更有效率，而且系統中的資料量也能隨時維持正常水準。 這樣就可以提供有效率且一致的效能。 將此程序自動化，可讓您省卻手動維護資料庫的負擔。  
  
## <a name="configuring-a-healthy-environment"></a>設定狀況良好的環境  
 您用於維護良好 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境的策略，高度依賴您特定的實例及所用的硬體。 要監控的主要事項為「BizTalk 追蹤」(BizTalkDTADb) 資料庫的成長率及大小。 追蹤資料庫的少數幾個資料表佔有資料庫大小的大部分，因此會在執行階段影響效能。  
  
 依據現有追蹤點的多寡、有多少不同的訊息在使用中、訊息大小和使用的訊息內文追蹤層級，您可以設定同樣的實例來產生大為不同的追蹤資料數量。 以下是一些需要監控的重要因數：  
  
-   追蹤點數目 - 例如管線、協調流程和連接埠  
  
-   追蹤的訊息屬性數目  
  
-   每個內送訊息的訊息數目  
  
-   訊息大小  
  
-   傳輸速率 (平均與尖峰)  
  
-   訊息內文追蹤組態  
  
 在考慮自動封存和清除資料時，請考慮您需要在追蹤資料庫中保留多少即時資料。 您必須視環境需要微調「DTA 清除與封存」工作參數，讓清除效能可以支援即時資料的目標數量，而不致降低效能。  
  
 「DTA 清除與封存」工作可以在指定的時間間隔內清除特定的資料量。 工作的容量取決於執行的實例、目前的資料庫大小和硬體。 若要擁有穩定的環境，您必須在內送追蹤資料的產生與清除之間取得平衡。 在測試環境中，您可以變動資料的存留窗期和清除工作的頻率來找到平衡。 在平衡狀態中，系統將會傳送持續性輸送量。 您的目標就是要在 BizTalk 追蹤資料庫資料表大小會造成持續的重大效能問題之前，提供足夠的緩衝區。  
  
## <a name="performance-limitations"></a>效能限制  
 不是所有的實例都會相應調整清除效能。 任何實例都可能產生不斷增加的追蹤資料數量。 一貫以較低的速率清除追蹤資料時，追蹤資料庫大小會增長，並且進一步讓清除效能變得更糟。  
  
 在無法維持負載的情況下，複製訊息內文的動作也會變得更慢，並且還可能在 MessageBox 資料庫造成積存現象。 就極端的情況而論，每日的訊息內文複製和追蹤可能會產生即使其中包含相關的執行個體資訊、卻沒有訊息內文的封存。 基本上，高負載期間會和低負載期間交替出現，讓工作可以在低負載期間跟上進度。  
  
 由於持續清除資料庫並壓縮儲存的追蹤資料，封存和清除 BizTalk 追蹤資料庫應該會大幅降低發生無法維持負載之情況的可能性。 這些程序將大幅減少手動介入的需要。  
  
## <a name="see-also"></a>另請參閱  
 [封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)