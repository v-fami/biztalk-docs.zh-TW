---
title: 持續性負載測試 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sustainable load test
- LoadGen tool, sustainable load test
ms.assetid: a9d752ff-aff1-4445-8af5-8f84609880e2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d17d8d38323f7933c8e60cb2b87e0ec312d270c5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015647"
---
# <a name="sustainable-load-test"></a>持續性負載測試
本主題中的資訊是指在所說明的測試[測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)。  
  
 在第一個測試中，系統由 MST 驅動，所以可以觀察狀況良好的系統。  
  
 下圖顯示使用這個方法來尋找測試系統的最大持續性輸送量之後的幾個主要指示器。  
  
 **持續性負載測試的負載概述**  
  
 ![效能監控測量持續性負載](../core/media/bts06-sustainable-load.gif "BTS06_Sustainable_Load")  
  
 這個圖表顯示在經過一小時的測試後，多工緩衝處理的深度穩定且未成長。  
  
- 圖表上方的黑線顯示系統每秒接收的總訊息數 (例如，兩部接收伺服器的每秒總訊息數)。  
  
- 圖表下方的線條表示每部 SQL 伺服器上的 MessageBox 多工緩衝處理深度。  
  
  一旦系統到達穩定的多工緩衝處理深度上限時，就會用每秒接收的訊息數來測量 MST。 在此實例所描述的硬體上，會達到每秒 290 個訊息的 MST。  
  
> [!NOTE]
>  經過一段時間，一旦系統到達多工緩衝處理深度不再穩定的點時，會超過 MST。 可能需要執行多個不同負載的測試，以評估多工緩衝處理仍為穩定的負載上限，及系統可處理的訊息積存，而不造成其他的訊息積存。  
  
 任何 BizTalk 部署效能分析都應該要檢查某些主要指示器，以瞭解資源的瓶頸。 在持續性輸送量上限之下所執行部署使用的主要量值及其值如下：  
  
 **CPU 使用率**  
  
|[伺服器]|平均的 CPU 使用|  
|------------|-----------------------------|  
|BizTalk Server|55%|  
|SQL Server (主要 MessageBox 伺服器)|76%|  
|SQL Server (其他 MessageBox 伺服器)|83%|  
  
 **實體磁碟閒置時間**  
  
|[伺服器]|平均磁碟閒置時間|  
|------------|----------------------------|  
|所有 SQL Server 的平均數|69%|  
  
 **SQL Server 上的 SQL 鎖定**  
  
|參數|ReplTest1|  
|---------------|-----------|  
|每秒平均封鎖逾時總數 (每部 SQL Server)|1980|  
|平均封鎖等候總時數 (毫秒)|495|  
  
 在這個測試期間，BizTalk 或 SQL Server 應用程式日誌中並未產生任何錯誤。  
  
 從這個資料中，我們可以得到下列結論：  
  
- 系統中沒有明顯的資源瓶頸發生。  
  
- 所有的指示器都在狀態良好的限度內。  
  
- CPU 及磁碟閒置時間顯示有大量的空間，甚至沒有接近限制。  
  
- SQL 鎖定指示器看起來正常， **Lock Timeouts/sec**不是問題開始，直到解決 5000 個 （取決於您的 SQL Server) 的鎖定等候 1 秒的時間也是狀況良好。  
  
  現在我們已經示範如何尋找持續性輸送量上限的方法，並已經看到持續狀態良好的系統主要指示器應該長什麼樣子，現在我們要探討某些與系統相關的行為，該系統接收的速度比處理及回收記憶體要快。 請繼續進行[加速負載測試](../core/overdrive-load-test.md)。  
  
## <a name="see-also"></a>另請參閱  
 [測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)   
 [加速負載測試](../core/overdrive-load-test.md)