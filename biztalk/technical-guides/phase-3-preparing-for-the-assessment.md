---
title: 階段 3： 準備評定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d153ed62-f2cc-4080-8912-c98ecdd329f5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 890047f6a13352d89d33d9514883dc20eacd4001
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22301838"
---
# <a name="phase-3-preparing-for-the-assessment"></a>階段 3： 準備進行評估
準備效能評估階段可以視為 「 範圍 」 階段的 「 作法 」 和 「 如何 」 計劃 」 階段的 「 時機 」。 此時效能評定，所有專案關係人應該均同意 engagement 和計劃的範圍進行實驗室。 它是在其中執行計畫，而會採取的步驟以準備好的效能實驗室執行效能評定的準備階段。  
  
 本主題說明 BizTalk Server 效能評定的準備階段的各個層面。  
  
## <a name="detailed-design-of-the-solution-platform"></a>詳細的方案平台設計  
 詳細的解決方案設計有助於進行通訊，並避免將來提高靈活度及所有活動的效用的假設。 您應該完整記載下列項目：  
  
-   **BizTalk Server 資料庫和如何分散在電腦**-SQL Server 效能是其中一個 BizTalk 伺服器的整體效能的關鍵因素。 如果 SQL Server 發生資源條件約束，這會影響 BizTalk Server 處理訊息的能力。 會影響 BizTalk 資料庫效能的主要因素是磁碟上裝載的速度。 將交易記錄檔和資料庫檔案的每個 BizTalk 資料庫到不同的磁碟機或 SAN LUN 可能會非常改善 BizTalk Server 的整體效能。 因此，很重要，這項資訊會記錄在更容易存取的方式。 將用於實際執行環境中的值應該記錄詳細的解決方案設計中。 下表提供如何完成的範例。  
  
    |BizTalk 資料庫|磁碟區名稱|檔案|LUN # 或 ML_ #|實體的 LUN 大小 (GB)|  
    |----------------------|-----------------|-----------|---------------------|------------------------------|  
    |MessageBox|Data_TempDb_1|TEMPDB、 主機和 MSDB 資料檔案|1|134|  
    ||Logs_TempDb_1|TEMPDB、 主機和 MSDB 交易記錄檔|2|134|  
    ||Data_BtsMsgBox|BizTalkMsgBoxDb 資料檔案|3|134|  
    ||Logs_BtsMsgBox|BizTalkMsgBoxDb 交易記錄檔|4|134|  
    |BAM|Data_TempDb_2|TEMPDB、 主機和 MSDB 資料檔案|5|67|  
    ||Logs_TempDb_2|TEMPDB、 主機和 MSDB 交易記錄檔|6|67|  
    ||Data_BAM|BAMPrimaryImport 資料檔案|7|134|  
    ||Logs_BAM|BAMPrimaryImport 的交易記錄檔|8|134|  
    |BizTalk 追蹤、 管理、 單一登入，以及規則引擎資料庫|Data_TempDb_3|TEMPDB、 MASTER、 MSDB、 BizTalkDTADb、 BizTalkMgmtDb、 ENTSSO 和 BizTalkRuleEngineDb 資料檔案|9|67|  
    ||Logs_TempDb_3|TEMPDB、 MASTER、 MSDB、 BizTalkDTADb、 BizTalkMgmtDb、 ENTSSO 和 BizTalkRuleEngineDb 交易記錄檔|10|67|  
  
-   **BizTalk 主控件的設計和每個主控件和其執行個體的描述。**  
  
-   **每個協調流程的描述。**  
  
-   **每個管線的描述。**  
  
-   **自訂元件，例如.NET 組件和 COM + 元件的描述。**  
  
## <a name="detailed-architecture-diagram"></a>詳細的架構圖  
 下圖說明可用於效能評定架構圖表。  
  
 ![BizTalk 架構圖](../technical-guides/media/architecturediagram.gif "ArchitectureDiagram")  
BizTalk 架構圖  
  
## <a name="message-flow-diagrams"></a>訊息流程圖  
 建立詳細的訊息流程圖表，為了避免混淆或 false 的假設，都應該在處理期間發生狀況的訊息。  
  
 當而加以進行歷程改善 BizTalk 解決方案，我們會傾向於認為訊息流程通過系統。 進行效能測試，因為流程的所有部分必須都視為潛在的瓶頸時，此訊息流程檢視方塊是特別重要。 訊息流程圖會使任何混淆或 false 的假設，都應該在每個測試期間發生狀況的訊息執行。  
  
 在下列範例中，建立使用簡單的 Visio 圖形，不論背景專案上的每個人都可以快速了解訊息如何抵達到系統、 解決方案的哪些部分互動的訊息，和最後其中訊息會落入之後處理程序。  
  
 ![Message Flow Diagram](../technical-guides/media/11c5afac-5c1b-42a5-8947-7c6d0ca4e2df.gif "11c5afac-5c1b-42a5-8947-7c6d0ca4e2df")  
訊息流程圖  
  
 建立訊息流程圖表時，應該考慮下列詳細資料：  
  
-   描述每一種訊息的時間所有產生的訊息會傳送，且所有相關的處理完成，直到到達接收位置的生命週期。  
  
-   描述如何處理錯誤狀況的變更時。  
  
-   包含有關相互關聯、 傳遞通知和通知詳細資料。  
  
-   包含有關在外部系統上的相依性的詳細資料。  
  
-   效能需求的資訊包括延遲和輸送量。  
  
## <a name="third-party-software-details"></a>第三方軟體詳細資料  
 詳細的解決方案設計的一部分，應該完整記錄所使用的所有非 Microsoft 軟體。  
  
## <a name="detailed-lab-hardware-stack"></a>詳細的實驗室硬體堆疊  
 建置在先前建立的高階硬體圖表上，下列硬體資訊應該是完整記錄：  
  
-   處理器  
  
    -   類型  
  
    -   速度  
  
    -   核心數目  
  
    -   超執行緒  
  
-   記憶體  
  
    -   Amount  
  
    -   速度  
  
    -   Parity  
  
-   網路  
  
    -   網路介面卡 (Nic) 數目  
  
    -   網路連線的速度  
  
-   SAN  
  
    -   在每台電腦的 SAN 卡數目  
  
    -   針對每個電腦和目的每個 LUN 的邏輯單元編號 (Lun) 的數目  
  
    -   速度的存放區域網路 (SAN) 卡  
  
    -   SAN 的介面卡的組態詳細資料  
  
    -   SAN 磁碟配置、 格式化和分割  
  
-   磁碟  
  
    -   每一部電腦的本機磁碟詳細資料  
  
    -   格式設定用於本機磁碟  
  
    -   資料分割的本機磁碟的詳細資料  
  
-   Cache  
  
    -   L2 快取容量  
  
    -   L3 快取容量  
  
## <a name="detailed-lab-software-stack"></a>詳細的實驗室軟體堆疊  
 應該記錄下列軟體的資訊：  
  
-   特定作業系統版本、 版本和架構  
  
-   特定的作業系統功能  
  
-   在每一部電腦上已安裝特定軟體  
  
-   特定驅動程式  
  
-   Service Pack 及其他更新  
  
-   如果兩者的差異的預設值使用的所有軟體和作業系統功能的組態值  
  
## <a name="see-also"></a>另請參閱  
 [效能評定階段](../technical-guides/phases-of-a-performance-assessment.md)