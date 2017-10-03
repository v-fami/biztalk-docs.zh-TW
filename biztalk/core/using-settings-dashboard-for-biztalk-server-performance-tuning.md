---
title: "使用設定儀表板，以便讓 BizTalk Server 效能調整 |Microsoft 文件"
description: "更新群組、 主機和主機執行個體設定 BizTalk Server 管理中使用設定儀表板"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bb1ddac-1e8f-4928-9c70-8326ae64a734
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be1978f92cbbbce945cb7b5a97458577cbf6f725
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="use-settings-dashboard-for-biztalk-server-performance-tuning"></a>使用設定儀表板，以便讓 BizTalk Server 效能調整

## <a name="overview"></a>概觀
使用此 [設定儀表板]，您可以彈性調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定以獲得最佳效能。 您也可以修改 BizTalk 群組、BizTalk 主控件與 BizTalk 主控件執行個體的設定。  
  
-   **群組層級設定**： 在群組層級中，您可以使用[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]設定像是組態重新整理間隔、 訊息批次大小上限、 群組層級追蹤的屬性，等等。這些設定會套用到 BizTalk 群組中的所有電腦。  
  
-   **主機層級設定**： 在主機層級中，您可以修改像是主控件追蹤、 與資源型節流相關的屬性、 訊息處理節流相關的屬性和屬性與協調流程節流相關的設定。 這些設定會套用至所選主控件的所有執行個體。  
  
-   **主控件執行個體層級設定**： 主控件執行個體層級，您可以修改.NET CLR 設定和與協調流程記憶體節流相關的屬性。 這些設定只會套用至所選主控件執行個體。  
  
 如需有關 BizTalk 群組、 BizTalk 主控件與 BizTalk 主控件執行個體設定的詳細資訊，請參閱[如何修改群組設定](../core/how-to-modify-group-settings.md)，[如何修改主控件設定](../core/how-to-modify-host-settings.md)，和[如何修改主機執行個體設定](../core/how-to-modify-host-instance-settings.md)。  
  
 [設定儀表板] 可讓您在不需一致的部署間匯入/匯出 BizTalk 設定。 使用此使用者介面，您可以將目的地的主控件和主控件執行個體對應至來源部署。 這樣可讓您將設定套用至主控件與電腦名稱或它們的數目各不相同的的環境中。 如需匯入/匯出 BizTalk 設定的詳細資訊，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk Server 效能設定](../core/managing-biztalk-server-performance-settings.md)