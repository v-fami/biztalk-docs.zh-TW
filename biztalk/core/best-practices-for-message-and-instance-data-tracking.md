---
title: "訊息與執行個體資料追蹤的最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HAT, best practices
- best practices, HAT
ms.assetid: 2ac5c87b-2059-4912-9cec-2ae4eaac56df
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a6f673b0a70903575918eb87dc4bd8edc9841e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-message-and-instance-data-tracking"></a>訊息和執行個體資料追蹤的最佳作法
檢閱使用歷程記錄和追蹤資料的下列最佳作法。  
  
-   **檢閱使用歷程記錄和追蹤資料的安全性考量**  
  
    -   如需歷程記錄和追蹤資料的安全性考量的詳細資訊，請參閱[訊息和執行個體資料追蹤的安全性考量](../core/security-considerations-for-message-and-instance-data-tracking.md)。  
  
-   **確定 SQL Server Agent 服務正在所有的 MessageBox 資料庫上執行**  
  
    -   SQL Server Agent 讓訊息內文可供 WMI 和歷程記錄和追蹤資料。 這可讓您執行作業來清除 MessageBox 資料庫。 如需有關 SQL Server Agent 的詳細資訊，請參閱《SQL Server 線上叢書》。  
  
-   **啟用訊息內文追蹤**  
  
    -   在服務執行個體處理完成之後，必須要有訊息內文追蹤才能儲存訊息。  
  
-   **針對您的商務需求適當地設定追蹤**  
  
    -   您可以檢視歷程記錄和追蹤資料之前，您必須先設定使用 BizTalk Server 管理主控台的追蹤。 在啟用或停用追蹤選項時，必須牢記多個考量。 您追蹤的資料越多，「BizTalk 追蹤」(BizTalkDTADb) 資料庫的大小便會成長越快，這可能會對執行階段效能造成不良的影響。 如需詳細資訊，請參閱[設定追蹤使用 BizTalk Server 管理主控台](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef)。  
  
-   **選取適當類型的追蹤，以進行疑難排解或稽核**  
  
    -   在開發環境，或在臨時或生產環境中進行疑難排解時，應該啟用所有追蹤選項，以便您可以查看成品事件、訊息屬性、訊息內文和協調流程事件的細節。 這會提供豐富的追蹤資訊，可讓您在系統中重新建立事件序列並偵錯應用程式。  
  
    -   對於執行層級的稽核，請仔細選取您要稽核的事件，然後只啟用那些事件的稽核。 例如，許多企業想要能夠證實訊息已輸入且已離開系統。 為達成此目的，您應該啟用對應接收埠上的輸入追蹤，並啟用對應傳送埠上的輸出追蹤。 如有必要，您可以新增訊息屬性和訊息內文追蹤。  
  
    -   如需測量商務關鍵效能指標 (KPI) 或是由指定商務里程碑的達成度所測量的進度，您應該使用商務活動監控 (BAM) 追蹤。 BAM 追蹤的追蹤，以及將訊息內文，因此如果這是重要的是，您應該使用歷程記錄和追蹤的資料搭配 BAM 追蹤的能力有限。 如需有關 BAM 追蹤的詳細資訊，請參閱[使用商務活動監控](../core/using-business-activity-monitoring.md)。  
  
-   **封存和清除 BizTalk 追蹤 (BizTalkDTADb) 資料庫以規則為基礎的資料**  
  
    -   如果已啟用追蹤，您應該定期從「BizTalk 追蹤」資料庫封存和清除資料，協助讓資料庫保持適當的大小，以利改善系統效能。 如需詳細資訊，請參閱[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)。  
  
## <a name="see-also"></a>另請參閱  
 [檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)