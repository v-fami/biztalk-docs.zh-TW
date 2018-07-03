---
title: 監視工作的常式 |Microsoft Docs
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
ms.openlocfilehash: d500e79cdf20c6a1914708976101715c2f00ae69
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001655"
---
# <a name="routine-monitoring-tasks"></a>例行性監視工作
執行下列監視工作依定期排程將會協助您保留您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構，操作。  
  
## <a name="daily-monitoring-tasks"></a>每日監視工作  
  
- 檢閱所有未解決的警示。  
  
- 使用**群組中樞**頁面中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]調查協調流程、 連接埠和訊息失敗的管理主控台。 **群組中樞**頁面會提供即時的目前狀態，系統中，在 MessageBox 資料庫中存取資料的存取權。 您可檢視所有服務執行個體 (如協調流程、連接埠和傳訊)，及其關聯的訊息。 使用**群組中樞**頁面，您可以執行下列活動：  
  
  - 請參閱目前正在執行的服務執行個體，例如協調流程和傳訊，以及相關的訊息。  
  
  - 查看 MessageBox 資料庫中的目前資料與系統即時狀態檢視。  
  
  - 擱置、終止與繼續服務執行個體。  
  
    如需使用詳細資訊**群組中樞**頁面上，請參閱[ http://go.microsoft.com/fwlink/?LinkId=155281 ](http://go.microsoft.com/fwlink/?LinkId=155281)。  
  
- 檢視警告 (選擇性)。  
  
  如需詳細資訊，請參閱 <<c0> [ 檢查清單： 執行每日維護檢查](../technical-guides/checklist-performing-daily-maintenance-checks.md)。  
  
## <a name="weekly-monitoring-tasks"></a>每週的監視工作  
  
- 檢閱事件記錄檔，每週至少一次。 這項工作的原因是為了防止問題，例如讓未偵測到的 DBNetLib 錯誤。 服務中斷可能會被忽視除非您有非常低的延遲系統。 不過，某些錯誤可能表示更大的問題 （例如太多主機或 BizTalk Server 伺服器，訊息方塊中，SQL 方塊等的效能問題的數目）。  
  
  如需詳細資訊，請參閱 <<c0> [ 檢查清單： 執行每週維護檢查](../technical-guides/checklist-performing-weekly-maintenance-checks.md)。  
  
## <a name="as-needed-tasks"></a>視需要的工作  
  
- 修改規則，以自訂的監視您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構。  
  
- 執行記錄檔的效能分析工具 (PAL)。 如果您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署是很頻繁 （比方說，新的交易夥伴未定期，加入新的程式碼未部署），您可能會執行效能監視器及 PAL 一季一次，或甚至是每隔六個月。 如果您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署的變更頻率，您可能要執行 Perfmon PAL 每隔幾個月的時間相比較的基準。 如需有關 PAL 的詳細資訊，請參閱 <<c0> [ 使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。  
  
- 執行效能監視器中發生的變更數目而定的一季一次，或甚至是每隔六個月來每幾個月您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。  
  
- 執行 BizTalk Server Best Practices Analyzer 時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署的變更 （例如，新增新的應用程式） 或建立新的主機。 您可以下載 BizTalk Server Best Practices Analyzer 在[ http://go.microsoft.com/fwlink/?LinkId=83317 ](http://go.microsoft.com/fwlink/?LinkId=83317)。  
  
- 執行[BizTalk MsgBoxViewer 工具](http://go.microsoft.com/fwlink/?LinkId=151930)(http://go.microsoft.com/fwlink/?LinkId=151930)。 這項工具會分析 BizTalk MessageBox 和其他資料庫，並產生包含警告的 HTML 報告與資料庫相關的任何，和其他資訊。  
  
  > [!TIP]  
  >  您也可以儲存供稍後使用的報表。 與 BizTalk 應用程式的問題進行疑難排解時，這些報表可能會很有用。  
  
  > [!NOTE]  
  >  Microsoft 不支援使用這個工具，Microsoft 不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
- 執行[結束字元 工具](http://go.microsoft.com/fwlink/?LinkId=151931)(http://go.microsoft.com/fwlink/?LinkId=151931)。 這項工具可讓使用者輕鬆地解決 BizTalk MsgBoxViewer 工具所識別的任何問題。 如需結束字元工具如何與 BizTalk MsgBoxViewer 工具整合的詳細資訊，請參閱[若要解決 BizTalk MsgBoxViewer 所識別的問題使用 BizTalk 結束字元](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932)。  
  
  > [!NOTE]  
  >  Microsoft 不支援使用這個工具，Microsoft 不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="annual-monitoring-tasks"></a>每年的監視工作  
  
- 檢閱監視的有效性您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和基礎結構。  
  
- 建立計畫以監視進行任何所需的變更。  
  
## <a name="see-also"></a>另請參閱  
 [例行性維護工作檢查清單](../technical-guides/routine-maintenance-checklists.md)