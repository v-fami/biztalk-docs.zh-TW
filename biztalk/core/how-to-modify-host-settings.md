---
title: "如何修改主控件設定 |Microsoft 文件"
description: "變更以改善效能和節流設定的 BizTalk Server 管理 中的 BizTalk 主控件設定"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0759b3a0-560e-4a11-92e6-9de0e15f463b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 998c668bf787c9db260597c3a350e0e571492212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="update-biztalk-host-settings"></a>更新 BizTalk 主控件設定

## <a name="overview"></a>概觀
您可以使用「設定儀表板」修改某個主控件在整個 BizTalk 群組中的組態資訊。 本主題提供在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中修改主控件層級效能設定的逐步程序。  
  
> [!NOTE]
>  您也可以修改群組與主控件執行個體設定。 如需如何修改的設定資訊，請參閱[使用設定儀表板進行 BizTalk Server 效能微調](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)。  
  
 您可以將目前的 BizTalk Server 設定匯出至 XML 檔案。 稍後您可以將這些設定匯入到「設定儀表板」，而不需設定新值。 如需有關匯入詳細[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)和[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。 
  
## <a name="prerequisites"></a>必要條件  
 若要執行這項作業，您必須為 BizTalk Server 系統管理員群組的成員登入。  
  
## <a name="update-the-host-level-settings"></a>更新主機層級設定  
  
1.  在**BizTalk Server 管理主控台**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**。  
  
2.  在**BizTalk 設定儀表板**對話方塊**主機**頁面上，執行下列一或多個項目。  
  
    -   修改 BizTalk 主控件的一般效能設定。 請參閱[如何修改一般設定](../core/how-to-modify-general-settings.md)。  
  
    -   修改 BizTalk 主控件的資源型節流設定。 請參閱[如何修改資源型節流設定](../core/how-to-modify-resource-based-throttling-settings.md)。  
  
    -   修改 BizTalk 主控件的根據速率的節流設定。 請參閱[如何修改速率型節流設定](../core/how-to-modify-rate-based-throttling-settings.md)。  
  
    -   修改 BizTalk 主控件的協調流程節流設定。 請參閱[如何修改協調流程節流設定](../core/how-to-modify-orchestration-throttling-settings.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用設定儀表板，以便讓 BizTalk Server 效能調整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)