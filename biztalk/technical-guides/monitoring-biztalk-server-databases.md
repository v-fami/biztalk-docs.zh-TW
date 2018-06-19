---
title: 監控 BizTalk Server 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7fee5015-e818-459b-aeeb-a084ef355600
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fed740f0c2689c8c531a2f92ad4be356d82205db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298166"
---
# <a name="monitoring-biztalk-server-databases"></a>監控 BizTalk Server 資料庫
您可以執行監視 BizTalk Server SQL 代理程式作業，以識別任何已知的問題，管理、 訊息方塊或 DTA 資料庫中。 當您在 BizTalk Server 管理主控台中設定 BizTalk 群組或從舊版本升級 BizTalk 時，就會建立此工作。  
  
## <a name="the-monitor-biztalk-server-job"></a>監視 BizTalk Server 作業  
 [監控 BizTalk Server] 作業會在管理、訊息方塊或 DTA 資料庫中掃描下列問題：  
  
> [!NOTE]  
>  [監控 BizTalk Server] 工作只會掃描問題。 並不會修正找到的問題。  
  
-   不具任何參考的訊息  
  
-   不具參考計數的訊息  
  
-   參考計數小於 0 的訊息  
  
-   不具多工緩衝處理列的訊息參考  
  
-   不具執行個體的訊息參考  
  
-   不具執行個體的執行個體狀態  
  
-   不具對應執行個體的執行個體訂閱  
  
-   被遺棄的 DTA 服務執行個體  
  
-   被遺棄的 DTA 服務執行個體例外狀況  
  
-   啟用全域追蹤選項時，任何主控件執行個體上沒有執行 TDDS  
  
 已設定 [監控 BizTalk Server] 工作，而且已自動化成一週執行一次。 因為工作會耗用大量運算資源，我們建議您排定的停機時間或低流量期間執行。  
作業失敗時，如果遇到任何問題。傳回的錯誤字串會包含找到的問題數。 否則表示已順利執行。 您可以在工作記錄中查看詳細資料。 如果您使用系統管理員權限執行作業，就會記錄錯誤字串作業歷程記錄和 SQL Server 應用程式記錄檔。  
  
> [!IMPORTANT]  
>  這項工作的失敗不一定是構成嚴重的問題，但而不是問題，應調查和解決的定期維護 BizTalk Server 資料庫的一部分。 此作業失敗時設計事件會探索其中一個上面所列的問題。