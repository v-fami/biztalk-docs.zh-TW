---
title: 管理 BizTalk Server 效能設定 |Microsoft Docs
description: 使用設定儀表板更新 BizTalk 群組、 主機和設定 BizTalk Server 中的主控件執行個體
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ca56a981-a255-4c4d-82f8-a57d390e425e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19acfa50ecbcaf46cb796630e88d292283f4631e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999767"
---
# <a name="manage-biztalk-server-performance-settings"></a>管理 BizTalk Server 效能設定
  
 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] BizTalk Server 中定序和效能設定，並提供了中央主控台來管理這些設定。 這有助於：  
  
-   改良可設定之屬性的可搜尋的性
  
-   減少至解決方案的時間，因為所有的設定現在都可存取在單一位置，而且可以匯出/匯入輕鬆
  
-   提供在某個 BizTalk 部署上完成的層級的效能微調的全面檢視
  
## <a name="why-use-it"></a>為何要使用它？  
 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 是針對需要廣泛調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定以達最佳化效能的 IT 系統管理員而設計的。  
  
 您可以使用 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 來修改 BizTalk 群組的設定，以及該群組中所有 BizTalk 主控件和 BizTalk 主控件執行個體的設定。  
  
 若要深入了解群組、 主機和主機執行個體設定，請參閱[如何修改群組設定](../core/how-to-modify-group-settings.md)，[如何修改主控件設定](../core/how-to-modify-host-settings.md)，和[如何修改主控件執行個體設定](../core/how-to-modify-host-instance-settings.md).  
  
## <a name="prerequisites"></a>必要條件 
 您可以從 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 管理主控台啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如需如何管理[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用的效能設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，請參閱[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。  
  
## <a name="where-do-i-start"></a>要從何處著手？  
 您可以使用下列任一種方式存取 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]：  
  
- 開始[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**BizTalk 群組**主控台樹狀目錄中，然後選取**設定**。  
  
- 以滑鼠右鍵按一下任何主機**平台設定**MMC，然後按一下 節點**設定**。 這會啟動 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]，而您可以在其中修改該主控件的相關設定。  
  
- 以滑鼠右鍵按一下任何主控件執行個體，底下**平台設定**MMC，然後按一下 節點**設定**。 這會啟動 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]，而您可以在其中修改該主控件執行個體的相關設定。  
  
## <a name="export-and-import-settings"></a>匯出和匯入設定  
 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 可讓您匯出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的設定，再將該設定匯入到其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境，進而縮短完成解決方案所需的整體時間。 當系統管理員會試著在測試環境中調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 效能，並會在達成想要的結果時將設定匯入實際執行環境的情況下，這種方式就特別有用。  
  
 如需如何使用匯入/匯出[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]使用者介面，請參閱 <<c2> [ 匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)。
  
## <a name="scripting-support"></a>指令碼支援
 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 不僅提供用以管理 BizTalk 設定的中央使用者介面，也可確保所有的設定與匯入/匯出工作皆可透過 API 與命令列選項來存取。 這可以讓 BizTalk Server 系統管理員將 BizTalk Server 的相關設定工作自動化。 在這樣的指令碼支援當中：  
  
- 所有的群組設定可以存取和修改透過 WMI 類別： `MSBTS_GroupSetting`  
  
- 所有的主控件設定可以存取和修改透過 WMI 類別： `MSBTS_HostSetting`  
  
- 所有的主控件執行個體設定可以存取和修改透過 WMI 類別： `MSBTS_HostInstanceSetting`  
  
- 您可以透過匯入和匯出作業**BTSTask.exe**命令：`ExportSettings`和 `ImportSettings`  
  
  如需有關如何使用 BTSTask.exe 命令列公用程式匯入/匯出的詳細資訊，請參閱 <<c0> [ 匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。  
  
## <a name="next"></a>下一個  
  
-   [使用設定儀表板調整 BizTalk Server 效能](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)  
  
-   [自動化 BizTalk Server 效能調整](../core/automating-biztalk-server-performance-tuning.md)  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk Server](../core/use-groups-create-artifacts-optimize-performance-and-more-in-biztalk-server.md)