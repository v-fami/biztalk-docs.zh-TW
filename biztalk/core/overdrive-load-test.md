---
title: 加速負載測試 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d16d0a8-4255-4f5a-86a2-26cc11bb9a70
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cff4592c58dd165a85d63666958721231cfcbd4c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007656"
---
# <a name="overdrive-load-test"></a>加速負載測試
本主題中的資訊是指中所說明的測試[測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)。  
  
 「負載產生」工具 LoadGen 2007 可讓您在 BizTalk Server 系統上模擬負載過重的情形。  
  
> [!NOTE]
>  下載[LoadGen](https://www.microsoft.com/download/details.aspx?id=14925)。 此工具的舊版，BizTalk Server 2004 負載產生工具是下載[http://go.microsoft.com/fwlink/?linkid=108999](http://go.microsoft.com/fwlink/?linkid=108999)。  
  
 為了模擬連續超載的系統，LoadGen 2007 的傳送速度是設定為 410 msgs/sec，比已測量的最大持續輸送量多 120 msgs/sec。  
  
 測試的設計目的不僅是為了加速系統，也是希望瞭解從大約 2 百萬筆記錄的多工緩衝處理積存深度復原需要多少時間。  
  
 若要達到這個目的，系統會以增加速率運作，直到多工緩衝處理深度達到約 2 百萬筆記錄為止。 一旦多工緩衝處理深度到達所需的程度後，就不會繼續產生負載。  
  
 若要確保 BizTalk 節流機制未節流接收主控件，而這可避免多工緩衝處理表格積存累積，**訊息 DB 中的計數**的接收主控件已經從節流處理臨界值預設值 50000 調高為 2000000。 如需變更資訊**訊息 DB 中的計數**節流處理臨界值，請參閱[如何修改資源基礎節流設定](../core/how-to-modify-resource-based-throttling-settings.md)。 如需預設主控件節流設定資訊，請參閱[使用設定儀表板進行 BizTalk Server 效能微調](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)。  
  
 下圖顯示的指示器與上圖相同。  
  
 **加速負載測試的負載設定檔**  
  
 ![加速負載的效能監控顯示](../core/media/bts06-overdrive-load.gif "BTS06_Overdrive_Load")  
  
 如圖所示，多工緩衝處理深度會立即開始累積，尖峰期大約在 2 百萬筆記錄。 以這種速率，大約需要 2.5 個小時才能達到目標的 2 百萬筆記錄積存。 負載停止後，清除工作大約需要 8 小時從積存復原。  
  
## <a name="see-also"></a>請參閱  
 [測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)   
 [使用設定儀表板，以便讓 BizTalk Server 效能調整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)   
 [持續性負載測試](../core/sustainable-load-test.md)