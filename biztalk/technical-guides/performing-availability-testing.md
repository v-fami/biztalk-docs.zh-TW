---
title: 執行可用性測試 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10b543dd-ba85-40da-8c6f-485eddb59158
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6f0d9b1cb7b38ab8a1173ee227a8202812048f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298302"
---
# <a name="performing-availability-testing"></a>執行可用性測試
您應該測試系統，以確認它能夠從各種層級失敗時，範圍介於小規模失敗 （例如網路卡失敗） 至實際執行伺服器遺失復原的嚴重損壞修復。 您損毀修復測試應該包含下列步驟：  
  
-   **測試個別硬體元件失敗。**  
  
     您應該測試系統能夠從個別的硬體元件失敗，例如網路或磁碟中復原。  
  
-   **測試單一 BizTalk server 失敗。**  
  
     在大部分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]生產環境中，主機處理分散多部電腦執行間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]單一的 BizTalk 群組中。 什麼是 BizTalk 群組能夠繼續在事件處理的主機群組中伺服器的其中一個失敗？  
  
-   **測試叢集節點容錯移轉。**  
  
     如果使用 Windows 叢集提供高可用性的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫或 BizTalk 主控件，您應該確認叢集節點容錯移轉功能。 如需有關使用 Windows 叢集提供高可用性的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢查清單： 使用容錯或負載平衡提供高可用性](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)。  
  
-   **測試的使用記錄傳送的 BizTalk Server 資料庫的復原。**  
  
     您應該確認復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 如需有關使用記錄傳送備份和還原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[什麼是 BizTalk Server 記錄傳送？](../technical-guides/what-is-biztalk-server-log-shipping.md)本指南中或[記錄傳送](http://go.microsoft.com/fwlink/?LinkID=153450)(http://go.microsoft.com/fwlink/?LinkID=153450)。  
  
     增加的可用性時，您應該遵循的步驟的檢查清單的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中使用災害復原，請參閱[檢查清單： 提高可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)。  
  
## <a name="see-also"></a>另請參閱  
 [增加可用性，以便讓 BizTalk Server](../technical-guides/increasing-availability-for-biztalk-server.md)