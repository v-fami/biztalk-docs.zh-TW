---
title: 更新主控件執行個體設定 |Microsoft 文件
description: 變更主控件執行個體設定在 「 BizTalk Server 系統管理員
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2338255b-cc13-4f6a-86c3-9ecc666c43e5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d85635f7f7a3b2cfe05abaf041cac07913b36f96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254374"
---
# <a name="update-biztalk-host-instance-settings"></a>更新 BizTalk 主控件執行個體設定

## <a name="overview"></a>概觀
使用 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]，您就可以跨 BizTalk 群組修改指定主控件執行個體的組態資訊。 此主題中提供的逐步程序，可讓您修改 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的主控件執行個體層級效能設定。  
  
 您通常會將 BizTalk 設定 (來自來源環境) 儲存為 XML 檔案。 XML 檔案中包含的資訊可讓您複寫目標電腦上的設定。 您可以將那些設定匯入「設定儀表板」，而不用設定新的值。 而另一方面，在為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定新值之後，您可以將它們匯出成 XML 檔案，以用於另一部電腦。  
  
 如需有關匯入詳細[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)和[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。 
  
## <a name="prerequisites"></a>必要條件  
 若要執行這項作業，您必須為 BizTalk Server 系統管理員群組的成員登入。  
  
## <a name="update-the-host-instance-level-settings"></a>更新主控件執行個體層級設定  
  
1.  在**BizTalk Server 管理主控台**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**。  
  
2.  在**BizTalk 設定儀表板**對話方塊**主控件執行個體**索引標籤上，執行下列任一項：  
  
    -   修改主控件執行個體的 .NET CLR 設定。 請參閱[變更.NET CLR 設定](../core/how-to-modify-net-clr-settings.md)。  
  
    -   修改協調流程記憶體節流設定。 請參閱[變更協調流程記憶體節流設定](../core/how-to-modify-orchestration-memory-throttling-settings.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用設定儀表板，以便讓 BizTalk Server 效能調整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)