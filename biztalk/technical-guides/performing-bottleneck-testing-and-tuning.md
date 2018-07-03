---
title: 執行瓶頸測試與微調 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95d41d95-3a76-4eb0-b07d-14c6b6dccdaa
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 468f7a3a35922c6348369050593cbb56b56457d3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018591"
---
# <a name="performing-bottleneck-testing-and-tuning"></a>執行瓶頸測試與微調
您應該先完成效能測試以判斷系統中的瓶頸，並據以調整系統。  
  
## <a name="testing-a-subsystem"></a>測試一個子系統  
 找出系統瓶頸的最佳作法是整個系統，子集上執行效能測試，例如：  
  
- 建立傳送或接收訊息的外部系統的基準效能參數[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
- 登錄協調流程，但不是啟動它們。 卸除訊息的輸入的佇列/檔案位置，讓傳入接收配接器清空佇列/檔案位置，並將訊息發佈至 MessageBox 資料庫。 這可讓您找出您的接收連接埠，以判斷其最大持續性的輸入的速率。  
  
- 訊息會提取至 MessageBox 資料庫之後再, 停止接收配接器、 啟用的協調流程處理程序和/或傳送配接器，然後測量的速率在哪一個協調流程和/或傳送配接器處理訊息。  
  
## <a name="testing-the-end-to-end-system"></a>測試端對端系統  
 上一節所述的輸入和輸出速率測試是有效的方式，來隔離應用程式子系統的效能，雖然它不會說明端對端的效能。 您也應該測試端對端效能，因為無法識別有些瓶頸，直到開始爭用相同的共用資源 （例如，MessageBox 資料庫） 的多個資源。  
  
 若要產生負載與針對[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，請考慮使用 Microsoft BizTalk LoadGen 2007 工具。 下載[LoadGen](https://www.microsoft.com/download/details.aspx?id=14925)。  
  
 產生並分析效能報告[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，請考慮使用效能分析的記錄檔 (PAL) 工具。 如需有關 PAL tool 的詳細資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。  
  
## <a name="what-developers-operators-and-administrators-should-know"></a>應該要知道哪些開發人員、 運算子和系統管理員  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發人員應該十分熟悉上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能特性和調整。 操作員和系統管理員應該了解 MessageBox 資料庫向外延展的層面，SAN 微調，網路微調和調整 SQL Server 資料庫 (例如，請參閱[SQL Server 設定，不應變更](../technical-guides/sql-server-settings-that-should-not-be-changed.md))。 開發人員、 運算子和系統管理員應該了解如何調整[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]高輸送量和低延遲。