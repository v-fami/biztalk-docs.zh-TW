---
title: 監視工作的常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2f9f56a-c839-4108-933d-69b00a1e3817
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d91a49393e2b43c9cf39add35e06c5bd864782e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22301902"
---
# <a name="routine-monitoring-tasks"></a>例行監視工作
在定期排定執行下列監視工作將會協助您維持您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構操作就緒。  
  
## <a name="daily-monitoring-tasks"></a>每日監視工作  
  
-   檢閱所有未解決的警示。  
  
-   使用**群組中樞**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來調查協調流程、 連接埠和訊息失敗。 **群組中樞**頁面會提供目前即時狀態系統，在 MessageBox 資料庫中存取資料的存取權。 您可檢視所有服務執行個體 (如協調流程、連接埠和傳訊)，及其關聯的訊息。 使用**群組中樞**頁面，您可以執行下列活動：  
  
    -   查看目前執行中服務執行個體，例如協調流程和傳訊，以及其相關聯的訊息。  
  
    -   查看 MessageBox 資料庫中的目前資料與系統即時狀態檢視。  
  
    -   擱置、終止與繼續服務執行個體。  
  
     如需有關使用**群組中樞**頁面上，請參閱[http://go.microsoft.com/fwlink/?LinkId=155281](http://go.microsoft.com/fwlink/?LinkId=155281)。  
  
-   檢視警告 (選擇性)。  
  
 如需詳細資訊，請參閱[檢查清單： 執行每日維護檢查](../technical-guides/checklist-performing-daily-maintenance-checks.md)。  
  
## <a name="weekly-monitoring-tasks"></a>每週的監視工作  
  
-   檢閱事件記錄檔中每週至少一次。 這項工作的原因是為了防止問題，例如讓未偵測到的 DBNetLib 錯誤。 除非您有非常低的延遲系統，可能會移沒有通知服務中斷。 不過，某些錯誤可能更大的問題 （適用於例如太多主機或 BizTalk Server 伺服器的訊息方塊中，效能問題，SQL 方塊等數目）。  
  
 如需詳細資訊，請參閱[檢查清單： 執行每週維護檢查](../technical-guides/checklist-performing-weekly-maintenance-checks.md)。  
  
## <a name="as-needed-tasks"></a>視需要的工作  
  
-   修改規則，自訂的監視您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構。  
  
-   執行記錄檔的效能分析工具 (PAL)。 如果您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署是相當常數 （例如，新交易夥伴並未定期，加入新的程式碼未部署），您可能會執行 Perfmon 及 PAL 一季一次，或甚至是每隔六個月。 如果您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署變更更頻繁，您可能要執行 Perfmon PAL 每隔幾個月要與基準比較。 如需有關 PAL 的詳細資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。  
  
-   執行效能監視器每隔幾個月內，一季一次，或甚至是每隔六個月，根據變更的數目而定會發生在您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。  
  
-   執行 BizTalk Server Best Practices Analyzer 時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署的變更 （例如，新增新的應用程式） 或建立新的主機。 您可以下載 BizTalk Server Best Practices Analyzer 在[http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317)。  
  
-   執行[BizTalk MsgBoxViewer 工具](http://go.microsoft.com/fwlink/?LinkId=151930)(http://go.microsoft.com/fwlink/?LinkId=151930)。 此工具會分析 BizTalk MessageBox 資料庫與其他資料庫，並會產生 HTML 報表包含警告，如果與資料庫相關的任何，和其他資訊。  
  
    > [!TIP]  
    >  您也可以儲存供稍後使用的報表。 與 BizTalk 應用程式的問題進行疑難排解時，這些報表可能會有用。  
  
    > [!NOTE]  
    >  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
-   執行[結束字元工具](http://go.microsoft.com/fwlink/?LinkId=151931)(http://go.microsoft.com/fwlink/?LinkId=151931)。 此工具可讓使用者輕鬆地解決 BizTalk MsgBoxViewer 工具所識別的任何問題。 如需結束字元工具如何與 BizTalk MsgBoxViewer 工具整合的詳細資訊，請參閱[解決 BizTalk MsgBoxViewer 所識別的問題使用 BizTalk 結束字元](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932)。  
  
    > [!NOTE]  
    >  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="annual-monitoring-tasks"></a>每年的監視工作  
  
-   檢閱效能監視的您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構。  
  
-   建立計劃在監視中進行任何所需的變更。  
  
## <a name="see-also"></a>另請參閱  
 [例行的維護工作檢查清單](../technical-guides/routine-maintenance-checklists.md)