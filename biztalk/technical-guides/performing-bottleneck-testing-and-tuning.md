---
title: "執行測試與微調瓶頸 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d41d95-3a76-4eb0-b07d-14c6b6dccdaa
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d21b558f75824340718f7bd6efa3f10ae9926ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="performing-bottleneck-testing-and-tuning"></a>執行測試與微調瓶頸
您應該完成效能測試以判斷系統瓶頸，並據以調整系統。  
  
## <a name="testing-a-subsystem"></a>測試子系統  
 找出系統瓶頸的最佳作法是以整個系統之子集的執行效能測試，例如：  
  
-   建立傳送訊息至或接收訊息，從外部系統的基準效能參數[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
-   登錄協調流程，但不是啟動它們。 訊息放入輸入的佇列/檔案位置，並讓傳入接收配接器清空佇列/檔案位置，並將訊息發佈至 MessageBox 資料庫。 這可讓您找出您的接收連接埠，以判斷其最大持續性的輸入的速率。  
  
-   一旦訊息會提取至 MessageBox 資料庫中，停止接收配接器、 啟用協調流程和/或傳送配接器，然後測量在哪一個協調流程的速率及/或傳送配接器會處理訊息。  
  
## <a name="testing-the-end-to-end-system"></a>測試端對端系統  
 在前面章節中所述的輸入和輸出速率測試是有效的方式來隔離應用程式子系統的效能，雖然它不會描述端對端的效能。 您也應該測試端對端效能，因為無法指出有些瓶頸，直到開始爭用相同的共用資源 （例如，MessageBox 資料庫） 的多個資源。  
  
 若要產生負載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，請考慮使用 Microsoft BizTalk LoadGen 2007 工具。 如需 LoadGen 2007 工具的詳細資訊，請參閱[Microsoft BizTalk LoadGen 2007](http://go.microsoft.com/fwlink/?LinkID=59841) (http://go.microsoft.com/fwlink/?LinkID=59841)。  
  
 產生及分析的效能報告[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，請考慮使用效能分析的記錄檔 (PAL) 工具。 如需 PAL 工具的詳細資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。  
  
## <a name="what-developers-operators-and-administrators-should-know"></a>應該要知道哪些開發人員、 運算子和系統管理員  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]開發人員應熟悉上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能特性和調整。 操作員和系統管理員應該了解 MessageBox 資料庫向外延展方面，SAN 微調，網路微調和調整的 SQL Server 資料庫 (例如，請參閱[SQL Server 設定，不應該變更](../technical-guides/sql-server-settings-that-should-not-be-changed.md))。 開發人員、 運算子和系統管理員應該了解如何微調[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]高輸送量和低度延遲。