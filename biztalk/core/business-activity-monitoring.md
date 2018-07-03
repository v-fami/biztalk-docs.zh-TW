---
title: 商務活動監控 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83b3c92f-3062-413e-8d89-797f1c7ea7ab
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1700cd8aa120d11413a5fba16ce2e1439315df4a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006039"
---
# <a name="business-activity-monitoring"></a>商務活動監控
資訊工作者需要在查看及評估商務程序上具有彈性。 例如，採購經理可能需要知道每日有多少採購單已核准或已拒絕，而業務經理可能需要產品訂購的每小時更新資訊。 要符合這些不同的需求，需要整體性的架構來追蹤商務程序中發生的狀況。 這正是 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的「商務活動監控」(BAM) 元件所要提供的。  
  
 ![BAM 圖](../core/media/bam-diagram.gif "bam_diagram")  
  
 如上圖所示，BAM 元件可監控 BizTalk 應用程式產生的事件及資料。 此資訊是使用 SOAP 可呼叫的 Web 服務來進行存取，且可以由數種不同方式來存取，方法如下：  
  
- 透過 Microsoft Excel 或其他桌面用戶端，如自訂儀表板應用程式。  
  
- 使用 BAM 入口網站，可讓商務使用者檢查並設定 BAM 資訊的 BizTalk Server 中的元件。 資訊工作者可以使用 BAM 入口網站選取特定的商務程序，然後選擇指定的 BAM 檢視給程序。 每個檢視都提供不同觀點，如每一產品銷售趨勢、目前庫存數量，或其他重要效能指標的圖形說明。 這些檢視中的資訊可以每日、每小時或更頻繁地更新。 資訊工作者也可以使用 BAM 入口網站定義資料的彙總，像是已完成、取消或前一個小時處理的訂單數。 實作方式如同一組 ASP.NET 頁面一樣，BAM 入口網站也可以裝載為 Windows SharePoint Services 內部的網頁組件。  
  
- 透過 SQL Server Notification Services，可將 BAM 資訊以通知方式傳遞。 前兩個選項可讓資訊工作者檢查 BAM 資訊，而第三個選項則會在發生事件時建立通知。 資訊工作者可以使用 BAM 入口網站的警示管理員定義在特定事件發生時要傳送的警示。 比方說，BAM 使用者可能會選擇要傳送電子郵件給特定管理員，只要在一天內已取消的訂單數目超過 10，或隨時通知某業務代表的隨時收到其最大客戶的訂單。  
  
  事實上，每一個 BAM 檢視都依賴一或多個 BAM 活動。 一個　BAM 活動代表一個特定的商務程序，例如處理採購單或運送產品，而且每一個商務程序都有一組已定義的里程碑和商務資料。 例如，採購單活動可能有已核准、已拒絕和已傳遞等等的里程碑，以及像客戶名稱和產品等等的商務資料。  
  
  對於透過 Excel 存取 BAM 的資訊工作者，BAM 活動及 BAM 檢視可以使用來建立 Excel 增益集。 此增益集的 「 BAM 活動精靈 」 可定義的活動中，「 BAM 檢視精靈 」 可讓您可根據這些活動的檢視的定義。 事實上，BAM 檢視精靈只是使用一或多個 BAM 活動中的資訊來幫助資訊工作者建置標準的 Excel 樞紐分析表。 然後該檢視中提供的資訊可直接在 Excel 中顯示，如下圖所示。  
  
  ![](../core/media/understandingbts-12-bam2.gif "UnderstandingBTS_12_BAM2")  
  
  在這個簡單的範例中，兩個 Excel 圖表顯示訂單進度及銷售的資訊。 BAM 檢視可能更複雜，而且其建立者可以指定哪些使用者可查看公開的資料。 例如，也許採購經理可存取檢視中某些進入採購程序的資料，但是採購人員卻看不到。  
  
  雖然資訊工作者可自行建立 BAM 檢視及 BAM 活動，但是這些檢視及活動則依賴他們監控之協調流程提供的資訊。 因此，開發人員還是有需要扮演的角色。 使用名為「追蹤設定檔編輯器」(TPE) 的工具，開發人員必須設定協調流程，才可提供特定 BAM 活動所需的資訊，也因此可供依賴此活動的 BAM 檢視使用。 這個工具可讓開發人員將協調流程中的適當事件及訊息欄位與 BAM 活動中對應的里程碑及商務資料進行圖形化的關聯。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]引擎接著會傳送這些事件及訊息欄位值到追蹤資料庫中，如前圖所示 BAM 元件可存取。 雖然開發人員必須負責，但 BAM 活動及 BAM 檢視不是他們關心的主要項目。 資訊工作者會獨力建立、維護及使用這些商務導向的服務。  
  
  在  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，TPE 也可用來指定管線產生事件的方式。 更重要的是，現在 BAM 可接受並顯示任何使用者程式碼產生的事件，不管事件是不是建置為協調流程。 使用.NET Framework 建置任何應用程式可能可監視使用的 BAM 元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [資訊工作者技術](../core/information-worker-technologies.md)