---
title: "清除和封存追蹤資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14094fda-3fd9-4d45-9bbb-cd9377c2cbad
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94a2560bc8a57a8f60bf2d1ebcddf68b62fd178a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="purging-and-archiving-tracking-data"></a>清除和封存追蹤資料
請務必設定並啟用 DTA 清除與封存 SQL 代理程式作業。 此作業會封存，並且從 BizTalk 追蹤 (DTA) 資料庫清除舊資料。 這是不可或缺的狀況良好[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。 大型的追蹤資料庫將會開始追蹤主控件以及任何其他處理序的效能影響該查詢追蹤資料庫。 如果追蹤資料不會清除從追蹤資料庫，資料庫會繼續成長。  
  
## <a name="guidelines-for-using-the-dta-purge-and-archive-job"></a>指導方針使用 DTA 清除與封存工作  
  
-   **請確認已正確設定、 啟用以及已成功完成 DTA 清除與封存 SQL 代理程式作業。**  
  
     因為您必須先將它設定為包含可以在其中寫入封存檔案的目錄，預設不會啟用這項作業。  
  
-   **如果您只需要清除舊資料，而不需要將它封存在第一次，然後變更 SQL Agent 作業來呼叫預存程序 」 dtasp_PurgeTrackingDatabase"。**  
  
     這會略過 「 封存 」 步驟，並只清除。 如需有關這個預存程序和變更的 SQL 代理程式作業來使用它時，請參閱[< 如何清除資料從 BizTalk 追蹤資料庫的 「](http://go.microsoft.com/fwlink/?LinkId=153817) (http://go.microsoft.com/fwlink/?LinkId=153817)。  
  
-   **請確保工作能夠以最快速度的內送的追蹤資料會產生清除追蹤資料。**  
  
     它是可接受的工作負載在尖峰期間，取得，但永遠應該能夠跟上。 如果清除工作落後，而且絕不會是能夠趕上，追蹤資料庫將會繼續成長，而效能將最終會受到負面影響。  
  
-   **檢閱軟清除和硬清除參數，以確保保持最佳的時間長度的資料。**  
  
     如需這些參數的詳細資訊，請參閱[「 封存和清除 BizTalk 追蹤資料庫 」](http://go.microsoft.com/fwlink/?LinkId=153816) (http://go.microsoft.com/fwlink/?LinkId=153816)。  
  
-   **如果您要保留追蹤封存檔案，請確定您已成功還原，並使用它們的位置中有程序。**  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 設定 SQL Server](~/technical-guides/checklist-configuring-sql-server.md)