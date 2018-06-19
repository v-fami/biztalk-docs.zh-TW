---
title: 管理 BAM 事件匯流排服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MessageBox database, migrating data
- Primary Import database [BAM], migrating data
- migrating, data [BAM]
- managing [BAM], Event Bus Service
- Event Bus Service [BAM], managing
- Tracking Data Decode Service (TDDS)
ms.assetid: 556e7fe2-4a7d-46f6-8e55-f41be4e666dc
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f265201e371a86072c06b336b4d00bb1742f5f6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262814"
---
# <a name="managing-the-bam-event-bus-service"></a>管理 BAM 事件匯流排服務
BAM 事件匯流排服務也稱為「追蹤資料解碼服務」(TDDS)，會處理儲存在來源資料庫中的追蹤資料 (資料流)，並以方便日後查詢的格式保存該資料。  
  
 BAM 事件匯流排服務會將商務智慧資料移至 BAM 主要匯入資料庫，並將 BizTalk 狀況監控資料移至 DTA 資料庫。 BAM 事件匯流排服務在 BizTalk 服務中以子服務方式執行。  
  
 您可以藉由收集執行期間的事件資料，然後將資料以應用程式狀態暫時儲存在相同資料庫 (例如 MessageBox 資料庫)，以監控交易應用程式的活動，例如 Microsoft BizTalk® Server。  
  
> [!NOTE]
>  請避免在相同電腦上建立一個以上控制追蹤不同 BizTalk 群組的應用程式執行個體。 如果追蹤不同 BizTalk 群組的執行個體存在同一部電腦上，您將無法辨別哪個事件屬於哪個 BizTalk 群組，在 BizTalk 管理主控台或事件記錄檔中所有的 BizTalk 群組會顯示具有相同名稱。  
  
 BAM 事件匯流排服務可讀取事件資料、將資料解碼並儲存至 Microsoft SQL Server?資料庫，您可以在其中輕鬆地查詢資料。  
  
 BAM 事件匯流排服務提供下列優點：  
  
-   事件資料永遠符合應用程式的狀態，並且絕不會公開未認可的進度。  
  
-   對執行中應用程式造成的效能影響最小，因為事件資料會在相同本機交易中儲存如同應用程式狀態變更時所儲存少數的記錄。  
  
-   應用程式狀態的 SQL Server 儲存體已針對執行效能最佳化。 資料是由 TDDS 解碼後儲存至另一個資料庫，可能是 BAM 主要匯入資料庫或 DTA 資料庫。 報表的產生則是從此資料庫查詢資料的結果，所以不會影響到儲存應用程式狀態的 MessageBox 資料庫。  
  
-   使用您可以查詢的形式儲存事件資料不是在應用程式伺服器和資料庫中完成的， 它被卸載至執行 BAM 事件匯流排服務和目的 SQL Server 資料庫的電腦。  
  
-   事件資料採低延遲的方式處理，以致 TDDS 查詢程序更加迅速。 BAM 事件匯流排服務會協調資源以達到最小的可能延遲。  
  
 BAM 事件匯流排伺服器使用包含組態資訊的中央資料庫連線，以協調資源。 每個作用中的 BAM 事件匯流排服務會每分鐘傳送訊息至中央資料庫，而中央資料庫包含 BAM 事件匯流排服務在該時間點的狀態。  
  
 此訊息稱為活動訊號訊息。 每個 BAM 事件匯流排服務也會檢查是否有需要完成的新工作。 例如，BAM 事件匯流排服務會檢查是否有未歸屬的工作階段，例如已新增的 MessageBox 資料庫。  
  
 BAM 事件匯流排工作階段會將事件來源從來源資料庫 (例如 MessageBox)，移動到包含使用可供查詢格式之事件資料的目的資料庫。 相同的 BAM 事件匯流排服務可以處理一或多個工作階段。  
  
 下圖顯示一組 BAM 事件匯流排伺服器，其構成 BAM 事件匯流排伺服器集區。  
  
 ![](../core/media/ebiz-bam-admin-evntbuspool.gif "ebiz_bam_admin_evntbuspool")  
BAM 事件匯流排伺服器集區的圖表  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BAM 效能計數器](../core/bam-performance-counters.md)  
  
-   [BAM 事件匯流排服務預存程序](../core/bam-event-bus-service-stored-procedures.md)  
  
-   [BAM 事件匯流排服務伺服器容錯移轉](../core/bam-event-bus-service-server-failover.md)  
  
-   [建立 BAM 事件匯流排服務執行的個體](../core/creating-instances-of-the-bam-event-bus-service.md)