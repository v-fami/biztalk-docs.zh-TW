---
title: "資料庫可用性規劃 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aa74257-4159-46f6-b538-f7e9083d74ad
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d77ce6572ace3617308a046a422a3422b2dd8df5
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-database-availability"></a>資料庫可用性規劃
BizTalk Server 傳訊引擎可確保商務程序的可靠性，方法是保存的永久性狀態和商務資料處理至稱為 BizTalk Messagebox 資料庫的 SQL Server 資料庫。 可靠性和保存資料持續性只會顯示為基礎的資料存放區，因為 BizTalk Server 資料庫的高可用性規劃是非常重要。  
  
## <a name="hardware-considerations"></a>硬體考量  
 若要確保 BizTalk Server 資料庫的高可用性，請考慮下列規劃硬體時：  
  
1.  請考慮實作存放區域網路 (SAN) 裝載 BizTalk Server 資料庫。 SAN 的磁碟應設定使用 RAID 1 + 0 （等量磁碟區鏡像組） 拓撲盡可能以最大效能和高可用性。 
  
2.  計劃安裝多部執行 SQL Server 以裝載 BizTalk Server 資料庫。 執行 SQL Server 的多部電腦將會需要適用於 SQL Server 叢集 （建議使用） 和 （或) 罩個別實體 SQL Server 執行個體上 （建議） 特定 BizTalk Server 資料庫。  
  
3.  計劃安裝一或多部執行 SQL Server 實作的 SQL Server 記錄傳送災害復原用途。 BizTalk Server 實作資料庫待命功能，透過使用 SQL Server 記錄傳送。 SQL Server 記錄傳送會自動備份和還原的資料庫和交易記錄檔，允許繼續處理的實際執行伺服器失敗，資料庫的待命伺服器。 如需實作的 SQL Server 記錄傳送災害復原用途的詳細資訊，請參閱[什麼是 BizTalk Server 記錄傳送嗎？](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## <a name="software-considerations"></a>軟體考量  
 若要確保 BizTalk Server 資料庫的高可用性，請考慮下列規劃軟體時： 計劃安裝版本與版本的 SQL Server 可支援容錯移轉叢集支援，及/或 BizTalk 記錄傳送支援。 如需完整的 SQL Server 版本所支援的功能清單，請參閱[版本和支援的功能](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)。
  
## <a name="high-availability-vs-disaster-recovery"></a>高可用性與災害復原  
 有兩個不同的方法，來增加 BizTalk Server 環境的可用性： 提供容錯和/或負載平衡，或提供可用性使用災害復原使用的高可用性。 由於每個方法會增加可用性，它們之間的主要差異是該容錯和/或負載平衡通常會提供更快速的復原時間比災害復原。 因此，容錯上建置方案或負載平衡會更常被認為是提供高可用性而非只提供可用性。 在生產環境 BizTalk Server 環境中，因此可以用這兩種方法。  
  
 使用 Windows 叢集的容錯能力的 BizTalk Server 資料庫提供高可用性。 如需有關如何為 BizTalk Server 資料庫提供高可用性的詳細資訊，請參閱[資料庫的高可用性](../technical-guides/high-availability-for-databases.md)。  
  
 提高可用性與災害復原使用 BizTalk Server 記錄傳送。 若要增加可用性與災害復原 BizTalk Server 資料庫，請依照下列主題中的步驟[檢查清單： 提高可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)。