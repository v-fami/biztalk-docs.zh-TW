---
title: MessageBox 延遲問題疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9eb5789-80bd-40d4-8c27-7ae117fd9232
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e37fc970230bf218bcfd820611fb6b87322e535
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279870"
---
# <a name="troubleshooting-messagebox-latency-issues"></a>MessageBox 延遲問題疑難排解
在理想的世界裡，所有的訊息都應該在發佈到 MessageBox 資料庫時就進行處理和傳遞，這樣 MessageBox 資料庫的大小永遠都不會過度膨脹。 負責定期清除 MessageBox 資料庫資料表的 SQL 代理程式工作，會將 MessageBox 中不再受到參考的訊息立即移除。  
  
 不過，在真實世界的案例中，通常不是以可預期的線性方式接收訊息，所以 SQL 代理程式工作需要時間來清除 MessageBox 資料庫資料表。  
  
 因此，在某些案例中，MessageBox 可能會膨脹地相當快速。  
  
 下列情況可能會導致 MessageBox 過度膨脹而妨礙了整體效能：  
  
-   **具有 「 允許主控件追蹤 」 設定選項的 Biztalk 主控件執行個體已停止**。 這是負責將追蹤資料從 MessageBox 資料庫移至 BizTalk 追蹤資料庫 (BizTalkDTADb) 的主控件。  
  
-   **SQL Server 代理程式未執行**這種情況不執行 SQL 工作負責將資料從 MessageBox 資料庫移到 BizTalkDTADb 資料庫 [並且之後會清除在 MessageBox 中移動的資料]。 SQL 代理程式服務必須隨時都在執行，才能避免這種問題。  
  
-   **SQL Server 作業已停用**即使 SQL Server Agent 正在執行，請務必無預設 SQL Server 工作停用。  
  
-   **BizTalkDTADb 資料庫過度膨脹**這種情況，BizTalkDTADb 資料庫變得十分龐大，而導致插入 BizTalkDTADb 資料庫需要更長時間。 發生這種情況時，「追蹤資料傳遞服務」(Tracking Data Delivery Service，TDDS) 速度會變慢，導致 MessageBox 資料庫的待處理項目增多。 為了避免這個問題，您必須定期在 BizTalkDTADb 資料庫上執行 SQL 伺服器封存並將工作清除。  
  
-   **磁碟 I/O 過度延遲**如果 MessageBox 資料庫的資料的傳入速度會比系統能夠處理更快，並將資料移到 BizTalkDTADb 資料庫中，待處理項目可以建置在 MessageBox 資料庫。 如果待處理的項目持續增多而無緩解，就會造成嚴重的問題，系統效能可能隨時間增長而每況愈下。 一種紓解這個問題的方式，是安裝速度更快的磁碟及 (或) 升級硬體，以協助確保系統可以從訊息積存的情況復原。  
  
## <a name="plan-for-the-future"></a>計畫未來  
 即使遵守了上述所有的最佳作法，隨著時間增長，移到 BizTalkDTADb 資料庫的追蹤資料量仍會累積成很大的量。 您必須實作資料庫維護計畫，以定期封存追蹤資料，使系統仍可保持最佳效能。  
  
 可保留在 BizTalkDTADb 資料庫中的歷程資料量，是依照系統所處理的訊息量而定。 對於工作量及輸送量不會暴增的系統而言，這個資料庫膨脹的速度較慢，可在 BizTalkDTADb 資料庫中保留較多的歷程資料。  
  
 建議您在 BizTalkDTADb 資料庫中保留最少量的資料，如此就不會影響執行階段的效能。