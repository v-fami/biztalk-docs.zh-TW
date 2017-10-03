---
title: "規劃 BizTalk 解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30d56a04-966a-46b1-861d-f5be4e58b7d2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74b7cbe23a6fc818428478859ea021d4fbf38546
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-the-biztalk-solution"></a>規劃 BizTalk 解決方案
主要設計目標之一[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是容納最多處理的案例中，盡可能提供最大的彈性。 此絕佳的彈性，因為主要的 BizTalk 解決方案的開發人員所面臨的挑戰之一就是要判斷如何在中提供的功能的最佳使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]最符合其商務需求。 規劃[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以分成不同階段的以下摘要說明。  
  
## <a name="scoping-the-solution"></a>設定方案的範圍  
  
### <a name="performance-considerations"></a>效能考量  
 設定 BizTalk 方案的範圍時，請考慮下列：  
  
-   哪些配接器和/或加速器需要？  
  
-   在方案中實作協調流程的需求是什麼？  
  
-   文件輸送量需求： 方案的最大持續輸送量需求是什麼？  
  
-   延遲需求： 回應速度方案必須為請求-回應和要求-回應的案例？  
  
-   方案程度的文件的尖峰負載期間復原？  
  
-   方案的高可用性需求有哪些？  
  
-   解決方案的文件追蹤需求有哪些？  
  
-   任何相依的應用程式，例如遠端的 Web 服務或其他系統的效能特性有哪些？ 如果相依的應用程式執行無法跟上必要的負載然後整體系統效能會下降據此。  
  
-   將 BizTalk 應用程式耗用不相關資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]嗎？ 例如，如果 BizTalk 應用程式使用 SQL Server 資料庫使用 SQL 配接器中的資料表，資料表有效率地設定嗎？  
  
### <a name="hardware-considerations"></a>硬體考量  
 設定方案的範圍，當建立高階硬體圖表，包括下列各項：  
  
-   電腦架構 （例如 x86、 x64 和 IA64）  
  
-   （例如類型、 速度、 數字、 核心，以及使用超執行緒） 的 CPU 需求  
  
-   每一部電腦的 RAM 需求  
  
-   本機磁碟儲存體 （類型、 大小、 速度）  
  
-   SAN (存放裝置需求： 數字的 LUN。SAN 卡片類型）  
  
-   網路卡 (數字在每台電腦，100 mb (Mbps) 與 1 Gigabit (1 Gbps)。)  
  
-   防火牆會部署方案中的方式？  
  
-   會使用網路負載平衡硬體嗎？  
  
-   要叢集化是特定的電腦？  
  
-   您可會使用與 Microsoft HYPER-V Server 或任何其他虛擬化產品相關的虛擬環境嗎？  
  
## <a name="planning-the-solution"></a>規劃的解決方案  
  
### <a name="solution-milestones-timeline"></a>方案里程碑時間軸  
 完成 BizTalk 方案的特定層面的里程碑與建立排程。 設定特定的里程碑將會增加方案可能性及時完成。  
  
### <a name="non-microsoft-software-considerations"></a>非 Microsoft 軟體的考量  
 解決方案會使用非 Microsoft 軟體時，請考慮下列：  
  
-   判斷軟體或硬體所需的可取得。  
  
-   規劃容量，並調整大小以確保該非 Microsoft 軟體不會成為您的方案中的瓶頸。  
  
-   判斷安裝所需的非 Microsoft 軟體的動作計劃。  
  
-   建立計劃的設定和最佳化所需的非 Microsoft 軟體的動作。  
  
## <a name="preparing-for-the-solution"></a>準備方案  
 準備階段中包括下列項目：  
  
### <a name="detailed-design-of-the-solution-platform"></a>詳細的方案平台設計  
 詳細的解決方案設計有助於進行通訊，並避免將來提高靈活度及所有活動的效用的假設。 您應該完整記載下列項目：  
  
-   BizTalk Server 資料庫和如何分散在電腦中。  
  
-   BizTalk 主控件的設計和每個主控件和其執行個體的描述。  
  
-   每個協調流程的描述。  
  
-   每個管線的描述。  
  
-   自訂元件，例如.NET 組件和 COM + 元件的描述。  
  
 **訊息流程圖**  
  
 建立詳細的訊息流程圖表，以避免任何混淆或 false 的假設，都應該在處理期間發生狀況的訊息。 建立訊息流程圖表時，應該考慮下列詳細資料：  
  
-   描述每一種訊息的時間所有產生的訊息會傳送，且所有相關的處理完成，直到到達接收位置的生命週期。  
  
-   描述如何處理錯誤狀況的變更時。  
  
-   包含有關相互關聯、 傳遞通知和通知詳細資料。  
  
-   效能需求的資訊包括延遲和輸送量。  
  
 **非 Microsoft 軟體詳細資料**  
  
 詳細的解決方案設計的一部分，應該完整記錄所使用的所有非 Microsoft 軟體。  
  
 **詳細的硬體堆疊**  
  
 建置在先前建立的高層級硬體圖表上，下列硬體資訊應該是完整記錄：  
  
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
  
 **詳細的軟體堆疊**  
  
 應該記錄下列軟體的資訊：  
  
-   特定作業系統版本、 版本和架構  
  
-   特定的作業系統功能  
  
-   在每一部電腦上已安裝特定軟體  
  
-   特定驅動程式  
  
-   Service Pack 及其他更新  
  
-   如果兩者的差異的預設值使用的所有軟體和作業系統功能的組態值  
  
## <a name="building-out-the-environment-for-the-solution"></a>方案建置環境  
 詳細的安裝指示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和必要的相依性軟體可以在 BizTalk Server 安裝指南下載[BizTalk Server 2010 文件](http://go.microsoft.com/fwlink/?LinkId=183138)(http://go.microsoft.com/fwlink/ 嗎？LinkId = 183138)。  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BizTalk Server 層](../technical-guides/planning-the-biztalk-server-tier.md)