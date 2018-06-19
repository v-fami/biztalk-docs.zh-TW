---
title: 如何避免磁碟 Contention2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37bdf6bd-cb34-4540-819e-908d83a22d40
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7be7a38ac3f3f6cc1d7d266c664cbb85f731c22
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22298134"
---
# <a name="how-to-avoid-disk-contention"></a>如何避免磁碟爭用
BizTalk Server 設計為持續性的系統。 針對高輸送量、 MessageBox 和 「 BizTalk 追蹤資料庫可能會遇到嚴重的爭用情況。 這個爭用情況可能會因緩慢的磁碟而加重。 如果磁碟緩慢 （大於 15ms 平均 avg.Disk sec/Read 或 avgDisk sec/Write)，它可能會造成 SQL Server 來保存鎖定更久 （高鎖定等候時間及高鎖定逾時）。 亦可以使得 MessageBox 表格 （多工緩衝處理和應用程式佇列） 的成長，讓資料庫膨脹和節流。 這種情況下，最終結果都較低的整體持續性輸送量。  
  
> [!NOTE]  
>  如果伺服器具有磁碟瓶頸所識別的相關資訊，請參閱[Windows 效能監視器](http://go.microsoft.com/fwlink/?LinkID=204007)(http://go.microsoft.com/fwlink/?LinkID=204007)。 Windows 效能監視器是 Microsoft Management Console (MMC) 嵌入式管理單元，可提供分析系統效能的工具。  
  
 若要避免磁碟爭用情況，執行下列作業：  
  
|步驟|참조|  
|-----------|---------------|  
|使用 Raid10 0 + 1 的磁碟組態。|[避免瓶頸的最佳做法](../technical-guides/best-practices-for-avoiding-bottlenecks.md)|  
|可能的話，請部署在高速 SAN 上的資料庫。 如果多個資料庫共用相同的磁碟，我們建議您在上個別進行設定**專用**磁碟。 此外，我們建議您分隔到不同的磁碟上的 MessageBox 資料庫的 MDF 和 LDF 檔案。|[Databases2 最佳化檔案群組](../technical-guides/optimizing-filegroups-for-the-databases2.md)|  
|請考慮為 TEMPDB 資料庫中，配置多個檔案，因為這會大幅降低磁碟爭用情況，將負載分散到多個資料檔案。|[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|請考慮將 MessageBox 資料庫到不同的 BizTalk 追蹤資料庫的專用伺服器。|[組態後資料庫 Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|將 MSDTC 記錄檔目錄指派給另一個專用的磁碟機。|[最佳化作業系統效能](../technical-guides/optimizing-operating-system-performance.md)|  
|如果因為 PageFile 或 MSDTC 記錄的原因，而在本機磁碟機上造成爭用，請嘗試將 PageFile 及/或 MSDTC 記錄移到另一個磁碟機。|[避免瓶頸的最佳做法](../technical-guides/best-practices-for-avoiding-bottlenecks.md)|  
|最佳化追蹤資料庫的寫入作業。|[如何識別追蹤資料庫中的瓶頸](../technical-guides/how-to-identify-bottlenecks-in-the-tracking-database.md)|  
|最佳化 MessageBox 資料庫的讀取和寫入作業。|[如何識別 MessageBox Database1 中的瓶頸](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md)|  
|如果 BizTalk 主控件執行個體讓 CPU 飽和，請考慮將傳送、 接收、 處理及追蹤功能分成多個主控件。 這會設定系統，讓協調流程功能來改善整體系統輸送量的專用伺服器上的執行。|[最佳化 BizTalk Server 效能](../technical-guides/optimizing-biztalk-server-performance.md)|  
|如果部署多個協調流程，請考慮在不同的專用協調流程主控件中登錄它們。 這會隔離不同的協調流程，並防止在相同的實體位址空間，或在相同伺服器上的共用資源爭用的情況。|[最佳化 BizTalk Server 效能](../technical-guides/optimizing-biztalk-server-performance.md)|  
|請考慮使用 Windows 效能監視器診斷磁碟爭用問題...|[Windows 效能監視器](http://go.microsoft.com/fwlink/?LinkID=204007)|  
  
 如需磁碟效能分析的詳細資訊，請參閱下列資源：  
  
-   [繫結磁碟問題出 ruling](http://go.microsoft.com/fwlink/?LinkId=120947) (超連結 "http://go.microsoft.com/fwlink/?LinkId=120947" \t "_blank"http://go.microsoft.com/fwlink/?LinkId=120947) 。  
  
-   [SQL Server 前置部署 I/O 最佳做法](http://go.microsoft.com/fwlink/?LinkId=120948)(http://go.microsoft.com/fwlink/?LinkId=120948)。  
  
-   「 I/O 瓶頸 」 一節[效能問題的疑難排解 SQL Server 2008](http://go.microsoft.com/fwlink/?LinkID=153586) (http://go.microsoft.com/fwlink/?LinkID=153586)。  
  
## <a name="see-also"></a>另請參閱  
 [資料庫層中的瓶頸](../technical-guides/bottlenecks-in-the-database-tier.md)