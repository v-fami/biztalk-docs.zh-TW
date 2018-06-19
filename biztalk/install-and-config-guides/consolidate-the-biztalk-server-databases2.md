---
title: 合併 BizTalk Server Databases2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7fc4fe6-3fc2-4164-9f16-90b6f473ba8c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56a8f594298569caaa4842a5f754ba991e9e5f51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22296318"
---
# <a name="consolidate-the-biztalk-server-databases2"></a>合併 BizTalk Server 資料庫2
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝需要在 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 中建立多達 13 個不同的資料庫，以做為各種 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 功能的資料存放區。 基於管理和維護這些資料庫所需的額外負荷，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將其中數個資料庫合併為單一資料庫。 本節說明如何達成 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫合併，並討論實作 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫合併的考量。  
  
> [!NOTE]
>  如需安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時所需之所有資料庫的完整清單，請參閱 [BizTalk Server 中的資料庫](../core/databases-in-biztalk-server.md)。  
  
## <a name="implementing-biztalk-database-consolidation"></a>實作 BizTalk 資料庫合併  
 在安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之後，進行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定期間，可以執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫合併。 請依照下列步驟，實作 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫合併：  
  
1.  按一下 [開始]，依序指向 [程式集] 和 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]]，然後按一下 [BizTalk Server 組態]。 如果系統提示您選取組態類型，請按一下 [自訂組態]。  
  
2.  請針對下列其中一個或多個資料存放區，輸入相同的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]「伺服器名稱」和「資料庫名稱」(例如 *BizTalkConsolidatedDb*)：  
  
    |功能名稱|資料存放區名稱|  
    |------------------|---------------------|  
    |企業 SSO|SSO 資料庫|  
    |群組|BizTalk 管理資料庫|  
    |群組|BizTalk MessageBox 資料庫|  
    |群組|BizTalk 追蹤資料庫|  
    |商務規則引擎|規則引擎資料庫|  
  
     請注意，下列資料存放區**不**應該設定為共用 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫：  
  
    |功能名稱|資料存放區名稱|  
    |------------------|---------------------|  
    |BAM 工具|BAM 主要匯入資料庫|  
    |BAM 工具|BAM 封存資料庫|  
  
3.  設定其餘組態選項，然後套用此組態。 組態工具會針對已指定相同 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]「伺服器名稱」和「資料庫名稱」的資料存放區，在共用的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫中建立資料表。  
  
## <a name="considerations-for-implementing-biztalk-database-consolidation"></a>實作 BizTalk 資料庫合併的考量  
 合併 BizTalk 資料庫時，請考量下列事項：  
  
1.  資料庫合併會降低與管理及維護 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫相關的額外負荷，但只能在適當環境中實作。 在實際執行環境中實作 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫之前，必須先在執行環境中衡量對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 持續性效能的影響。 在下列情況下，請考量實作 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫合併，以簡化資料庫管理及維護：  
  
    -   小型、低資料量的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實際執行環境，此時資料庫效能很難成為效能瓶頸。  
  
    -   中型、中量資料的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實際執行環境，此時 BizTalk 追蹤資料庫不包含在合併中，而且理想上，BizTalk 追蹤資料庫是建立在不同於合併資料庫的實體磁碟上。  
  
    -   大型、大量資料的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 生產環境，此時共用的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫位在極高效能的儲存區域網路 (SAN) 裝置上，而資料庫不大可能形成效能瓶頸。  
  
    -   資料庫效能是次要考量之概念或開發環境的證明。  
  
2.  整體的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 效能通常由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的效能決定。 因此，任何正在處理或即將處理大量資料的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實際執行環境，都不應該實作資料庫合併。 唯一的例外是當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫位在極高效能的儲存區域網路 (SAN) 裝置，此時資料庫不大可能會造成效能瓶頸。 如果資料庫磁碟不是裝載於高效能的儲存區域網路，分散式資料庫便可針對合併的資料庫提供絕佳效能，這點在負載過低時更是明顯。  
  
3.  如果資料庫合併中有包含 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理資料庫，而該合併資料庫的名稱不是 **BizTalkMgmtDb**，這時 [BizTalk 管理] 主控台必須設定為指向該合併資料庫。 請依照[如何連接至現有的群組](../core/how-to-connect-to-an-existing-group.md)中的步驟，並將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台設定為指向該合併資料庫，以便管理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組。  
  
4.  如需持續性 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 效能的詳細資訊，請參閱[持續性效能的規劃](../core/planning-for-sustained-performance.md)。  
  
 如需 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫維護相關活動的詳細資訊，請參閱[維護 BizTalk Server1](../core/maintaining-biztalk-server1.md)。