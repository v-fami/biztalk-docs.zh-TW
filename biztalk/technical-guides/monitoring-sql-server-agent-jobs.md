---
title: 監視 SQL Server Agent 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 60d0a377-c86d-429b-9e48-c37bd5b0f912
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fb4026b95a5f368c265b49425ab1d3e1ec776cd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015389"
---
# <a name="monitoring-sql-server-agent-jobs"></a>監視 SQL Server Agent 作業
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含多項 SQL Server Agent 作業，可執行重要功能以維持伺服器運作正常且狀況良好。 您應該監視這些作業的狀況，確保它們在沒有錯誤的情況下執行。  

## <a name="guidelines-for-monitoring-the-sql-server-agent-jobs"></a>監視 SQL Server Agent 作業的指導方針  
 以下是監視作業的指導方針：  

- **確認 SQL Server Agent 服務正在執行**  

- **確認 BizTalk Server 所安裝的 SQL Server Agent 作業已啟用且正在執行成功**  

   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Server Agent 作業而言十分重要： 如果它們並未執行，經過一段時間，會降低系統效能。  

- **確認 BizTalk Server SQL Server Agent 作業所完成及時**  

   設定 Microsoft System Center Operations Manager，以監視作業。  

   您應該注意的是專門針對特定工作的排程：  

  -   預設會持續 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作執行。 監視軟體，請考量此排程，並不會產生警告。  

  -   MessageBox_Message_Cleanup_BizTalkMsgBoxDb 作業未啟用或排程，但它由 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作開始每隔 10 秒。 因此，這項作業不應啟用、 排程，或以手動方式啟動。  

- **確認已正確設定 SQL Server Agent 服務的啟動類型**  

   確認 SQL Server Agent 服務已設有**Startuptype**的**自動**除非 SQL Server Agent 服務設定為 Windows Server 叢集上叢集資源。 如果 SQL Server Agent 服務設定為叢集資源，則您應該設定**Startuptype**作為**手動**因為服務將受叢集服務。  

## <a name="additional-resources"></a>其他資源  

- 如需監視的詳細資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SQL Agent 作業，請參閱[監視 SQL Server Agent 作業和資料庫](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)。  

- 如需隨附於 SQL Server Agent 作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]請參閱 < [[資料庫結構和作業]](http://go.microsoft.com/fwlink/?LinkID=153451) (<http://go.microsoft.com/fwlink/?LinkID=153451>)。
