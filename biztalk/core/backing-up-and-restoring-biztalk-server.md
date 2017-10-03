---
title: "備份和還原 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe03a75a-1ea6-4ccc-9543-7989ec6b1cff
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1adac25b23c69b51e07ed5f30768d046a453887a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-and-restoring-biztalk-server"></a>備份和還原 BizTalk Server
當發生硬體故障時，擁有良好的 BizTalk Server 資料庫與元件備份是非常重要的。 良好的備份可讓您進行還原，而只有輕微的損失或毫無損失。 BizTalk Server 的還原方式根據發生硬體故障的系統上所安裝的元件而不同。 本指南包含下列硬體故障的情況：  
  
 **執行 BizTalk Server 的電腦硬體發生故障**  
  
 如果 BizTalk 群組不是設計為高可用性，當執行 BizTalk Server 的電腦硬體發生故障時，可能導致系統停機或效能降低。 如需如何建立高可用性的 BizTalk 群組的詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。  
  
 若要確保可在硬體故障時替換執行 BizTalk Server 的電腦，您必須備份該電腦上的 BizTalk Server 元件。 如需如何備份和還原執行 BizTalk Server 的電腦的詳細資訊，請參閱[Backing Up a 的電腦執行 BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md)和[復原電腦執行 BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)。  
  
 **執行 SQL Server 的電腦硬體發生故障**  
  
 您可以使用 SQL Server 叢集來降低執行 SQL Server 的電腦發生硬體故障的風險。 但即使您使用了 SQL Server 叢集，包含 BizTalk Server 資料庫的 SQL 伺服器還是有可能發生無法還原的硬體故障。 例如，整個資料層都發生錯誤。 在這樣的情況下，您必須還原最近備份的資料庫集以恢復 BizTalk 群組。  
  
 如需為 BizTalk Server 資料庫提供容錯功能的詳細資訊，請參閱[的 BizTalk Server 資料庫提供高可用性](../core/providing-high-availability-for-biztalk-server-databases.md)。 發生嚴重的 SQL Server 失敗發生的停機時間，您應該依照[Backing Up and Restoring BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)。  
  
 如果發生硬體故障的電腦上同時安裝了 SQL Server 與 BizTalk Server，您應該先還原 BizTalk Server 資料庫，再還原 BizTalk Server 元件。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [檢查清單： 備份與還原](../core/checklist-backup-and-restore.md)  
  
-   [備份和還原的最佳作法](../core/best-practices-for-backup-and-restore.md)  
  
-   [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)  
  
-   [執行 BizTalk Server 之電腦的嚴重損壞修復](../core/disaster-recovery-for-computers-running-biztalk-server.md)  
  
-   [備份執行 BizTalk Server 的電腦](../core/backing-up-a-computer-running-biztalk-server.md)  
  
-   [復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md)