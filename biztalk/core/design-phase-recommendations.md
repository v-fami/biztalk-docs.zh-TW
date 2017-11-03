---
title: "設計階段建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3d183e-a6f3-47d0-90ac-99b12c064607
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0f361734aa7539f12940212a339b582bb4f2641
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="design-phase-recommendations"></a>設計階段建議
設計階段的主要產物，是為了驗證系統功能和效能而提供的系統和測試案例設計規格。 調查功能及測試的可行性是設計程序常見的一部分，其中包含初始的開發以及一些概念証明實作的一些早期測試 (在驗證設計的情況下)，如以下章節所述。  
  
## <a name="acquire-detailed-throughput-and-latency-profiles"></a>取得詳細的輸送量和延遲設定檔  
 在設計階段期間，以前一個專案階段效能發佈準則所依據的初始負載設定檔為基礎，建立詳細的輸送量和延遲設定檔。 如果可以，請從實際執行系統取得效能資料。 使用實際執行資料可提供實際的效能設定檔，可根據此種設定檔在此階段設計測試案例。 如果沒有實際執行資料可用，則必須從預期的負載情況推斷實際的設定檔。  
  
 在設計階段所建立的效能測試案例，必須包含能在實際執行時精確模擬系統之預期支援情況的效能設定檔，這點非常重要。 如需建立實際的持續性效能設定檔的詳細資訊，請參閱[何謂持續性效能？](../core/what-is-sustainable-performance.md)  
  
## <a name="investigate-performance-risk-mitigations"></a>調查效能風險防護  
 在需求階段期間，會辨識達到所要效能目標的風險，並指出可能的防護方法。  應該儘早在設計階段中調查風險及防護方法，如此在必要時才有時間變更設計。 每項辨識出的風險，都應該先藉由概念証明 (POC) 測試證明確有問題，然後再測試防護方法來評估其功效。  
  
 例如，假設舊版系統是使用 FTP 與其他系統通訊。 不過，以舊版 FTP 伺服器搭配 BizTalk Server FTP 配接器所能達到的輸送量層級來看，想要的輸送量 (在需求階段期間建立為發行準則) 很明顯是無法達成的。 若要緩解專案的風險，必須在需求階段期間確認下列方法：  
  
-   向上或向外延展 FTP 伺服器，並建立多個邏輯 FTP 位址，專供特定的訊息類型擴充負載。  
  
-   修改舊版系統，以在單一檔案中傳送許多訊息，以每個訊息傳輸的額外負荷降低批次  
  
-   修改舊版系統，以使用傳送速度比 FTP 快的其他通訊協定 (例如 MSMQ)。  
  
 在此範例中需要完成的第一項調查，是測試目前的 FTP 系統效能，證明有風險存在。 首先會建立及部署只會從 FTP 伺服器接收訊息的簡單的概念証明方案，然後對其套用 FTP 路徑所預期的實際執行負載設定檔。 如果伺服器可以維持所需的負載，則不會構成風險，也不需要進行更多調查。 如果不能維持所需的負載，則應該透過概念証明調查，來調查最可能解決這個問題、成本最低，專案風險又最少的方案。  
  
## <a name="refine-system-size-estimate"></a>調整系統大小估計  
 在設計階段期間所進行的調查，可提供有關系統效能功能的寶貴經驗資訊。  
  
 例如，讓我們繼續上述的範例，此範例中的 FTP 效能過低。 因為環境中已經包含使用 MSMQ 做為傳訊傳輸的系統，所以決定要將舊版系統修改為同樣使用 MSMQ。 不過，對運用 MSMQ 的新 POC 進行效能測試時，觀察到其中安裝 MessageBox 資料庫的 SQL 伺服器 CPU 幾乎經常達到 100% 的使用率，而您無法在 MSMQ 路徑上達到預期的輸送量。  
  
 假設 SQL Server 組態已針對應用程式進行最佳化，則 SQL Server 硬體的大小對於所需的輸送量而言明顯不足，需要重新調整系統的大小。 在這種狀況下，SQL Server 硬體需要新增 CPU、更換更快的 CPU，或兩者皆需要。  
  
## <a name="see-also"></a>另請參閱  
 [依階段的專案規劃建議](../core/project-planning-recommendations-by-phase.md)   
 [需求階段建議](../core/requirements-phase-recommendations.md)   
 [實作階段建議](../core/implementation-phase-recommendations.md)   
 [驗證階段建議](../core/verification-phase-recommendations.md)   
 [發行階段建議](../core/release-phase-recommendations.md)