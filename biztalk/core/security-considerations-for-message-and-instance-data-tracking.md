---
title: 訊息和執行個體資料追蹤的安全性考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- permissions, HAT
- MessageBox database, HAT
- Tracking database, HAT
- security, HAT
- HAT, permissions
- HAT, security
- Management database, HAT
ms.assetid: 83e47dc2-c8e2-42a2-9c85-d511e7dae83f
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ff40db932a7fa1932830289557e1e0bb71b61c7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974567"
---
# <a name="security-considerations-for-message-and-instance-data-tracking"></a>訊息和執行個體資料追蹤的安全性考量
基於安全性理由，追蹤的訊息和服務執行個體不會使用瀏覽器或 Url 如同舊版[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 此監視的選項就會包含在 BizTalk Server 管理主控台的 [群組概觀] 頁面的一部分。  回溯相容性，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]仍然裝載了 Microsoft Internet Explorer 基於安全性理由在殼層內。  

 藉由追蹤訊息和服務執行個體資料，您可以存取進行疑難排解並最佳化所需的技術細節您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 因為這個追蹤資料是功能強大，您應該限制您的生產環境中加以存取，讓惡意或未經授權的使用者並不會造成損害。 建議您遵循下列指導方針保護與您環境中使用 BizTalk Server 管理主控台。  

- 您必須以成員的登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Operators 群組，若要使用 BizTalk Server 管理主控台檢視資料。 若要存取訊息內文中的 [群組概觀] 區段[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須以成員的登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  

   當您使用訊息和服務執行個體的追蹤時，您可以存取下列資料庫：  


  |               [資料庫]               |                                                                                                   使用者群組/權限                                                                                                   |
  |--------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |  BizTalk 管理 (BizTalkMgmtDb)  |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]運算子               |
  | BizTalk MessageBox (BizTalkMsgBoxDb) | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]操作員或讀寫權限 |
  |   BizTalk 追蹤 (BizTalkDTADb)    | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]操作員或唯讀權限  |


- 訊息與服務執行個體追蹤會產生中的所有主機都在報導[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境會根據查詢的參數。 只有成員的資訊洩漏的可能性降至最低[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組可以使用 BizTalk Server 管理主控台，來執行這些性查詢。 不過，如果您不想所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員存取的資料這追蹤程序會產生時，您可以新增/移除使用者從 BizTalk 中的 HM_EVENT_WRITER 與 BAM_EVENT_WRITER SQL Server 角色來限制其存取資料追蹤 (BizTalkDTADb) 資料庫。  

- BizTalk 會使用 BAM_EVENT_WRITER 與 HM_EVENT_WRITER SQL Server 角色，而不是透過角色成員資格，來授予/拒絕其中成員讀/寫「追蹤」資料庫中追蹤資料的權限。 請勿移除這些 SQL Server 角色。 將主控件從裝載變更為不裝載追蹤 (反之亦然) 時，會呼叫 adm_ChangeHostTrackingPrivilege 預存程序。 此預存程序會讀取 BAM_EVENT_WRITER 與 HM_EVENT_WRITER SQL Server 角色的定義，並將對應的 GRANT/DENY 陳述式套用到主控件 Windows 群組。 這種做法的效果與新增主控件 Windows 群組到這些 SQL 角色的效果一樣。  

- 當您設定 BizTalk Server 管理主控台喜好設定，若要檢視封存資料庫中的資料時，在此情況下追蹤查詢連接到保留封存的資料，不到目前作用中 BizTalk 追蹤 (BizTalkDTADb) 資料庫資料庫。  

- 您不能偵錯網路位址轉譯 (NAT，Network Address Translation) 防火牆之間的即時協調流程。 您在處理網域上必須有管理電腦，才能偵錯即時協調流程。  

- 根據您設定追蹤管線和管線，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能會儲存訊息內容中所含敏感性資訊。 如果您使用 WMI 或追蹤訊息內文儲存至檔案位置，請確定該位置具有強式判別存取控制清單 (DACL) 使得只有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員具有讀取這些訊息內文的權限。 將相同 DACL 套用到您儲存訊息內文的所有位置，包括您可能要在其中封存和復原訊息內文的非 BizTalk 資料庫。  

- 您必須以手動方式授與的權限[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組，來存取追蹤 Analysis Server (BizTalkAnalysisDb) 資料庫中; 依預設，只有 OLAP 系統管理員有權限為止。  

## <a name="see-also"></a>另請參閱  
 [規劃訊息和追蹤的執行個體](../core/planning-for-message-and-instance-tracking.md)   
 [檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)